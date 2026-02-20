--[[ Deobfuscated by MLRTAKEN | Full Source Leak ]]

loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = CreateWindow({
    Title = "Dupe Script Version",
    SubTitle = "GG-HUB (FREE)",
    MadeBy = "@farxss",
    TabWidth = 140,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true,
    Theme = "Darker",
    MinimizeKey = Enum.KeyCode.LeftControl
})

local Main = Window:AddTab({ Title = "¡ Dupe & More", Icon = "folder" })
local Misc = Window:AddTab({ Title = "¡ Auto", Icon = "list-plus" })
local Craft = Window:AddTab({ Title = "¡ Crafts", Icon = "axe" })
local Other = Window:AddTab({ Title = "¡ Others", Icon = "table" })
local Visual = Window:AddTab({ Title = "¡ Visual", Icon = "zoom-in" })
local Fun = Window:AddTab({ Title = "¡ Fun", Icon = "smile" })
local upd = Window:AddTab({ Title = "¡ Update Log", Icon = "book" })
local Fix = Window:AddTab({ Title = "¡ Credits & Discord", Icon = "info" })

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")

Main:AddParagraph({
    Title = "IF YOU WANT INFINITE ITEM METHOD DO:",
    Content = "- You need 2 Account\n- Put a item to stand\n- After Putting item Drop Putted item\n- Then Buy Putted Item From Stand With Other Account\n- And Accept Trade With 2 Account"
})

Main:AddParagraph({
    Title = "If you still dont understand",
    Content = "Youtube Tut Video: FarxScripts"
})

Main:AddDropdown("Mode_Selection", {
    Title = "Mode",
    Values = {"Buyer", "Giver"},
    Default = "Buyer"
})

Main:AddInput("Item_Name", {
    Title = "Item Name",
    Default = ""
})

Main:AddInput("Custom_Value", {
    Title = "Set Price",
    Default = "0"
})

Main:AddToggle("Dupe_Toggle", {
    Title = "Dupe",
    Default = false
})

Main:AddToggle("AutoBuy_Toggle", {
    Title = "Auto Buy Aura",
    Default = false
})

Main:AddToggle("Click_And_NoClip_Toggle", {
    Title = "Auto Place Stands",
    Default = true
})

Main:AddSection("Others")

Main:AddToggle("Enable Inventory", {
    Title = "Enable/Disable Inventory",
    Default = true,
    Callback = function(Value)
        game:GetService("StarterGui"):SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, Value)
    end
})

Main:AddButton({
    Title = "Check Item Amount",
    Description = "Check holding item value",
    Callback = function()
        local tool = LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Tool")
        if tool and tool:FindFirstChild("Items") then
            HoldingItem.Text = tostring(tool.Items.Value)
        else
            HoldingItem.Text = "0"
        end
    end
})

Main:AddButton({
    Title = "Anti Afk",
    Description = "Prevents you from getting kicked after 20 minutes. Shows up w gui",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Farx11122/TestAntiAfk/main/AntiAfkWithGui"))()
    end
})

Main:AddButton({
    Title = "Goto Safe Place",
    Description = "Creates a baseplate and teleports you",
    Callback = function()
        local part = Instance.new("Part")
        part.Size = Vector3.new(50, 1, 50)
        part.Position = Vector3.new(0, 100, 0)
        part.Anchored = true
        part.CanCollide = true
        part.BrickColor = BrickColor.new("Cyan")
        part.Parent = Workspace
        LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = CFrame.new(0, 105, 0)
    end
})

Main:AddButton({
    Title = "Remove tools (DontHold)",
    Callback = function()
        for _, tool in ipairs(LocalPlayer.Backpack:GetChildren()) do
            if tool:IsA("Tool") or tool:IsA("HopperBin") then
                tool:Destroy()
            end
        end
        print("Tüm tool'lar backpack'ten silindi!")
    end
})

Misc:AddSection("Fast drop")

Misc:AddInput("Input", {
    Title = "Name of item",
    Default = "",
    Placeholder = "Name of item",
    Numeric = true,
    Finished = true
})

Misc:AddToggle("Collect", {
    Title = "Collect First Then drop",
    Default = false
})

Misc:AddToggle("Duplicate", {
    Title = "Fast Drop",
    Default = false,
    Callback = function(Value)
    end
})

Misc:AddSection("Auto Buy")

Misc:AddInput("ItemToAuto", {
    Title = "Item Name",
    Default = "",
    Placeholder = "item name",
    Numeric = false,
    Finished = true
})

Misc:AddToggle("ToggleAutoBuy", {
    Title = "Auto Buy",
    Default = false,
    Callback = function(Value)
        _G.ItemToAuto = Value
    end
})

Misc:AddSection("Auto Sell")

Misc:AddInput("ItemName", {
    Title = "Item Name",
    Placeholder = "Type item name..."
})

Misc:AddToggle("ToggleSeller", {
    Title = "Auto Sell",
    Default = false,
    Callback = function(Value)
        print("Auto Sell is active.")
    end
})

Misc:AddSection("Auto features")

Misc:AddToggle("Toggle Jump Event", {
    Title = "Auto A/C",
    Default = false
})

Misc:AddToggle("Toggle Jet Farm", {
    Title = "Jet Farm",
    Default = false
})

Misc:AddToggle("SpinWheel", {
    Title = "AutoSpinWheel",
    Default = false,
    Callback = function(Value)
        IsLooping = Value
        while IsLooping do
            ReplicatedStorage.RemoteEvents.SpinWheel:InvokeServer()
            wait(1)
        end
    end
})

Craft:AddToggle("Craft Toggle Beacon", {
    Title = "LoopCraft Beacon",
    Default = false,
    Callback = function(Value)
        IsLooping = Value
        task.spawn(function()
            while IsLooping do
                CraftBeacon()
                wait(1)
            end
        end)
    end
})

Craft:AddToggle("Craft Toggle FireEye", {
    Title = "LoopCraft FireEye",
    Default = false,
    Callback = function(Value)
        IsLooping = Value
        task.spawn(function()
            while IsLooping do
                CraftFireEye()
                wait(1)
            end
        end)
    end
})

Craft:AddToggle("Craft Toggle NewCraft", {
    Title = "LoopCraft Waste",
    Default = false,
    Callback = function(Value)
        IsLooping = Value
        task.spawn(function()
            while IsLooping do
                CraftNewCraft()
                wait(1)
            end
        end)
    end
})

Craft:AddButton({
    Title = "Load all recipes gui",
    Description = "See all book recipes in gui",
    Callback = function()
        local LuxuryBookGUI = Instance.new("ScreenGui")
        LuxuryBookGUI.Name = "LuxuryBookGUI"
        LuxuryBookGUI.Parent = LocalPlayer:WaitForChild("PlayerGui")

        local MainFrame = Instance.new("Frame")
        MainFrame.Name = "MainFrame"
        MainFrame.Draggable = true
        MainFrame.Size = UDim2.new(0, 500, 0, 600)
        MainFrame.Position = UDim2.new(0.5, -250, 0.5, -300)
        MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
        MainFrame.BorderSizePixel = 2
        MainFrame.Parent = LuxuryBookGUI

    end
})

Other:AddToggle("Freeze Character", {
    Title = "Freeze Character",
    Default = false,
    Callback = function(Value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            LocalPlayer.Character.HumanoidRootPart.Anchored = Value
        end
    end
})

Other:AddButton({
    Title = "Enable X-Ray",
    Description = "Enable Xray mode for free",
    Callback = function()
        if LocalPlayer:FindFirstChild("XRay") then
            LocalPlayer.XRay.Value = true
            print("X-Ray enabled")
        else
            print("X-Ray property not found")
        end
    end
})

Other:AddButton({
    Title = "Anti sit",
    Description = "prevents sitting",
    Callback = function()
        LocalPlayer.Character:WaitForChild("Humanoid").StateChanged:Connect(function(_, new)
            if new == Enum.HumanoidStateType.Seated then
                LocalPlayer.Character.Humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
            end
        end)
    end
})

Other:AddButton({
    Title = "StartTimer",
    Description = "Shows up a timer gui on screen",
    Callback = function()
        local TimerGUI = Instance.new("ScreenGui")
        TimerGUI.Name = "TimerGUI"
        TimerGUI.ResetOnSpawn = false
        TimerGUI.DisplayOrder = 999
        TimerGUI.Parent = LocalPlayer.PlayerGui

        local Frame = Instance.new("Frame")
        Frame.Size = UDim2.new(0, 200, 0, 50)
        Frame.Position = UDim2.new(0.5, -100, 0, 10)
        Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
        Frame.BorderSizePixel = 2
        Frame.Parent = TimerGUI

        local Label = Instance.new("TextLabel")
        Label.Size = UDim2.new(1, 0, 1, 0)
        Label.BackgroundTransparency = 1
        Label.TextColor3 = Color3.fromRGB(255, 255, 255)
        Label.Font = Enum.Font.SourceSans
        Label.TextSize = 20
        Label.Text = "Timer: 0"
        Label.Parent = Frame

        local start = tick()
        while wait(1) do
            local elapsed = math.floor(tick() - start)
            Label.Text = "Timer: " .. elapsed
            if elapsed >= 60 then
                Label.Text = "Timer: Done!"
                break
            end
        end
    end
})

Other:AddButton({
    Title = "AntiLag",
    Description = "Makes your game smooth",
    Callback = function()
        for _, v in ipairs(Workspace:GetDescendants()) do
            if v:IsA("BasePart") and not v:IsDescendantOf(LocalPlayer.Character) then
                v.CanCollide = false
                v.Anchored = true
            end
        end
    end
})

Other:AddButton({
    Title = "No Object",
    Description = "Remove objects on map.",
    Callback = function()
        for _, v in ipairs({
            Workspace:FindFirstChild("Map"),
            Workspace:FindFirstChild("Decorations"),
            Workspace:FindFirstChild("GroupReward"),
            Workspace:FindFirstChild("ClothingRack"),
            Workspace:FindFirstChild("FeaturedItem"),
            Workspace:FindFirstChild("FirstWinner"),
            Workspace:FindFirstChild("WeeklyDrop"),
            Workspace:FindFirstChild("CodePad")
        }) do
            if v then v:Destroy() end
        end
    end
})

Other:AddButton({
    Title = "Run Infinite yield",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
    end
})

Fun:AddInput("Target_Player_Name", {
    Title = "Player Name",
    Default = ""
})

Fun:AddToggle("Targeting_Toggle", {
    Title = "Targeting",
    Default = false
})

Fun:AddInput("Radius_Input", {
    Title = "Orbit Radius",
    Default = "10"
})

Fun:AddInput("Speed_Input", {
    Title = "Orbit Speed",
    Default = "1"
})

upd:AddParagraph({
    Title = "Last updates",
    Content = "-Removed Message Gui\n+Auto Buy Aura is Faster now\n+Added Auto sell. and more.. Join discord"
})

Fix:AddButton({
    Title = "Click to copy discord server link",
    Description = "Credits to 4farx | @farxss",
    Callback = function()
        setclipboard("https://discord.gg/hx94NxwMSQ")
        toclipboard("https://discord.gg/hx94NxwMSQ")
    end
})

do
    local ToggleUiGGH = Instance.new("ScreenGui")
    ToggleUiGGH.Name = "GGHUB"
    ToggleUiGGH.Parent = game.CoreGui

    local Image = Instance.new("ImageButton")
    Image.Name = "ToggleUiGGH"
    Image.Image = "rbxassetid://17439034945"
    Image.BackgroundTransparency = 1
    Image.Size = UDim2.new(0, 50, 0, 50)
    Image.Position = UDim2.new(0, 10, 0.5, -25)
    Image.Draggable = true
    Image.Parent = ToggleUiGGH

    Image.MouseButton1Click:Connect(function()
        Window:Minimize()
    end)
end

do
    local gui = Instance.new("ScreenGui")
    gui.Parent = LocalPlayer:WaitForChild("PlayerGui")

    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 200, 0, 50)
    frame.Position = UDim2.new(0, 10, 0, 10)
    frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    frame.BorderSizePixel = 0
    frame.Parent = gui

    local gradient = Instance.new("UIGradient")
    gradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(100, 50, 200)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(50, 150, 255))
    })
    gradient.Parent = frame

    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 1, 0)
    label.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    label.BorderSizePixel = 0
    label.Font = Enum.Font.Unknown
    label.Text = "Holding Item: 0"
    label.TextColor3 = Color3.fromRGB(255, 255, 255)
    label.TextScaled = true
    label.Parent = frame

    local gradient2 = Instance.new("UIGradient")
    gradient2.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 100, 100)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(100, 255, 100))
    })
    gradient2.Parent = label

    _G.HoldingItem = label

    LocalPlayer.Character.ChildAdded:Connect(function(child)
        if child:IsA("Tool") then
            wait(0.1)
            if child:FindFirstChild("Items") then
                label.Text = "Holding Item: " .. tostring(child.Items.Value)
            end
        end
    end)

    LocalPlayer.Backpack.ChildAdded:Connect(function(child)
        if child:IsA("Tool") then
            label.Text = "Hold item to see: None"
        end
    end)

    LocalPlayer.Backpack.ChildRemoved:Connect(function()
        label.Text = "0"
    end)
end

task.spawn(function()
    while wait(0.5) do
        if AutoBuy_Toggle.Value and Mode_Selection.Value == "Buyer" then
            local stands = {}
            for _, v in ipairs(Workspace.Dropped:GetChildren()) do
                if v:FindFirstChild("Stand") and v.Stand:FindFirstChild("Sign") and v.Stand.Sign:FindFirstChild("SurfaceGui") then
                    local name = v.Stand.Sign.SurfaceGui.ItemName.Text
                    if name:lower():match(Item_Name.Value:lower()) then
                        table.insert(stands, v.Stand.Buy.Prompt)
                    end
                end
            end

            for _, prompt in ipairs(stands) do
                if prompt:IsA("ProximityPrompt") then
                    fireproximityprompt(prompt)
                    task.wait(0.1)
                end
            end
        end
    end
end)
