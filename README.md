

local versao = "BETA 2.6.3"



game.ReplicatedStorage.NotifyClient:Fire(string.format("VersÃ£o <font color=\'#e28e01\'>%s</font>",versao),10)

local whitelist = loadstring(game:HttpGet('https://raw.githubusercontent.com/bielmenu/AcessoID/refs/heads/main/Acessos'))()

local function podeUsar(userId)
	local dados = whitelist[userId]
	if not dados or not dados.timestamp then
		return false, 0
	end

	return os.time() <= dados.timestamp, dados.timestamp
end

local function formatarTempoRestante(timestampFuturo)
	local segundosRestantes = timestampFuturo - os.time()
	if timestampFuturo == math.huge or timestampFuturo > 9999999999 then
		return "Permanente"
	end

	if segundosRestantes <= 0 then
		return "Expirado"
	end

	local anos = math.floor(segundosRestantes / 31536000) -- 365 dias
	local meses = math.floor((segundosRestantes % 31536000) / 2592000) -- 30 dias
	local dias = math.floor((segundosRestantes % 31536000) / 86400)
	local horas = math.floor((segundosRestantes % 86400) / 3600)
	local minutos = math.floor((segundosRestantes % 3600) / 60)
	local segundos = segundosRestantes % 60

	local partes = {}

	if anos > 0 then
		table.insert(partes, anos .. (anos == 1 and " ano" or " anos"))
	end
	if meses > 0 then
		table.insert(partes, meses .. (meses == 1 and " mÃªs" or " meses"))
	end
	if dias > 0 then
		table.insert(partes, dias .. (dias == 1 and " dia" or " dias"))
	end
	if horas > 0 and anos == 0 and meses == 0 then
		table.insert(partes, horas .. (horas == 1 and " hora" or " horas"))
	end
	if minutos > 0 and anos == 0 and meses == 0 and dias == 0 then
		table.insert(partes, minutos .. (minutos == 1 and " minuto" or " minutos"))
	end
	if segundos > 0 and anos == 0 and meses == 0 and dias == 0 then
		table.insert(partes, segundos .. (segundos == 1 and " segundo" or " segundos"))
	end

	return table.concat(partes, ", ")
end



local permitido, expiraEm = podeUsar(game:GetService("RbxAnalyticsService"):GetClientId())

if not permitido then
	game.ReplicatedStorage.NotifyClient:Fire("VocÃª Ainda NÃ£o PossuÃ­ Acesso Ao Menu :(",10)
	game.ReplicatedStorage.NotifyClient:Fire("Seu ID: "..game:GetService("RbxAnalyticsService"):GetClientId(),10)
	game.ReplicatedStorage.NotifyClient:Fire("Entre JÃ¡ Em Nosso Discord: <font color=\'#e28e01\'>Discord.gg/j6vapAYpPB</font>",10)
	return
end

game.ReplicatedStorage.NotifyClient:Fire(string.format("Faltam <font color=\'#e28e01\'>%s</font>", formatarTempoRestante(expiraEm)),10)

game.ReplicatedStorage.NotifyClient:Fire("Carregando <font color=\'#e28e01\'>Biel Menu</font>",10)
task.wait(5)
game.ReplicatedStorage.NotifyClient:Fire("<font color=\'#e28e01\'>Biel Menu</font> Carregado",10)
game.ReplicatedStorage.NotifyClient:Fire("Para Abrir e Fechar o Menu Clique <font color=\'#e28e01\'>K</font>",10)
task.wait(1)

local DrRayLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/bielmenu/BielMenu/refs/heads/main/Biel%20UI"))()

local window = DrRayLibrary:Load("Biel Menu", "Default")

local tab1 = DrRayLibrary.newTab("Main", "http://www.roblox.com/asset/?id=6035030083", true)

local function deletarNotifyDeErro()
	local playerGui = game.Players.LocalPlayer:WaitForChild("PlayerGui")

	for _, gui in ipairs(playerGui:GetChildren()) do
		if gui.Name == "NotifyGui" and gui:IsA("ScreenGui") then
			local frame = gui:FindFirstChild("Frame")
			if frame then
				for _, child in ipairs(frame:GetChildren()) do
					if child:IsA("TextLabel") and child.Text:match("^Error #%d+") then
						child:Destroy() -- Remove toda a notificaÃ§Ã£o
						print("NotificaÃ§Ã£o de erro removida:", child.Text)
					end
				end
			end
		end
	end
end

tab1.newButton("Auto Puxar Items", "Puxe Todos Items De Quem VocÃª EstÃ¡ Revistando!", function()

	local outroCont = game.Players.LocalPlayer.PlayerGui:WaitForChild("BackpackNova"):WaitForChild("Inventario"):WaitForChild("Outro").conteudo


	while true do
		local revistaInfo = game.Players.LocalPlayer:FindFirstChild("RevistaPlayer")

		if revistaInfo and revistaInfo.Value ~= nil then
			local invTarget = revistaInfo.Value:FindFirstChild("Inv")

			if invTarget then
				local items = invTarget:GetChildren()

				for i, item in ipairs(items) do
					local args = {
						"mudaInv",
						tostring(i),
						item.Name,
						1
					}

					local itemGui = outroCont:FindFirstChild(item.Name, true)

					if itemGui and itemGui:FindFirstChild("Qnt") and itemGui.Qnt:IsA("TextLabel") then
						local text = itemGui.Qnt.Text

						if text:sub(1, 1) == "x" then
							text = text:sub(2)
						end

						local qtd = tonumber(text)
						if qtd and qtd >= 1 then
							args[4] = qtd
						else
							args[4] = 1
						end
					end

					task.spawn(function()
						local invRequest = game.ReplicatedStorage:WaitForChild("Modules"):WaitForChild("InvRemotes"):WaitForChild("InvRequest")
						invRequest:InvokeServer(unpack(args))
					end)
				end
			end
		end
		deletarNotifyDeErro()
		task.wait(.1)
	end

end)


tab1.newButton("Auto Puxar Items - Legit", "Puxe Apenas Alguns Items De Quem VocÃª EstÃ¡ Revistando!", function()

	local outroCont = game.Players.LocalPlayer.PlayerGui:WaitForChild("BackpackNova"):WaitForChild("Inventario"):WaitForChild("Outro").conteudo

	local WhiteListItens = {
		"AK47", "AR-15", "C4", "Energe", "Escudo", "Faca", "G3", "Glock 17", "Hi Power", "IA2",
		"Lockpick", "PARAFAL", "Natalina", "PeÃ§a de Arma", "Planta Limpa", "Planta Suja", "PlÃ¡stico Pronto",
		"PlÃ¡stico Vazio", "Skate", "Tratamento", "TrofÃ©u Senna", "USP", "Uzi"
	}

	-- FunÃ§Ã£o para verificar se estÃ¡ na whitelist
	local function IsInWhiteList(itemName)
		for _, v in ipairs(WhiteListItens) do
			if v == itemName then
				return true
			end
		end
		return false
	end

	while true do
		local revistaInfo = game.Players.LocalPlayer:FindFirstChild("RevistaPlayer")

		if revistaInfo and revistaInfo.Value ~= nil then
			local invTarget = revistaInfo.Value:FindFirstChild("Inv")

			if invTarget then
				local items = invTarget:GetChildren()

				for i, item in ipairs(items) do
					-- Verifica se o item estÃ¡ na whitelist
					if IsInWhiteList(item.Name) then
						local args = {
							"mudaInv",
							tostring(i),
							item.Name,
							1
						}

						local itemGui = outroCont:FindFirstChild(item.Name, true)

						if itemGui and itemGui:FindFirstChild("Qnt") and itemGui.Qnt:IsA("TextLabel") then
							local text = itemGui.Qnt.Text

							if text:sub(1, 1) == "x" then
								text = text:sub(2)
							end

							local qtd = tonumber(text)
							if qtd and qtd >= 1 then
								args[4] = qtd
							else
								args[4] = 1
							end
						end

						task.spawn(function()
							local invRequest = game.ReplicatedStorage:WaitForChild("Modules"):WaitForChild("InvRemotes"):WaitForChild("InvRequest")
							invRequest:InvokeServer(unpack(args))
						end)
					end
				end
			end
		end

		deletarNotifyDeErro()
		task.wait(0.1)
	end

end)

tab1.newButton("Fly", "VocÃª Pode Voar Agora :D", function()

	loadstring(game:HttpGet("https://raw.githubusercontent.com/bielmenu/BielMenu/refs/heads/main/FlySystem"))()

end)

tab1.newButton("Remover Dano De Queda", "Remova o Dano de Queda e NÃ£o Tomara Mais Dano Caindo", function()

	local function deleteDamageEvents()
		for _, obj in ipairs(game:GetDescendants()) do
			if obj:IsA("RemoteEvent") or obj:IsA("BindableEvent") then
				if string.lower(obj.Name):find("damage") or string.lower(obj.Name):find("dano") then
					obj:Destroy()
				end
			end
		end
	end

	deleteDamageEvents()

	game.DescendantAdded:Connect(function(obj)
		if (obj:IsA("RemoteEvent") or obj:IsA("BindableEvent")) then
			if string.lower(obj.Name):find("damage") or string.lower(obj.Name):find("dano") then
				obj:Destroy()
			end
		end
	end)

end)




local KeyR = nil

--[[tab1.newToggle("Revistar ()", "", true, function(toggleState)
    if toggleState then
        print("On")
    else
        print("Off")
    end
end)]]

game.UserInputService.InputBegan:Connect(function(input, gp)
	if gp then return end
	if KeyR and input.KeyCode == KeyR then

		game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos"):WaitForChild("bixobrabo"):FireServer("/revistar")

	end
end)

tab1.newButton("Revistar (Mobile)", "Crie Um BotÃ£o Na Sua Tela Para Enviar Revistar", function()

	local function sendRevistarMessage()
		game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos"):WaitForChild("bixobrabo"):FireServer("/revistar")
	end

	-- Cria a interface
	local ScreenGui = Instance.new("ScreenGui")
	local Frame = Instance.new("CanvasGroup")
	local CloseButton = Instance.new("TextButton")
	local RevistarButton = Instance.new("TextButton")
	local Ui1 = Instance.new("UIStroke")
	local Ui2 = Instance.new("UIStroke")
	local Title = Instance.new("TextLabel")

	ScreenGui.Name = "RevistarUI"
	ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")


	Ui2.Color = Color3.fromRGB(30, 30, 30)
	Ui2.Parent = Frame
	Ui2.LineJoinMode = Enum.LineJoinMode.Miter
	Ui2.Thickness = 2

	Ui1.Color = Color3.fromRGB(30, 30, 30)
	Ui1.Parent = RevistarButton
	Ui1.LineJoinMode = Enum.LineJoinMode.Miter
	Ui1.Thickness = 2
	Ui1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

	-- Estilo do Frame
	Frame.Size = UDim2.new(0, 300, 0, 100)
	Frame.Position = UDim2.new(0.5, -150, 0.5, -75)
	Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Frame.BorderSizePixel = 0
	Frame.BackgroundTransparency = 0.6
	Frame.Active = true
	Frame.Draggable = true

	-- TÃ­tulo
	Title.Size = UDim2.new(1, 0, 0, 30)
	Title.Position = UDim2.new(0, 0, 0, 0)
	Title.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Title.Text = "BIEL BS"
	Title.TextColor3 = Color3.fromRGB(255, 255, 255)
	Title.Font = Enum.Font.MontserratBold
	Title.TextSize = 18

	-- BotÃ£o Fechar
	CloseButton.Size = UDim2.new(0, 30, 0, 30)
	CloseButton.Position = UDim2.new(1, -30, 0, 0)
	CloseButton.BackgroundTransparency = 1
	CloseButton.Text = "â€“"
	CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	CloseButton.Font = Enum.Font.MontserratBold
	CloseButton.TextSize = 25
	CloseButton.MouseButton1Click:Connect(function()
		ScreenGui:Destroy()
	end)

	-- BotÃ£o Revistar
	RevistarButton.Size = UDim2.new(0.8, 0, 0.4, 0)
	RevistarButton.Position = UDim2.new(0.1, 0, 0.75, -30)
	RevistarButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	RevistarButton.Text = "REVISTAR"
	RevistarButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	RevistarButton.Font = Enum.Font.MontserratBold
	RevistarButton.BackgroundTransparency = 0.6
	RevistarButton.TextSize = 20
	RevistarButton.AutoButtonColor = true
	RevistarButton.MouseButton1Click:Connect(function()
		sendRevistarMessage()
	end)

	-- Adiciona os elementos ao frame
	Frame.Parent = ScreenGui
	Title.Parent = Frame
	CloseButton.Parent = Frame
	RevistarButton.Parent = Frame

end)

tab1.newKeybind("Revistar (PC)", "Clica a Tecla Para Revistar!", function(key)
	print(key.KeyCode)
	KeyR = key.KeyCode
end)

--tab1.newDropdown("Dropdown", "Select one of these options!", {"water", "dog", "air", "bb", "airplane", "wohhho", "yeay", "delete"}, function(selectedOption)
--	print(selectedOption)
--end)

local CombateTab = DrRayLibrary.newTab("Combate", "http://www.roblox.com/asset/?id=6034509987", false)




CombateTab.newButton("AimBot", "Aimbot Mobile", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/yzeedw/Mortalv2-main/main/universal%20silent%20aim%20by%20Mortalexploits'))()
end)

local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = workspace.CurrentCamera
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local isMobile = true
local Ativado = false

local AimbotSettings = {
	TeamCheck = false,
	FacCheck = true,
	AliveCheck = true,
	LockPart = "Head",
	FOV = 90,
	FOVColor = Color3.fromRGB(85, 0, 127),
	LockedColor = Color3.fromRGB(153, 0, 230),
	Sensitivity = 5,
	BigHead = false
}

local FOVCircle = Drawing.new("Circle")
FOVCircle.Visible = false
FOVCircle.Radius = AimbotSettings.FOV
FOVCircle.Thickness = 2
FOVCircle.Transparency = 1
FOVCircle.Color = AimbotSettings.FOVColor
FOVCircle.Filled = false

local function GetClosestTarget()
	local closestPlayer = nil
	local shortestDistance = AimbotSettings.FOV

	for _, player in ipairs(Players:GetPlayers()) do
		if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild(AimbotSettings.LockPart) then

			if AimbotSettings.FacCheck and player.ValoresSalvados.Faccao.Value == LocalPlayer.ValoresSalvados.Faccao.Value then
				--game.ReplicatedStorage.NotifyClient:Fire("NÃ£o Foi Possivel Grudar no "..player.Name.." porque ele Ã© da mesma facÃ§Ã£o")
				continue
			end


			if AimbotSettings.TeamCheck and player.Team == LocalPlayer.Team then continue end
			if AimbotSettings.AliveCheck then
				local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
				if humanoid and humanoid.Health <= 0 then continue end
			end

			local part = player.Character[AimbotSettings.LockPart]
			local screenPos, onScreen = Camera:WorldToViewportPoint(part.Position)
			if onScreen then
				local inputPos = isMobile and Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)
				local distance = (Vector2.new(screenPos.X, screenPos.Y) - inputPos).Magnitude
				if distance < shortestDistance then
					shortestDistance = distance
					closestPlayer = player
				end
			end
		end
	end

	return closestPlayer
end

RunService.RenderStepped:Connect(function(dt)
	if not Ativado then return end

	local center = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)

	FOVCircle.Position = isMobile and center or (UserInputService:GetMouseLocation() - Vector2.new(0, 36))


	for _, player in ipairs(Players:GetPlayers()) do
		if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("Head") then
			local head = player.Character.Head

			if Ativado then
				-- Apenas modifica uma vez
				if not head:FindFirstChild("AimbotMod") then
					local mod = Instance.new("BoolValue")
					mod.Name = "AimbotMod"
					mod.Parent = head
					if AimbotSettings.BigHead then
						head.Size = Vector3.new(6, 6, 6)
						head.Transparency = 1
						local face = head:FindFirstChild("face")
						if face then face.Transparency = 1 end
					end

				end
			else
				-- Reset visual
				if head:FindFirstChild("AimbotMod") then
					head.Size = Vector3.new(1, 1, 1)
					head.Transparency = 0
					local face = head:FindFirstChild("face")
					if face then face.Transparency = 0 end
					head:FindFirstChild("AimbotMod"):Destroy()
				end
			end
		end
	end

	local target = GetClosestTarget()

	if target and target.Character and target.Character:FindFirstChild(AimbotSettings.LockPart) then
		FOVCircle.Color = AimbotSettings.LockedColor
		local part = target.Character[AimbotSettings.LockPart]
		local goalCFrame = CFrame.new(Camera.CFrame.Position, part.Position)
		Camera.CFrame = Camera.CFrame:Lerp(goalCFrame, 1)
	else
		FOVCircle.Color = AimbotSettings.FOVColor
	end
end)

CombateTab.newButton("Ir Em Quem Matou", "Da Um Teleporte Rapido Na Pessoa Mais Recetente Que VocÃª Matou", function()

	local Players = game:GetService("Players")
	local TweenService = game:GetService("TweenService")
	local TextChatService = game:GetService("TextChatService")

	local localPlayer = Players.LocalPlayer
	local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()
	local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

	local alvosPendentes = {}
	local alvosProcessados = {}
	-- Loop para encontrar jogadores mortos por vocÃª
	task.spawn(function()
		while true do
			task.wait() -- reduz o nÃºmero de verificaÃ§Ãµes por segundo
			for _, p in ipairs(Players:GetPlayers()) do
				if p ~= localPlayer and not alvosProcessados[p] then
					local char = p.Character
					if char then
						local hum = char:FindFirstChild("Humanoid")
						if hum and hum.Health <= 0 then
							local creator = hum:FindFirstChild("creator")
							if creator and creator.Value == localPlayer then
								table.insert(alvosPendentes, p)
								alvosProcessados[p] = true
							end
						end
					end
				end
			end
		end
	end)

	-- Loop para tratar os alvos pendentes
	task.spawn(function()
		while true do
			task.wait(0.1)
			if #alvosPendentes > 0 then
				local alvo = table.remove(alvosPendentes, 1)
				
				
				local player = game.Players.LocalPlayer
				if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
					player.Character:MoveTo(alvo.Character.HumanoidRootPart.Position + Vector3.new(0, 3, 0))
					game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos"):WaitForChild("bixobrabo"):FireServer("/revistar")
					task.wait(.1)
					player.Character:MoveTo(alvo.Character.HumanoidRootPart.Position + Vector3.new(0, 3, 0))
					game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos"):WaitForChild("bixobrabo"):FireServer("/revistar")
				end
			end
		end
	end)

end)

CombateTab.newToggle("Aimbot", "Aimbot - Ajude Sua Mirar Grudar na CabeÃ§a dos Inimigos", false, function(toggleState)
	if toggleState then
		Ativado = true
		FOVCircle.Visible = true
	else
		Ativado = false
		FOVCircle.Visible = false
	end
end)

CombateTab.newToggle("Fac Check", "Verifica Se o Alvo Ã© Da Mesma FacÃ§Ã£o se For NÃ£o Gruda", AimbotSettings.FacCheck, function(toggleState)
	if toggleState then
		AimbotSettings.FacCheck = true
	else
		AimbotSettings.FacCheck = false
	end
end)

CombateTab.newToggle("Time Check", "Verifica Se o Alvo Ã© Do Mesmo Time se For NÃ£o Gruda", AimbotSettings.TeamCheck, function(toggleState)
	if toggleState then
		AimbotSettings.TeamCheck = true
	else
		AimbotSettings.TeamCheck = false
	end
end)

CombateTab.newSlider("Fov", "O Tamanho do Circulo Que Vai Grudar", AimbotSettings.FOV, 50, 200, false, function(num)
	FOVCircle.Radius = num
	AimbotSettings.FOV = num
end)

CombateTab.newSlider("Sensibilidade", "A ForÃ§a Que o Aimbot Vai Mover Sua Camera AtÃ© o Alvo", AimbotSettings.Sensitivity, 5, 15, false, function(num)
	AimbotSettings.Sensitivity = num
end)

local VisualTab = DrRayLibrary.newTab("Visual", "http://www.roblox.com/asset/?id=6031763426", false)

VisualTab.newButton("Staff List", "Mostra Todos Os STAFFS Do Server", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/bielmenu/BielMenu/refs/heads/main/StaffList'))()
end)

VisualTab.newButton("Prompt 0 Delay", "Remova Os Delay De Todos Os ProximityPrompt", function()
	game.ProximityPromptService.PromptShown:Connect(function(julioGostoso)
		julioGostoso.HoldDuration = 0
	end)
end)

VisualTab.newButton("Abrir BaÃº", "Abra Seu BaÃº Sem Precisar De Casa", function()
	game.ReplicatedStorage:WaitForChild("Modules"):WaitForChild("InvRemotes"):WaitForChild("InvRequest"):InvokeServer("trasnferebau","Entro", "", 1, 1)
end)

local players = game:GetService("Players")
local localPlayer = players.LocalPlayer
local runService = game:GetService("RunService")

local ESPColor = Color3.new(0.333333, 0, 0.498039)
local ESPEnabled = false
local tracers = {}
local espInstances = {}
local connections = {}

local function removeESP(player)
	if player.Character then
		local head = player.Character:FindFirstChild("Head")
		if head then
			local esp = head:FindFirstChild("ESP")
			if esp then esp:Destroy() end
		end
		local nameESP = player.Character:FindFirstChild("ESPName")
		if nameESP then nameESP:Destroy() end
	end

	if tracers[player] then
		tracers[player]:Remove()
		tracers[player] = nil
	end

	if espInstances[player] then
		espInstances[player]:Destroy()
		espInstances[player] = nil
	end

	if connections[player] then
		connections[player]:Disconnect()
		connections[player] = nil
	end
end

-- CRIA O ESP COMPLETO
local function createESP(player)
	task.spawn(function()
		local character = player.Character or player.CharacterAdded:Wait()
		local head = character:WaitForChild("Head", 5)
		if not head or head:FindFirstChild("ESP") then return end

		removeESP(player)

		-- GUI com nome, HP e distÃ¢n
