-- LYX Scripts | Saber Simulator Compact UI - Only Main Tab + Auto Buy
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local Header = Instance.new("TextLabel")
local TabsFrame = Instance.new("Frame")
local MainTabButton = Instance.new("TextButton")
local MainTabFrame = Instance.new("Frame")

-- Feature Buttons
local AutoSwingButton = Instance.new("TextButton")
local AutoSellButton = Instance.new("TextButton")
local AutoBossButton = Instance.new("TextButton")
local AutoBuySaberButton = Instance.new("TextButton")
local AutoBuyDNAButton = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

-- Main Frame
MainFrame.Size = UDim2.new(0, 250, 0, 400)
MainFrame.Position = UDim2.new(0.5, -125, 0.5, -200)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Parent = ScreenGui

UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = MainFrame

-- Header
Header.Size = UDim2.new(1, 0, 0, 30)
Header.BackgroundTransparency = 1
Header.Text = "LYX Scripts | Saber Sim"
Header.TextColor3 = Color3.fromRGB(255, 255, 255)
Header.Font = Enum.Font.SourceSansBold
Header.TextSize = 18
Header.Parent = MainFrame

-- Tabs Frame
TabsFrame.Size = UDim2.new(1, 0, 0, 30)
TabsFrame.Position = UDim2.new(0, 0, 0, 30)
TabsFrame.BackgroundTransparency = 1
TabsFrame.Parent = MainFrame

MainTabButton.Size = UDim2.new(0, 80, 0, 30)
MainTabButton.Position = UDim2.new(0, 5, 0, 0)
MainTabButton.Text = "Main"
MainTabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
MainTabButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
MainTabButton.Parent = TabsFrame

-- Main Tab Frame
MainTabFrame.Size = UDim2.new(1, -20, 1, -70)
MainTabFrame.Position = UDim2.new(0, 10, 0, 65)
MainTabFrame.BackgroundTransparency = 1
MainTabFrame.Parent = MainFrame

-- Helper to create feature buttons
local function createToggleButton(yPos, text)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(1, -20, 0, 40)
    button.Position = UDim2.new(0, 0, 0, yPos)
    button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    button.Text = text .. ": OFF"
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Font = Enum.Font.SourceSans
    button.TextSize = 18
    button.Parent = MainTabFrame
    return button
end

-- Buttons
AutoSwingButton = createToggleButton(0, "Auto Swing")
AutoSellButton = createToggleButton(45, "Auto Sell")
AutoBossButton = createToggleButton(90, "Auto Boss")
AutoBuySaberButton = createToggleButton(135, "Auto Buy Saber")
AutoBuyDNAButton = createToggleButton(180, "Auto Buy DNA")

-- Logic
local autoSwingOn = false
local autoSellOn = false
local autoBossOn = false
local autoBuySaberOn = false
local autoBuyDNAOn = false

-- Auto Swing
AutoSwingButton.MouseButton1Click:Connect(function()
    autoSwingOn = not autoSwingOn
    AutoSwingButton.Text = "Auto Swing: " .. (autoSwingOn and "ON" or "OFF")
    if autoSwingOn then
        task.spawn(function()
            while autoSwingOn do
                game:GetService("ReplicatedStorage").Events.SwingSaber:FireServer()
                task.wait(0.1)
            end
        end)
    end
end)

-- Auto Sell
AutoSellButton.MouseButton1Click:Connect(function()
    autoSellOn = not autoSellOn
    AutoSellButton.Text = "Auto Sell: " .. (autoSellOn and "ON" or "OFF")
    if autoSellOn then
        task.spawn(function()
            while autoSellOn do
                game:GetService("ReplicatedStorage").Events.SellStrength:FireServer()
                task.wait(1)
            end
        end)
    end
end)

-- Auto Boss
AutoBossButton.MouseButton1Click:Connect(function()
    autoBossOn = not autoBossOn
    AutoBossButton.Text = "Auto Boss: " .. (autoBossOn and "ON" or "OFF")
    if autoBossOn then
        task.spawn(function()
            while autoBossOn do
                local args = {
                    [1] = {
                        [1] = workspace.Gameplay.Boss.BossHolder.Boss
                    }
                }
                game:GetService("Players").LocalPlayer.Character.Starter.RemoteClick:FireServer(unpack(args))
                task.wait(0.1)
            end
        end)
    end
end)

-- Auto Buy Saber
AutoBuySaberButton.MouseButton1Click:Connect(function()
    autoBuySaberOn = not autoBuySaberOn
    AutoBuySaberButton.Text = "Auto Buy Saber: " .. (autoBuySaberOn and "ON" or "OFF")
    if autoBuySaberOn then
        task.spawn(function()
            while autoBuySaberOn do
                local args = { [1] = "BuyAllWeapons" }
                game:GetService("ReplicatedStorage").Events.UIAction:FireServer(unpack(args))
                task.wait(5)
            end
        end)
    end
end)

-- Auto Buy DNA
AutoBuyDNAButton.MouseButton1Click:Connect(function()
    autoBuyDNAOn = not autoBuyDNAOn
    AutoBuyDNAButton.Text = "Auto Buy DNA: " .. (autoBuyDNAOn and "ON" or "OFF")
    if autoBuyDNAOn then
        task.spawn(function()
            while autoBuyDNAOn do
                local args = { [1] = "BuyAllDNAs" }
                game:GetService("ReplicatedStorage").Events.UIAction:FireServer(unpack(args))
                task.wait(5)
            end
        end)
    end
end)
