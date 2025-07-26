local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local whitelist = {
    [shadowWolf23552] = true

}

local player = game.Players.LocalPlayer
if not whitelist[player.UserId] then
    player:Kick("tu nao ta na whitelist manin nÃ£o tente excutar")
    return
end

local Window = Rayfield:CreateWindow({
   Name = "                            Arthur Menu V2 ðŸ’Ž",
   Icon = 0,
   LoadingTitle = "Arthur V99 ðŸ”¥",
   LoadingSubtitle = "By Equip Of Arthur Store ðŸ›’",
   Theme = "DarkBlue",
   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false,
   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil,
      FileName = "Big Hub"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink",
      RememberJoins = true
   }
})


local Tab = Window:CreateTab("Infos", 9405926389)
Rayfield:Notify({
   Title = "Arthur Injected ðŸ’¸",
   Content = "Obrigado por Adquirir nosso menu!",
   Duration = 36.0,
   Image = 118582375849783,
})
local Paragraph = Tab:CreateParagraph({Title = "Arthur Menu â„¹ï¸", Content = "+Novas OpÃ§Ãµes +Novas Farms +Menu Reeconstruido "})
local Button = Tab:CreateButton({ Name = "Ver AtualizaÃ§Ãµes ðŸ“œ", Callback = function() 
    print("Abrindo atualizaÃ§Ãµes...")
end })

local Tab = Window:CreateTab("AUTO-FARMS", 484395794)
local Button = Tab:CreateButton({ Name = "Injetar Farms NESSESARIO âš™ï¸", Callback = function() 
    print("INJETADOOO")
	for _, prompt in ipairs(workspace:GetDescendants()) do
    if prompt:IsA("ProximityPrompt") then
        prompt.HoldDuration = 0
    end
end

workspace.DescendantAdded:Connect(function(descendant)
    if descendant:IsA("ProximityPrompt") then
        descendant.HoldDuration = 0
    end
end)

end })
local Button = Tab:CreateButton({ Name = "Auto-Farm Gari ðŸ—‘ï¸", Callback = function() 
    print("Auto-Farm Gari ativado!")
	local teleportLocations = {
    CFrame.new(-346.349335, 11.2034531, -15.1218395, -0.31654954, 0, 0.948575974, 0, 1, 0, -0.948575974, 0, -0.31654954),
    CFrame.new(-378.03656, 3.38713574, -27.1200333, -1, 0, 0, 0, 1, 0, 0, 0, -1),
    CFrame.new(-378.266357, 3.46769452, -30.3575802, 0, 0, 1, 0, 1, -0, -1, 0, 0),
    CFrame.new(-498.865448, 3.35259485, -68.842926, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    CFrame.new(-454.89386, 3.24043727, -37.3385849, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    CFrame.new(-455.081329, 3.26448464, -40.1521721, -0.879374862, 0, -0.476129979, 0, 1, 0, 0.476129979, 0, -0.879374862),
    CFrame.new(-454.84436, 3.35945153, -7.08071899, 0.312709093, -0, -0.94984895, 0, 1, -0, 0.94984895, 0, 0.312709093),
    CFrame.new(-454.901733, 3.35945153, -3.81340384, -0.867699981, 0, -0.497088224, 0, 1, 0, 0.497088224, 0, -0.867699981),
    CFrame.new(-485.288635, 3.25063586, 36.3800468, -1, 0, 0, 0, 1, 0, 0, 0, -1),
    CFrame.new(-493.315643, 3.25063586, 41.082119, 0, 0, -1, 0, 1, 0, 1, 0, 0),
    CFrame.new(-485.425842, 3.30863595, 40.0470543, 0, 0, -1, 0, 1, 0, 1, 0, 0),
    CFrame.new(-489.648621, 3.30863595, 41.219326, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    CFrame.new(-498.832886, 3.20863581, 10.057312, -1, 0, 0, 0, 1, 0, 0, 0, -1),
    CFrame.new(-495.288879, 3.20863581, 10.057312, 0.980359316, 0, 0.197219774, 0, 1, 0, -0.197219774, 0, 0.980359316),
    CFrame.new(-546.534424, 3.28816128, 41.2314491, 0.363939464, -0, -0.931422591, 0, 1, -0, 0.931422591, 0, 0.363939464),
    CFrame.new(-550.090454, 3.28816128, 40.9795532, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    CFrame.new(-529.422485, 7.59310627, 41.1137466, -0.941578388, 0.00161392801, -0.336789817, 0.03796231, 0.994124353, -0.101368994, 0.334647328, -0.108232185, -0.936107278),
    CFrame.new(-547.876831, 3.34044552, 4.75392103, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    CFrame.new(-530.51886, 5.72843599, 40.7209358, -0.214117646, 0.0016499348, 0.976806521, -0.105338335, 0.994127929, -0.0247695222, -0.971111536, -0.108198754, -0.212686539),
    CFrame.new(-555.154724, 3.26677322, 9.59934711, 0.962701917, -0, -0.270564169, 0, 1, -0, 0.270564169, 0, 0.962701917),
    CFrame.new(-552.148682, 3.26677322, 9.04824924, -0.607952714, 0, 0.793973267, 0, 1, 0, -0.793973267, 0, -0.607952714),
    CFrame.new(-556.973206, 3.34377933, 45.7063637, -0.799710631, 0, 0.600385725, 0, 1, 0, -0.600385725, 0, -0.799710631),
    CFrame.new(-616.710205, 3.24663591, 9.45095444, 0.904720604, 0, 0.426005453, 0, 1, 0, -0.426005453, 0, 0.904720604),
    CFrame.new(-617.171021, 3.24663591, 13.3314476, -1, 0, 0, 0, 1, 0, 0, 0, -1),
    CFrame.new(-585.328186, 3.89165664, 4.08425522, 1, 0, 0, 0, 1, 0, 0, 0, 1)
}

local player = game:GetService("Players").LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local function teleportToLocation(index)
    if character and character:FindFirstChild("HumanoidRootPart") then
        character.HumanoidRootPart.CFrame = teleportLocations[index]
    end
end

local currentIndex = 1

-- Teleport automatically every 3 seconds
while true do
    teleportToLocation(currentIndex)
    currentIndex = (currentIndex % #teleportLocations) + 1
    wait(0.3)  -- Espera 3 segundos antes de teleportar para a prÃ³xima localizaÃ§Ã£o
end

for _, prompt in ipairs(workspace:GetDescendants()) do
    if prompt:IsA("ProximityPrompt") then
        prompt.HoldDuration = 0
    end
end

workspace.DescendantAdded:Connect(function(descendant)
    if descendant:IsA("ProximityPrompt") then
        descendant.HoldDuration = 0
    end
end)

end })
local Button = Tab:CreateButton({ Name = "Auto Farm GÃ¡s", Callback = function() 
    print("Auto-Farm GÃ¡s ativado!")
loadstring(game:HttpGet('https://raw.githubusercontent.com/Rafaasxs/Nexus-Menu-/refs/heads/main/tesao'))()
end })
local Button = Tab:CreateButton({ Name = "Auto-Farm Minerador â›ï¸", Callback = function() 
    print("Auto-Farm Minerador ativado!")
end })

local Tab = Window:CreateTab("PVP", 15990136399)
local Button = Tab:CreateButton({ Name = "Aimbot ðŸŽ¯", Callback = function() 
    print("Aimbot ativado!")
	--// Cache

local select = select
local pcall, getgenv, next, Vector2, mathclamp, type, mousemoverel = select(1, pcall, getgenv, next, Vector2.new, math.clamp, type, mousemoverel or (Input and Input.MouseMove))

--// Preventing Multiple Processes

pcall(function()
	getgenv().Aimbot.Functions:Exit()
end)

--// Environment

getgenv().Aimbot = {}
local Environment = getgenv().Aimbot

--// Services

local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")
local Camera = workspace.CurrentCamera
local LocalPlayer = Players.LocalPlayer

--// Variables

local RequiredDistance, Typing, Running, Animation, ServiceConnections = 2000, false, false, nil, {}

--// Script Settings

Environment.Settings = {
	Enabled = true,
	TeamCheck = false,
	AliveCheck = true,
	WallCheck = false, -- Laggy
	Sensitivity = 0, -- Animation length (in seconds) before fully locking onto target
	ThirdPerson = false, -- Uses mousemoverel instead of CFrame to support locking in third person (could be choppy)
	ThirdPersonSensitivity = 3, -- Boundary: 0.1 - 5
	TriggerKey = "MouseButton2",
	Toggle = false,
	LockPart = "Head" -- Body part to lock on
}

Environment.FOVSettings = {
	Enabled = true,
	Visible = true,
	Amount = 90,
	Color = Color3.fromRGB(0, 0, 0),
	LockedColor = Color3.fromRGB(255, 70, 70),
	Transparency = 0.5,
	Sides = 60,
	Thickness = 1,
	Filled = false
}

Environment.FOVCircle = Drawing.new("Circle")

--// Functions

local function CancelLock()
	Environment.Locked = nil
	if Animation then Animation:Cancel() end
	Environment.FOVCircle.Color = Environment.FOVSettings.Color
end

local function GetClosestPlayer()
	if not Environment.Locked then
		RequiredDistance = (Environment.FOVSettings.Enabled and Environment.FOVSettings.Amount or 2000)

		for _, v in next, Players:GetPlayers() do
			if v ~= LocalPlayer then
				if v.Character and v.Character:FindFirstChild(Environment.Settings.LockPart) and v.Character:FindFirstChildOfClass("Humanoid") then
					if Environment.Settings.TeamCheck and v.Team == LocalPlayer.Team then continue end
					if Environment.Settings.AliveCheck and v.Character:FindFirstChildOfClass("Humanoid").Health <= 0 then continue end
					if Environment.Settings.WallCheck and #(Camera:GetPartsObscuringTarget({v.Character[Environment.Settings.LockPart].Position}, v.Character:GetDescendants())) > 0 then continue end

					local Vector, OnScreen = Camera:WorldToViewportPoint(v.Character[Environment.Settings.LockPart].Position)
					local Distance = (Vector2(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y) - Vector2(Vector.X, Vector.Y)).Magnitude

					if Distance < RequiredDistance and OnScreen then
						RequiredDistance = Distance
						Environment.Locked = v
					end
				end
			end
		end
	elseif (Vector2(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y) - Vector2(Camera:WorldToViewportPoint(Environment.Locked.Character[Environment.Settings.LockPart].Position).X, Camera:WorldToViewportPoint(Environment.Locked.Character[Environment.Settings.LockPart].Position).Y)).Magnitude > RequiredDistance then
		CancelLock()
	end
end

--// Typing Check

ServiceConnections.TypingStartedConnection = UserInputService.TextBoxFocused:Connect(function()
	Typing = true
end)

ServiceConnections.TypingEndedConnection = UserInputService.TextBoxFocusReleased:Connect(function()
	Typing = false
end)

--// Main

local function Load()
	ServiceConnections.RenderSteppedConnection = RunService.RenderStepped:Connect(function()
		if Environment.FOVSettings.Enabled and Environment.Settings.Enabled then
			Environment.FOVCircle.Radius = Environment.FOVSettings.Amount
			Environment.FOVCircle.Thickness = Environment.FOVSettings.Thickness
			Environment.FOVCircle.Filled = Environment.FOVSettings.Filled
			Environment.FOVCircle.NumSides = Environment.FOVSettings.Sides
			Environment.FOVCircle.Color = Environment.FOVSettings.Color
			Environment.FOVCircle.Transparency = Environment.FOVSettings.Transparency
			Environment.FOVCircle.Visible = Environment.FOVSettings.Visible
			Environment.FOVCircle.Position = Vector2(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y)
		else
			Environment.FOVCircle.Visible = false
		end

		if Running and Environment.Settings.Enabled then
			GetClosestPlayer()

			if Environment.Locked then
				if Environment.Settings.ThirdPerson then
					Environment.Settings.ThirdPersonSensitivity = mathclamp(Environment.Settings.ThirdPersonSensitivity, 0.1, 5)

					local Vector = Camera:WorldToViewportPoint(Environment.Locked.Character[Environment.Settings.LockPart].Position)
					mousemoverel((Vector.X - UserInputService:GetMouseLocation().X) * Environment.Settings.ThirdPersonSensitivity, (Vector.Y - UserInputService:GetMouseLocation().Y) * Environment.Settings.ThirdPersonSensitivity)
				else
					if Environment.Settings.Sensitivity > 0 then
						Animation = TweenService:Create(Camera, TweenInfo.new(Environment.Settings.Sensitivity, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {CFrame = CFrame.new(Camera.CFrame.Position, Environment.Locked.Character[Environment.Settings.LockPart].Position)})
						Animation:Play()
					else
						Camera.CFrame = CFrame.new(Camera.CFrame.Position, Environment.Locked.Character[Environment.Settings.LockPart].Position)
					end
				end

			Environment.FOVCircle.Color = Environment.FOVSettings.LockedColor

			end
		end
	end)

	ServiceConnections.InputBeganConnection = UserInputService.InputBegan:Connect(function(Input)
		if not Typing then
			pcall(function()
				if Input.KeyCode == Enum.KeyCode[Environment.Settings.TriggerKey] then
					if Environment.Settings.Toggle then
						Running = not Running

						if not Running then
							CancelLock()
						end
					else
						Running = true
					end
				end
			end)

			pcall(function()
				if Input.UserInputType == Enum.UserInputType[Environment.Settings.TriggerKey] then
					if Environment.Settings.Toggle then
						Running = not Running

						if not Running then
							CancelLock()
						end
					else
						Running = true
					end
				end
			end)
		end
	end)

	ServiceConnections.InputEndedConnection = UserInputService.InputEnded:Connect(function(Input)
		if not Typing then
			if not Environment.Settings.Toggle then
				pcall(function()
					if Input.KeyCode == Enum.KeyCode[Environment.Settings.TriggerKey] then
						Running = false; CancelLock()
					end
				end)

				pcall(function()
					if Input.UserInputType == Enum.UserInputType[Environment.Settings.TriggerKey] then
						Running = false; CancelLock()
					end
				end)
			end
		end
	end)
end

--// Functions

Environment.Functions = {}

function Environment.Functions:Exit()
	for _, v in next, ServiceConnections do
		v:Disconnect()
	end

	if Environment.FOVCircle.Remove then Environment.FOVCircle:Remove() end

	getgenv().Aimbot.Functions = nil
	getgenv().Aimbot = nil
	
	Load = nil; GetClosestPlayer = nil; CancelLock = nil
end

function Environment.Functions:Restart()
	for _, v in next, ServiceConnections do
		v:Disconnect()
	end

	Load()
end

function Environment.Functions:ResetSettings()
	Environment.Settings = {
		Enabled = true,
		TeamCheck = false,
		AliveCheck = true,
		WallCheck = false,
		Sensitivity = 0, -- Animation length (in seconds) before fully locking onto target
		ThirdPerson = false, -- Uses mousemoverel instead of CFrame to support locking in third person (could be choppy)
		ThirdPersonSensitivity = 3, -- Boundary: 0.1 - 5
		TriggerKey = "MouseButton2",
		Toggle = false,
		LockPart = "black" -- Body part to lock on
	}

	Environment.FOVSettings = {
		Enabled = true,
		Visible = true,
		Amount = 90,
		Color = Color3.fromRGB(0, 0, 0), --Preto
		LockedColor = Color3.fromRGB(255, 70, 70),
		Transparency = 0.5,
		Sides = 60,
		Thickness = 1,
		Filled = false
	}
end

--// Load

Load()
end })
local Button = Tab:CreateButton({ Name = "ESP ðŸ‘€", Callback = function() 
    print("ESP ativado!")
	loadstring(game:HttpGet(('https://raw.githubusercontent.com/cool83birdcarfly02six/UNIVERSALESPLTX/main/README.md'),true))()
end })
local Button = Tab:CreateButton({ Name = "HitBox ðŸ“¦", Callback = function() 
    print("HitBox expandido!")
	-- Defina a parte que serÃ¡ a hitbox (pode ser qualquer parte do personagem ou um objeto especÃ­fico)
local hitbox = workspace:WaitForChild("Hitbox")  -- Supondo que vocÃª tenha uma parte chamada "Hitbox"

-- FunÃ§Ã£o para criar o efeito RGB
local function setRGBColor(part)
    local time = tick()  -- Captura o tempo atual para efeitos baseados em tempo
    local r = math.abs(math.sin(time))  -- Cria uma cor vermelha animada
    local g = math.abs(math.sin(time + math.pi/3))  -- Cria uma cor verde animada
    local b = math.abs(math.sin(time + math.pi/2))  -- Cria uma cor azul animada
    part.Color = Color3.fromRGB(r * 255, g * 255, b * 255)  -- Converte para valores RGB
end

-- FunÃ§Ã£o para expandir a hitbox
local function expandHitbox()
    local size = 7  -- Tamanho inicial da hitbox
    while true do
        -- Expande a hitbox
        hitbox.Size = hitbox.Size + Vector3.new(0.1, 0.1, 0.1)
        
        -- Atualiza a cor com efeito RGB
        setRGBColor(hitbox)
        
        wait(0.1)  -- Aguarda um pequeno intervalo para o prÃ³ximo aumento e troca de cor
    end
end

-- Inicia a expansÃ£o da hitbox
expandHitbox()

end })
local Button = Tab:CreateButton({ Name = "Wallbang ðŸ”«", Callback = function() 
    print("Wallbang ativado!")
end })
local Section = Tab:CreateSection("Modo InvisÃ­vel")

Tab:CreateButton({
    Name = "Ativar Invisibilidade",
    Callback = function()
        local player = game.Players.LocalPlayer
        local character = player.Character
        if character then
            for _, v in pairs(character:GetDescendants()) do
                if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
                    v.Transparency = 1
                    if v:FindFirstChild("Mesh") then
                        v.Mesh.TextureId = ""
                    end
                end
            end
        end
        Rayfield:Notify({
            Title = "Invisibilidade",
            Content = "Seu personagem agora estÃ¡ invisÃ­vel!",
            Duration = 3
        })
    end
})

Tab:CreateButton({
    Name = "Desativar Invisibilidade",
    Callback = function()
        local player = game.Players.LocalPlayer
        local character = player.Character
        if character then
            for _, v in pairs(character:GetDescendants()) do
                if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
                    v.Transparency = 0
                end
            end
        end
        Rayfield:Notify({
            Title = "Invisibilidade",
            Content = "Seu personagem agora estÃ¡ visÃ­vel novamente!",
            Duration = 3
        })
    end
})

local Tab = Window:CreateTab("PLAYERS", 13289762774)
local Button = Tab:CreateButton({ Name = "Fly âœˆï¸", Callback = function() 
    print("Fly ativado!")
	local main = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local up = Instance.new("TextButton")
local down = Instance.new("TextButton")
local onof = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
local plus = Instance.new("TextButton")
local speed = Instance.new("TextLabel")
local mine = Instance.new("TextButton")
local closebutton = Instance.new("TextButton")
local mini = Instance.new("TextButton")
local mini2 = Instance.new("TextButton")

main.Name = "main"
main.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
main.ResetOnSpawn = false

Frame.Parent = main
Frame.BackgroundColor3 = Color3.fromRGB(163, 255, 137)
Frame.BorderColor3 = Color3.fromRGB(103, 221, 213)
Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
Frame.Size = UDim2.new(0, 190, 0, 57)

up.Name = "up"
up.Parent = Frame
up.BackgroundColor3 = Color3.fromRGB(79, 255, 152)
up.Size = UDim2.new(0, 44, 0, 28)
up.Font = Enum.Font.SourceSans
up.Text = "UP"
up.TextColor3 = Color3.fromRGB(0, 0, 0)
up.TextSize = 14.000

down.Name = "down"
down.Parent = Frame
down.BackgroundColor3 = Color3.fromRGB(215, 255, 121)
down.Position = UDim2.new(0, 0, 0.491228074, 0)
down.Size = UDim2.new(0, 44, 0, 28)
down.Font = Enum.Font.SourceSans
down.Text = "DOWN"
down.TextColor3 = Color3.fromRGB(0, 0, 0)
down.TextSize = 14.000

onof.Name = "onof"
onof.Parent = Frame
onof.BackgroundColor3 = Color3.fromRGB(255, 249, 74)
onof.Position = UDim2.new(0.702823281, 0, 0.491228074, 0)
onof.Size = UDim2.new(0, 56, 0, 28)
onof.Font = Enum.Font.SourceSans
onof.Text = "fly"
onof.TextColor3 = Color3.fromRGB(0, 0, 0)
onof.TextSize = 14.000

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(242, 60, 255)
TextLabel.Position = UDim2.new(0.469327301, 0, 0, 0)
TextLabel.Size = UDim2.new(0, 100, 0, 28)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Arthur store"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true

plus.Name = "plus"
plus.Parent = Frame
plus.BackgroundColor3 = Color3.fromRGB(133, 145, 255)
plus.Position = UDim2.new(0.231578946, 0, 0, 0)
plus.Size = UDim2.new(0, 45, 0, 28)
plus.Font = Enum.Font.SourceSans
plus.Text = "+"
plus.TextColor3 = Color3.fromRGB(0, 0, 0)
plus.TextScaled = true
plus.TextSize = 14.000
plus.TextWrapped = true

speed.Name = "speed"
speed.Parent = Frame
speed.BackgroundColor3 = Color3.fromRGB(255, 85, 0)
speed.Position = UDim2.new(0.468421042, 0, 0.491228074, 0)
speed.Size = UDim2.new(0, 44, 0, 28)
speed.Font = Enum.Font.SourceSans
speed.Text = "1"
speed.TextColor3 = Color3.fromRGB(0, 0, 0)
speed.TextScaled = true
speed.TextSize = 14.000
speed.TextWrapped = true

mine.Name = "mine"
mine.Parent = Frame
mine.BackgroundColor3 = Color3.fromRGB(123, 255, 247
