--Start

local function dupeItem(itemPath, maxTeleports)
    if itemPath then
        local teleportCount = 0
        while teleportCount < maxTeleports do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = itemPath.CFrame
            clickNormally(itemPath)
            teleportCount = teleportCount + 1
            wait(0.01) -- Tempo de espera para evitar travamento
        end
    end
end

local function getExecutor()
    return identifyexecutor and identifyexecutor() or "Unknown"
end

local function getPlayerCount()
    return #Players:GetPlayers()
end

local function getGameName()
    return game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId).Name
end

local function lagarServer()
--Spam
    local ghostMeterPath = workspace:FindFirstChild("WorkspaceCom"):FindFirstChild("001_GiveTools"):FindFirstChild("ElectricGuitar")
    if ghostMeterPath then
        local teleportCount = 0
        local maxTeleports = 99999999999999999999999999

        while teleportCount < maxTeleports do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = ghostMeterPath.CFrame
            clickNormally(ElectricGuitar)
            teleportCount = teleportCount + 1
            wait(0.1) -- Executa rapidamente
        end
    else
        warn("Item ElectricGuitar não encontrado.")
    end
end

--Test v1
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/Zeltau663/Ksepdo3jrmfoej3u44j/refs/heads/main/Zkm')))()
OrionLib:MakeNotification({
	Name = "inf",
	Content = "Bem - Vindo Ao Bloodyhub, Pode conter bugs e falhas!",
	Image = "rbxassetid://4483345998",
	Time = 10
})
local Window = OrionLib:MakeWindow({Name = "RDSCRIPTS HUB", HidePremium = false, SaveConfig = true, ConfigFolder = "Zalonteam",IntroEnabled = true, IntroText = "Zalon Team", IntroIcon = "rbxassetid://123573570247796"})
local flingActive = false
local loopFlingActive = false
local selectedPlayer = nil
local bodyVelocity, bodyAngularVelocity

local function startFling()
    if flingActive or not selectedPlayer then return end
    flingActive = true

    local character = game.Players.LocalPlayer.Character
    local targetCharacter = selectedPlayer.Character
    if not character or not targetCharacter then return end
    local hrp = character:WaitForChild("HumanoidRootPart")
    local targetHrp = targetCharacter:WaitForChild("HumanoidRootPart")

    -- Change character size down
    local args = {
        [1] = "CharacterSizeDown",
        [2] = 5
    }
    game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
  
  -- Equipa o item 'Couch'
  local args = {
[1] = "PickingTools",
[2] = "Couch"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))
  
  -- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end
  
    bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.Velocity = Vector3.new(100, 999, 100)
    bodyVelocity.MaxForce = Vector3.new(9999, 9999, 9999)
    bodyVelocity.Parent = hrp

    bodyAngularVelocity = Instance.new("BodyAngularVelocity")
    bodyAngularVelocity.AngularVelocity = Vector3.new(9999, 9999, 9999)
    bodyAngularVelocity.MaxTorque = Vector3.new(999999, 999999, 999999)
    bodyAngularVelocity.Parent = hrp

    game:GetService("RunService").Stepped:Connect(function()
        if flingActive then
            hrp.CFrame = targetHrp.CFrame
            hrp.CFrame = hrp.CFrame * CFrame.Angles(0, math.rad(10), 0)
        end
    end)
end

local function stopFling()
    if not flingActive then return end
    flingActive = false

    -- Change character size up
    local args = {
        [1] = "CharacterSizeUp",
        [2] = 1
    }
    game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

    if bodyVelocity then bodyVelocity:Destroy() end
    if bodyAngularVelocity then bodyAngularVelocity:Destroy() end
end

local function loopFling()
    while loopFlingActive do
        if selectedPlayer and selectedPlayer.Character then
            startFling()
            wait(0.1)
            stopFling()
        end
        wait(0.1)
    end
end

local function updatePlayerList()
local players = game.Players:GetPlayers()
local playerNames = {}
for _, player in ipairs(players) do
table.insert(playerNames, player.Name)
end
return playerNames
end

local MTab = Window:MakeTab({
Name = "Main",
Icon = "rbxassetid://4483345998",
PremiumOnly = false
})

local SSection = MTab:AddSection({ Name = "Good" })

MTab:AddButton({
    Name = "Davi babimet | Davi script",
    Callback = function()
    local args = {
    "CharacterChange",
    {
        14731377941,
        14731377894,
        14731377875,
        14731384498,
        14731377938,
        0
    },
    ""
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Avata1rOrigina1l"):FireServer(unpack(args))
    end
})

local CreditosSection = MTab:AddSection({ Name = "créditos" })

CreditosSection:AddLabel ("zeltauone")

local RunService = game:GetService("RunService")
local Stats = game:GetService("Stats")
local player = game.Players.LocalPlayer

-- FPS
local FPSSection = MTab:AddSection({Name = "FPS"})

-- Adiciona o parágrafo para FPS
local fpsParagraph = FPSSection:AddParagraph("FPS", "Calculando...")

-- Adiciona outros parágrafos
FPSSection:AddParagraph("Limite de FPS", "60")
FPSSection:AddParagraph("Desempenho", "Estável: Sim")

-- Variáveis para cálculo de FPS
local lastTime = tick()
local frameCount = 0

RunService.RenderStepped:Connect(function()
    frameCount = frameCount + 1
    local currentTime = tick()

    if currentTime - lastTime >= 1 then
        local fps = frameCount
        -- Atualiza o texto do parágrafo FPS com o valor calculado
        fpsParagraph:Set("" .. tostring(fps))  -- Atualiza corretamente o valor do FPS no OrionLib
        frameCount = 0
        lastTime = currentTime
    end
end)

-- Informações sobre o Jogo
local GameSection = MTab:AddSection({Name = "Jogo"})

-- Parágrafo para quantidade de jogadores
local PlayersLabel = GameSection:AddParagraph("Jogadores", "Carregando...")

-- Parágrafo para nome e ID do jogo
GameSection:AddParagraph("Nome", "brookhaven")
GameSection:AddParagraph("ID", tostring(game.GameId))

-- Função para atualizar a quantidade de jogadores
local function updatePlayerCount()
    local playerCount = #game.Players:GetPlayers()  -- Contagem de jogadores no jogo
    PlayersLabel:Set("Jogadores: " .. tostring(playerCount))  -- Atualiza o texto com a quantidade de jogadores
end

-- Atualiza a contagem de jogadores a cada 1 segundo
game:GetService("RunService").Heartbeat:Connect(function()
    updatePlayerCount()
end)

-- Informações do Jogador
local PlayerSection = MTab:AddSection({Name = "Jogador"})
local PlayerStatus = PlayerSection:AddParagraph("Status", "Online")
PlayerSection:AddParagraph("Nome", player.Name)
PlayerSection:AddParagraph("ID", tostring(player.UserId))

-- Atualização em tempo real
RunService.Heartbeat:Connect(function()
    -- Atualizar FPS
    FPSLabel:Set("FPS Atual", tostring(math.floor(workspace:GetRealPhysicsFPS())))

    -- Atualizar número de jogadores
    PlayersLabel:Set("Jogadores", tostring(#game.Players:GetPlayers()))

    -- Atualizar ping
    PingLabel:Set("Ping", Stats.Network.ServerStatsItem["Data Ping"]:GetValueString())

    -- Atualizar status do jogador
    PlayerStatus:Set("Status", player:IsInGroup(12345678) and "Membro de Grupo" or "Sem Grupo")
end)

local PaTab = Window:MakeTab({
Name = "Parceiros",
Icon = "rbxassetid://4483345998",
PremiumOnly = false
})

local PSection = PaTab:AddSection({ Name = "" })

PSection:AddLabel ("Parceiros")

PSection:AddParagraph("Thiago Script", "canal parceiro")
PSection:AddParagraph("Davi Script", "canal parceiro")
PSection:AddParagraph("Eclipse Sc", "canal parceiro")

local Tab = Window:MakeTab({
Name = "Troll",
Icon = "rbxassetid://4483345998",
PremiumOnly = false
})
local Section = Tab:AddSection({
	Name = "KILL TYPES"
})

local function couch()
local args = {
[1] = "PickingTools",
[2] = "Couch"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))
end

local function shoppingCart()
local args = {
[1] = "PickingTools",
[2] = "ShoppingCart"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))
end

local function stretcher()
local args = {
[1] = "PickingTools",
[2] = "Stretcher"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))
end

Tab:AddDropdown({
Name = "Kill Types",
Default = "",
Options = {"Couch", "Shopping Cart", "Stretcher"},
Callback = function(value)
if value == "Couch" then
couch()
elseif value == "Shopping Cart" then
shoppingCart()
elseif value == "Stretcher" then
stretcher()
end
end
})
local Section = Tab:AddSection({
	Name = "Damage Player"
})

local function WatherAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-72.37123107910156, -10.816083908081055, 112.93341827392578) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

-- Lista de Players para Bring Avançado
local killAdvancedPlayerList = {}
for _, player in ipairs(game.Players:GetPlayers()) do
table.insert(killAdvancedPlayerList, player.Name)
end

local function updatePlayerList()
local players = game.Players:GetPlayers()
local playerNames = {}
for _, player in ipairs(players) do
table.insert(playerNames, player.Name)
end
return playerNames
end

Tab:AddDropdown({
Name = "Selecionar Jogador",
Description = "Selecione o jogador alvo para o Bring Avançado",
Options = killAdvancedPlayerList,
Callback = function(playerName)
selectedKillAdvancedPlayer = playerName
end
})

Tab:AddButton({
Name = "Tornado Player",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
WatherAdvancedPlayer()
end
})
local Section = Tab:AddSection({
	Name = "Kills"
})
local selectedKillAdvancedPlayer = nil
local couchEquipped = false

local function killAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8.657157897949219, -222.3133087158203, -23.58349609375) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function FlyAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-107.91380310058594, -10.128937721252441, 261.37420654296875) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function SafeVoidAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(462.886474609375, -75.30844116210938, 123.47378540039062) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function BowAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-588.5294189453125, 8.251455307006836, -182.5675506591797) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function PlaneAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(665.856201171875, 3.6353466510772705, 89.86775970458984) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function LagAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(104.80880737304688, 34.60691833496094, 632.2498168945312) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function BringAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-570.4937133789062, 37.714874267578125, 963.8348999023438) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function SafeVoifAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(104.80880737304688, 34.60691833496094, 632.2498168945312) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function SkyAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(104.80880737304688, 34.60691833496094, 632.2498168945312) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function PriAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-783.1765747070312, -517.522216796875, 1115.422119140625) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function PrisionAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-783.1765747070312, -517.522216796875, 1115.422119140625) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

local function BugAdvancedPlayer()
if selectedKillAdvancedPlayer then
local player = game.Players:FindFirstChild(selectedKillAdvancedPlayer)
if player then
-- Equipa o item 'Couch' no inventário se ainda não estiver equipado
--big
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
local backpack = game.Players.LocalPlayer.Backpack
if backpack and not couchEquipped then
local couch = backpack:FindFirstChild("Couch")
if couch then
game.Players.LocalPlayer.Character.Humanoid:EquipTool(couch)
couchEquipped = true
else
print("O item 'Couch' não foi encontrado no seu inventário.")
end
end

-- Looping de teleportes no jogador selecionado da lista
while true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
wait(0.0) -- Intervalo entre cada teleporte, ajuste conforme necessário

-- Verifica se o jogador sentou no 'Couch' e realiza o teleporte para o céu
if player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.SeatPart then
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0) -- Teleporta para cima novamente
wait(0.0) -- Espera um pouco antes de teleportar de volta para evitar bugs
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(176.63543701171875, 594.9183959960938, 393.3529052734375) -- Teleporta de volta para a posição original
break -- Sai do loop após teleportar de volta
end
end

--Small
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))

-- Remove o item 'Couch' da mão do jogador após o teleporte para o céu
if couchEquipped then
local backpack = game.Players.LocalPlayer.Backpack
if backpack then
local couch = backpack:FindFirstChild("Couch")
if couch then
couch.Parent = nil -- Remove o 'Couch' do inventário
couchEquipped = false
end
end
end
else
print("Jogador não encontrado.")
end
else
print("Nenhum jogador selecionado para o Bring Avançado.")
end
end

-- Lista de Players para Bring Avançado
local killAdvancedPlayerList = {}
for _, player in ipairs(game.Players:GetPlayers()) do
table.insert(killAdvancedPlayerList, player.Name)
end

local function updatePlayerList()
local players = game.Players:GetPlayers()
local playerNames = {}
for _, player in ipairs(players) do
table.insert(playerNames, player.Name)
end
return playerNames
end

Tab:AddDropdown({
Name = "Selecionar Jogador",
Description = "Selecione o jogador alvo para o Bring Avançado",
Options = killAdvancedPlayerList,
Callback = function(playerName)
selectedKillAdvancedPlayer = playerName
end
})

Tab:AddButton({
Name = "Kill",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
killAdvancedPlayer()
end
})
Tab:AddButton({
Name = "Sky",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
BugAdvancedPlayer()
end
})
Tab:AddButton({
Name = "Bow Prision [NEW]",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
BowAdvancedPlayer()
end
})
Tab:AddButton({
Name = "Bug Kill",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
SkyAdvancedPlayer()
end
})

Tab:AddButton({
Name = "Freeze kill",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
LagAdvancedPlayer()
end
})

Tab:AddButton({
Name = "Kidnapping",
Description = "Equipa o item 'Couch' e teleporta o jogador selecionado",
Callback = function()
FlyAdvancedPlayer()
end
})
local Section = Tab:AddSection({
	Name = "Fling area"
})
local playerDropdown = Tab:AddDropdown({
Name = "Select Player",
Default = "",
Options = updatePlayerList(),
Callback = function(value)
selectedPlayer = game.Players:FindFirstChild(value)
end
})

Tab:AddButton({
Name = "Update Player List",
Callback = function()
playerDropdown:Refresh(updatePlayerList(), true)
end
})

Tab:AddButton({
Name = "Start Fling",
Callback = function()
startFling()
end
})

Tab:AddButton({
Name = "Stop Fling",
Callback = function()
stopFling()
end
})
local Section = Tab:AddSection({
    Name = "all"
})
Tab:AddButton({
	Name = "Fling all",
	Callback = function()
      	loadstring(game:HttpGet("https://pastebin.com/raw/zqyDSUWX"))()
  	end    
})
-- Variável para controlar o toggle
local teleportToggle = false

-- Função de teletransporte
local function teleportToPlayers()
    local localPlayer = game.Players.LocalPlayer
    local players = game.Players:GetPlayers()
    
    for _, player in pairs(players) do
        if not teleportToggle then break end -- Para se o toggle for desativado
        if player ~= localPlayer then
        --Ficar pequeno antes
        local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
            -- Teleporta para o jogador
            local character = player.Character
            if character and character:FindFirstChild("HumanoidRootPart") then
                local hrp = character.HumanoidRootPart
                localPlayer.Character.HumanoidRootPart.CFrame = hrp.CFrame
                wait(1) -- Aguarda 1 segundo para evitar problemas de sincronia
            end
        end
        -- Teleporta para (-8.657157897949219, -222.3133087158203, -23.58349609375)
        localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8.657157897949219, -222.3133087158203, -23.58349609375)
        wait(1) -- Aguarda antes de passar para o próximo jogador
    end
end

Tab:AddToggle({
    Name = "Kill All",
    Default = false,
    Callback = function(value)
        teleportToggle = value
        if teleportToggle then
            teleportToPlayers()
        end
    end
})

-- Variável para controlar o toggle
local teleportToggle = false

-- Função de teletransporte
local function teleportToSky()


--xaet

local args = {
[1] = "PickingTools",
[2] = "ShoppingCart"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))

--xaetttttt

local args = {
[1] = "PickingTools",
[2] = "Stretcher"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))

--Couch

local args = {
[1] = "PickingTools",
[2] = "Couch"
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))

--Equip itens

local function equiparItem(itemName)
    local player = game.Players.LocalPlayer
    local backpack = player:FindFirstChild("Backpack")
    
    if backpack then
        -- Verifica se o item já está no inventário
        local item = backpack:FindFirstChild(itemName)
        if item then
            -- Move o item para a mão do jogador, caso não esteja equipado
            local character = player.Character
            if character and not character:FindFirstChild(itemName) then
                item.Parent = character
                print(itemName .. " equipado!")
            else
                print(itemName .. " já está equipado.")
            end
        else
            print(itemName .. " não está no inventário.")
        end
    else
        print("Backpack não encontrado.")
    end
end

-- Checar e equipar Sniper e FireX
equiparItem("Couch")
equiparItem("ShoppingCart")
equiparItem("Stretcher")

    local localPlayer = game.Players.LocalPlayer
    local players = game.Players:GetPlayers()
    
    for _, player in pairs(players) do
        if not teleportToggle then break end -- Para se o toggle for desativado
        if player ~= localPlayer then
        --Ficar pequeno antes
        local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
            -- Teleporta para o jogador
            local character = player.Character
            if character and character:FindFirstChild("HumanoidRootPart") then
                local hrp = character.HumanoidRootPart
                localPlayer.Character.HumanoidRootPart.CFrame = hrp.CFrame
                wait(1) -- Aguarda 1 segundo para evitar problemas de sincronia
            end
        end
        -- Teleporta para (9999999827968, 9999999827968, 9999999827968)
        localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9999999827968, 9999999827968, 9999999827968)
        wait(1) -- Aguarda antes de passar para o próximo jogador
    end
end

Tab:AddToggle({
    Name = "Bug All",
    Default = false,
    Callback = function(value)
        teleportToggle = value
        if teleportToggle then
            teleportToSky()
        end
    end
})

-- Variáveis e serviços
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local TeleportToggle = false
local OriginalPosition

-- Função para teletransportar e voltar à posição original
local function TeleportToPlayers()
    while TeleportToggle do
        -- Salva a posição original do jogador
        if not OriginalPosition then
            OriginalPosition = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame
        end
        
        for _, player in ipairs(Players:GetPlayers()) do
            -- Ignora o jogador local
            if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                -- Teleporta para o jogador
                LocalPlayer.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
                wait(1) -- Espera 1 segundo antes de ir para o próximo jogador
                
                -- Retorna para a posição original
                if OriginalPosition then
                    LocalPlayer.Character.HumanoidRootPart.CFrame = OriginalPosition
                end
                wait(1) -- Espera 1 segundo antes de continuar
            end
        end
        
        -- Reseta a posição original se todos foram visitados
        OriginalPosition = nil
    end
end


Tab:AddToggle({
    Name = "Bring all",
    Default = false,
    Callback = function(Value)
        TeleportToggle = Value
        if TeleportToggle then
            TeleportToPlayers()
        end
    end
})
local Tab = Window:MakeTab({
Name = "Misc",
Icon = "rbxassetid://4483345998",
PremiumOnly = false
})

local Section = Tab:AddSection({
    Name = "Kick"
})

local Players = game:GetService("Players")
local playerNames = {}

local function updatePlayerList()
    playerNames = {}
    for _, player in pairs(Players:GetPlayers()) do
        table.insert(playerNames, player.Name)
    end
end

updatePlayerList()


local selectedPlayer = ""
local selectedReason = ""

Tab:AddDropdown({
    Name = "Select Player",
    Default = "",
    Options = playerNames,
    Callback = function(value)
        selectedPlayer = value
        print("Selected player: " .. value)
    end
})

Tab:AddButton({
    Name = "Update Player List",
    Callback = function()
        updatePlayerList()
        OrionLib:MakeNotification({
            Name = "Player List Updated",
            Content = "The player list has been updated.",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

Tab:AddDropdown({
    Name = "Select Reason",
    Default = "",
    Options = {"Web Namoro", "Exploits"},
    Callback = function(value)
        selectedReason = value
        print("Selected reason: " .. value)
    end
})

Tab:AddToggle({
    Name = "Loop Report",
    Default = false,
    Callback = function(value)
        while value do
            if selectedPlayer ~= "" and selectedReason ~= "" then
                print("Reporting " .. selectedPlayer .. " for " .. selectedReason)
                -- Aqui você pode adicionar o código para enviar a denúncia
            end
            wait(0.1)
        end
    end
})
local Section = Tab:AddSection({
    Name = "Notifications"
})
local Players = game:GetService("Players")
local notificationsEnabled = false

local function onPlayerAdded(player)
if notificationsEnabled then
game.StarterGui:SetCore("SendNotification", {
Title = "Player entered";
Text = player.Name .. " entrou no jogo";
Duration = 5;
})
end
end

local function onPlayerRemoving(player)
if notificationsEnabled then
game.StarterGui:SetCore("SendNotification", {
Title = "Player Left";
Text = player.Name .. " left the game";
Duration = 5;
})
end
end

local function toggleNotifications(toggleState)
notificationsEnabled = toggleState
if notificationsEnabled then
print("Notificações Ativadas")
else
print("Notificações Desativadas")
end
end

Tab:AddToggle({
Name = "Notify when player leaves/joins",
Default = false,
Callback = function(Value)
toggleNotifications(Value)
end
})

Players.PlayerAdded:Connect(onPlayerAdded)
Players.PlayerRemoving:Connect(onPlayerRemoving)

local Section = Tab:AddSection({
    Name = "Anti Functions"
})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")
local TeleportService = game:GetService("TeleportService")

local function disableLaggyFeatures()
for _, v in pairs(workspace:GetDescendants()) do
if v:IsA("ParticleEmitter") or v:IsA("Trail") or v:IsA("Smoke") or v:IsA("Fire") then
v.Enabled = false
end
end
end

Tab:AddToggle({
Name = "Anti Sit",
Default = false,
Callback = function(value)
if value then
RunService.Stepped:Connect(function()
if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
if LocalPlayer.Character.Humanoid.Sit then
LocalPlayer.Character.Humanoid.Sit = false
end
end
end)
end
end
})

Tab:AddToggle({
Name = "Anti Void",
Default = false,
Callback = function(value)
if value then
RunService.Stepped:Connect(function()
if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
if LocalPlayer.Character.HumanoidRootPart.Position.Y < -50 then
LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-118.54170227050781, 3.8526408672332764, -1.622152805328369)
end
end
end)
end
end
})

Tab:AddToggle({
Name = "Anti Kick",
Default = false,
Callback = function(value)
if value then
game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(child)
if child.Name == "ErrorPrompt" then
TeleportService:Teleport(game.PlaceId, LocalPlayer)
end
end)
end
end
})

Tab:AddToggle({
Name = "Anti Lag",
Default = false,
Callback = function(value)
if value then
disableLaggyFeatures()
workspace.DescendantAdded:Connect(function(descendant)
if descendant:IsA("ParticleEmitter") or descendant:IsA("Trail") or descendant:IsA("Smoke") or descendant:IsA("Fire") then
descendant.Enabled = false
end
end)
end
end
})
local Section = Tab:AddSection({
    Name = "Others Functions"
})

local function backToSize()
local args = {
[1] = "CharacterSizeUp",
[2] = 1
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args)) 
end

local function small()
local args = {
[1] = "CharacterSizeDown",
[2] = 5
}
game:GetService("ReplicatedStorage").RE:FindFirstChild("1Clothe1s"):FireServer(unpack(args))
end

Tab:AddDropdown({
Name = "Select Function - Stay small",
Default = "None",
Options = {"Back to size", "Small"},
Callback = function(option)
if option == "Back to size" then
backToSize()
elseif option == "Small" then
small()
end
end
})

local function danger()
local args = {
    [1] = "RolePlayName",
    [2] = "D\205\156\205\137\205\150\204\175A\204\162\204\169\204\150N\205\156\205\153\204\174\204\166\204\173G\204\167\204\150\205\154\205\150\205\149\204\175E\204\167\204\170\205\141\204\153\204\179R\205\162\205\149\204\150\204\171"
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1RPNam1eTex1t"):FireServer(unpack(args))
end

local function hacker()
local args = {
    [1] = "RolePlayName",
    [2] = "H\204\167\204\159\205\150\205\149\204\172\205\148A\204\161\204\172\205\153\205\133\204\174\205\153C\204\168\205\141\204\164\204\150K\204\168\204\174\204\169\204\170E\204\168\204\179\204\169\204\164R\204\161\205\149\205\147\204\163"
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1RPNam1eTex1t"):FireServer(unpack(args))
end

local function invasion()
local args = {
    [1] = "RolePlayName",
    [2] = "I\205\157\204\132\204\128\204\131\204\143n\204\155\205\155\204\132\204\142\204\137v\205\158\204\139\204\137\204\190\205\132a\204\155\204\132\205\131s\205\158\205\140\204\154\204\139\204\133i\204\155\204\130\204\136\204\138\204\136\204\129o\205\161\204\129\204\136n\205\160\205\128\204\129\205\129\204\146\205\132"
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1RPNam1eTex1t"):FireServer(unpack(args))
end

Tab:AddDropdown({
Name = "Select Name - Zalgo",
Default = "None",
Options = {"Danger", "Hacker", "Invasion"},
Callback = function(option)
if option == "Danger" then
danger()
elseif option == "Hacker" then
hacker()
elseif option == "Invasion" then
invasion()
end
end
})
local Section = Tab:AddSection({
	Name = "Pull player information"
})
local selectedPlayer = nil

local function getPlayerId(player)
    return player.UserId
end

local function getJoinDate(player)
    return player.AccountAge
end

local function copyName(player)
    setclipboard(player.Name)
end

local function createESP(player)
    local esp = Instance.new("Highlight")
    esp.Parent = player.Character
    esp.Adornee = player.Character
    esp.FillColor = Color3.new(1, 0, 0)
    esp.FillTransparency = 0.5
    esp.OutlineColor = Color3.new(1, 1, 1)
    esp.OutlineTransparency = 0
end

local function updateDropdown()
    local players = game:GetService("Players"):GetPlayers()
    local playerNames = {}
    for _, player in ipairs(players) do
        table.insert(playerNames, player.Name)
    end
    return playerNames
end

Tab:AddDropdown({
    Name = "Players",
    Default = "",
    Options = updateDropdown(),
    Callback = function(value)
        selectedPlayer = game:GetService("Players"):FindFirstChild(value)
    end
})

Tab:AddButton({
    Name = "Player id",
    Callback = function()
        if selectedPlayer then
            OrionLib:MakeNotification({
                Name = "Player ID",
                Content = "ID: " .. getPlayerId(selectedPlayer),
                Image = "rbxassetid://4483345998",
                Time = 5
            })
        end
    end
})

Tab:AddButton({
    Name = "JoinDate (see when the player entered the game)",
    Callback = function()
        if selectedPlayer then
            OrionLib:MakeNotification({
                Name = "Join Date",
                Content = "Account Age: " .. getJoinDate(selectedPlayer) .. " days",
                Image = "rbxassetid://4483345998",
                Time = 5
            })
        end
    end
})

Tab:AddButton({
    Name = "Copyname",
    Callback = function()
        if selectedPlayer then
            copyName(selectedPlayer)
            OrionLib:MakeNotification({
                Name = "Copy Name",
                Content = "Name copied to clipboard",
                Image = "rbxassetid://4483345998",
                Time = 5
            })
        end
    end
})
local Section = Tab:AddSection({
    Name = "Horror Song (GamePass - Only Skateboards, Overboards between others...)"
})

local songs = {
["Song 1"] = "933230732",
["Song 2"] = "300533476",
["Song 3"] = "472763153",
["Song 4"] = "300533288",
["Song 5"] = "1840020395",
["Song 6"] = "1840020758",
["Song 7"] = "567545087",
["Song 8"] = "5546573724",
["Song 9"] = "8584754036",
["Song 10"] = "8604878451",
}

local selectedSong = "Song 1"

local function executeSong(songId)
local args = {
[1] = "PickingScooterMusicText",
[2] = songId
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1NoMoto1rVehicle1s"):FireServer(unpack(args))
end

Tab:AddDropdown({
Name = "Select Horror Song",
Default = "Song 1",
Options = {"Song 1", "Song 2", "Song 3", "Song 4", "Song 5", "Song 6", "Song 7", "Song 8", "Song 9", "Song 10"},
Callback = function(value)
selectedSong = value
end
})


Tab:AddButton({
Name = "Execute Song",
Callback = function()
executeSong(songs[selectedSong])
end
})

local songs = {
["Song 1"] = "16662829817",
["Song 2"] = "14145618923",
["Song 3"] = "6841685130",
["Song 4"] = "13530439502",
["Song 5"] = "6676732301",
["Song 6"] = "15689448519"
}

local selectedSong = "Song 1"

local function executeSong(songId)
local args = {
[1] = "PickingScooterMusicText",
[2] = songId
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1NoMoto1rVehicle1s"):FireServer(unpack(args))
end

Tab:AddDropdown({
Name = "Select Phonk Song",
Default = "Song 1",
Options = {"Song 1", "Song 2", "Song 3", "Song 4", "Song 5", "Song 6"},
Callback = function(value)
selectedSong = value
end
})

Tab:AddButton({
Name = "Execute Song",
Callback = function()
executeSong(songs[selectedSong])
end
})
local Section = Tab:AddSection({
    Name = "Fire Function"
})
Tab:AddButton({
Name = "Hand Fire",
Callback = function()
OrionLib:MakeNotification({
	Name = "You only have 6 seconds!",
	Content = "Click the button under the table to get the fire hand!",
	Image = "rbxassetid://4483345998",
	Time = 6
})
 local plr = game.Players.LocalPlayer
local char = plr.Character
local hrp = char.HumanoidRootPart

hrp.CFrame = CFrame.new(-350.8634338378906, 3.6591341495513916, 100.41527557373047)
wait(6)
 local plr = game.Players.LocalPlayer
local char = plr.Character
local hrp = char.HumanoidRootPart

hrp.CFrame = CFrame.new(-24.741954803466797, 3.0249993801116943, -66.39078521728516)
    end
})
local Tab = Window:MakeTab({
Name = "House",
Icon = "rbxassetid://4483345998",
PremiumOnly = false
})

-- Variáveis globais
local Enabled = false
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Função para alternar noclip
local function toggleNoclip()
    noclipEnabled = not noclipEnabled

    if noclipEnabled then
        OrionLib:MakeNotification({
            Name = "UnBan Enabled",
            Content = "Você agora pode atravessar objetos.",
            Image = "rbxassetid://4483345998", -- Ícone opcional
            Time = 5
        })
    else
        OrionLib:MakeNotification({
            Name = "UnBan Disable",
            Content = "Modo normal ativado.",
            Image = "rbxassetid://4483345998", -- Ícone opcional
            Time = 5
        })
    end
end

-- Função para manipular colisões
local function noclipLoop()
    while wait() do
        if noclipEnabled then
            for _, part in pairs(character:GetDescendants()) do
                if part:IsA("BasePart") and part.CanCollide then
                    part.CanCollide = false
                end
            end
        else
            for _, part in pairs(character:GetDescendants()) do
                if part:IsA("BasePart") and not part.CanCollide then
                    part.CanCollide = true
                end
            end
        end
    end
end


Tab:AddButton({
    Name = "Ativar/Desativar UnBan",
    Callback = toggleNoclip
})

-- Inicia o loop de noclip em uma thread separada
spawn(noclipLoop)

local Section = Tab:AddSection({
    Name = "Ban tool"
})

-- Lista de Jogadores
local selectedPlayer = nil
local playerNames = {}

-- Atualizar lista de jogadores
local function updatePlayerList()
    playerNames = {}
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= Players.LocalPlayer then
            table.insert(playerNames, player.Name)
        end
    end
end

-- Banir jogador
local function banPlayer(playerName)
    local targetPlayer = Players:FindFirstChild(playerName)
    if targetPlayer and targetPlayer.Character then
        local args = {
            [1] = "BanPlayerFromHouse",
            [2] = targetPlayer,
            [3] = targetPlayer.Character
        }
        local remoteEvent = ReplicatedStorage.RE:FindFirstChild("1Playe1rTrigge1rEven1t")
        if remoteEvent then
            remoteEvent:FireServer(unpack(args))
        end
    end
end

local function updatePlayerList()
local players = game.Players:GetPlayers()
local playerNames = {}
for _, player in ipairs(players) do
table.insert(playerNames, player.Name)
end
return playerNames
end

Tab:AddDropdown({
    Name = "Selecione um Jogador",
    Options = playerNames,
    Callback = function(value)
        selectedKillAdvancedPlayer = playerName
    end
})

Tab:AddButton({
    Name = "Atualizar Lista de Jogadores",
    Callback = function()
        updatePlayerList()
        OrionLib:MakeNotification({
            Name = "Atualizado",
            Content = "Lista de jogadores foi atualizada.",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

Tab:AddToggle({
    Name = "Ativar Loop de Ban",
    Default = false,
    Callback = function(value)
        if value and selectedPlayer then
            while value do
                banPlayer(selectedPlayer)
                task.wait(1) -- Delay para evitar spam excessivo
            end
        end
    end
})
local Section = Tab:AddSection({
    Name = "Loops "
})
local toggleState = false
local function toggleCurtains()
while toggleState do
local args = {
[1] = "Curtains"
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1Player1sHous1e"):FireServer(unpack(args))
wait(1) -- ajusta o tempo de espera conforme necessário
end
end

Tab:AddToggle({
Name = "Toggle Curtains",
Default = false,
Callback = function(value)
toggleState = value
if toggleState then
toggleCurtains()
end
end
})

local toggleState = false
local function togglePool()
while toggleState do
local args = {
[1] = "PoolOnOff"
}

game:GetService("ReplicatedStorage").RE:FindFirstChild("1Player1sHous1e"):FireServer(unpack(args))
wait(1) -- ajusta o tempo de espera conforme necessário
end
end

Tab:AddToggle({
Name = "Toggle Pool",
Default = false,
Callback = function(value)
toggleState = value
if toggleState then
togglePool()
end
end
})

local toggleState = false
local function toggleGarageDoor()
while toggleState do
local args = {
[1]
