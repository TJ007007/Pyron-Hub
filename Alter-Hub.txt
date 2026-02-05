loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Hub/main/LoadingScreen.lua"))()
--load the lib

    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Hub/main/GUI"))()

    local Window = Library:Window("Alter-Hub")

    local AlterHub = Window:Server("Alter-Hub","https://raw.githubusercontent.com/AlterX404/Alter-Hub/main/channels4_profile.jpg")



--Credits

    local CreditsSection = AlterHub:Channel("Credits")

    CreditsSection:Label("Main Dev And Owner")

    CreditsSection:Button("Alter-X (click to visit my YouTube)", function()

        setclipboard("https://www.youtube.com/channel/UCBTkrkGEibTUayqVvs8G5fg")

        Library:Notification("Copied", "The link has been copied. Go and paste it in your browser.", "Okay!")

    end)



    CreditsSection:Label("Helper")



    CreditsSection:Button("Chat GPT(still click to visit my YouTube)", function()

        setclipboard("https://www.youtube.com/channel/UCBTkrkGEibTUayqVvs8G5fg")

        Library:Notification("Copied", "The link has been copied. Go and paste it in your browser.", "Okay!")

    end)





-- Universal Scripts 

    local UniversalSection = AlterHub:Channel("Universal Scripts")

    UniversalSection:Label("Offical Alter Troll Hub And Scripts")



    --Alter Troll Hub

        UniversalSection:Button("Alter Troll Hub", function()



            local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

            local Window = Library.CreateLib("Alter Hub troll script (Beta)", "BloodTheme")



            --credits

            local Tab = Window:NewTab("Credits")

            local CreditsSection = Tab:NewSection("Credits")

            CreditsSection:NewButton("Alter-X (click to visit my YouTube)", "click to copy it and paste it in your browser", function()

                setclipboard("https://www.youtube.com/channel/UCBTkrkGEibTUayqVvs8G5fg")

            end)

            CreditsSection:NewLabel("Helper")



            CreditsSection:NewButton("Chat GPT(still click to visit my YouTube)", "click to copy it and paste it in your browser", function()

                setclipboard("https://www.youtube.com/channel/UCBTkrkGEibTUayqVvs8G5fg")

            end)

            --main

            local Tab = Window:NewTab("Main Scripts")

            local Section = Tab:NewSection("Functions")

            --ALTER FE

            Section:NewButton("Alter-FE", "FE SCRIPT", function()

                loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/fe-script-for-roblox/main/Alter%20Hub%20Fe"))()

            end)
            Section:NewButton("Fling Yourself", "Flings you", function()

                local core
                if typeof(gethui) == 'function' then
                    core = gethui()
                end
                if typeof(core) ~= 'Instance' then
                    core = game:GetService("CoreGui")
                end

                local flingGui = select(2, pcall(function()
                    return game:GetObjects("rbxassetid://10171585012")[1]:Clone()
                end))

                if typeof(flingGui) == 'Instance' and flingGui:IsA("ScreenGui") then
                    flingGui.Parent = core

                    local players = game:GetService("Players")
                    local run = game:GetService("RunService")
                    local localplayer = players.LocalPlayer

                    local power = 15e3
                    local fling_active = {}

                    local frame = flingGui:WaitForChild("Frame")
                    local listedFrame = frame:WaitForChild("Frame")
                    local closeButton = frame:WaitForChild("CloseButton")
                    local flingButton = listedFrame:WaitForChild("Fling")

                    closeButton.MouseButton1Up:Connect(function()
                        return flingGui:Destroy()
                    end)

                    flingButton.MouseButton1Up:Connect(function()
                        local character = localplayer.Character

                        if typeof(fling_active[character]) == 'Instance' then
                            return
                        end

                        local head = character:FindFirstChild("Head")
                        local torso = character:FindFirstChild("Torso")
                        local lleg = character:FindFirstChild("Left Leg")
                        local rleg = character:FindFirstChild("Right Leg")

                        local uppertorso = character:FindFirstChild("UpperTorso")
                        local lowertorso = character:FindFirstChild("LowerTorso")

                        local rootpart = character:FindFirstChild("HumanoidRootPart")
                        local humanoid = character:FindFirstChildWhichIsA("Humanoid")
                        local content = {head, torso, lleg, rleg, uppertorso, lowertorso}

                        local connections = {}
                        if typeof(getconnections) == 'function' then
                            for _, part in pairs(content) do
                                for _, connection in pairs(getconnections(part:GetPropertyChangedSignal("CanCollide"))) do
                                    pcall(connection.Disable, connection)
                                end
                                for _, connection in pairs(getconnections(part.Changed)) do
                                    pcall(connection.Disable, connection)
                                end
                            end
                            connections = {
                                table.unpack(getconnections(game.DescendantAdded)),
                                table.unpack(getconnections(workspace.DescendantAdded)),
                                table.unpack(getconnections(character.DescendantAdded)),
                                typeof(rootpart) == 'Instance' and table.unpack(getconnections(rootpart.ChildAdded)),
                                typeof(humanoid) == 'Instance' and table.unpack(getconnections(humanoid:GetPropertyChangedSignal("WalkSpeed"))),
                                typeof(humanoid) == 'Instance' and table.unpack(getconnections(humanoid.Changed))
                            }
                        end
                        for _, connection in pairs(connections) do
                            pcall(connection.Disable, connection)
                        end
                        local connection; connection = run.Stepped:Connect(function()
                            for _, part in pairs(content) do
                                part.CanCollide = false
                            end
                            humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, false)
                        end)

                        task.wait(0.1)

                        local thrust = Instance.new("BodyThrust")
                        thrust.Force = Vector3.new(power, 0, power)
                        thrust.Location = rootpart.Position
                        thrust.Parent = rootpart
                        humanoid.WalkSpeed = 50
                        for _, connection in pairs(connections) do
                            pcall(connection.Enable, connection)
                        end
                    end)
                end

            end)

            Section:NewButton("Hair eater", "eat your hairs/hats", function()

                loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Troll-Hub/main/hair%20eater"))()

            end)



            Section:NewButton("Alter Hub Invisible (For PC)(Key B)", "Toggle press key B to invis/vis", function()

                loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Troll-Hub/main/pc%20invis"))()

            end)



            Section:NewButton("Alter Hub Invisible (For Mobile)", "makes u invis", function()

                loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Troll-Hub/main/mobile%20invis"))()

            end)

            Section:NewButton("Blink (Key z)", "Invisible blink", function()

				loadstring(game:HttpGet('https://pastebin.com/raw/4pc5Wx9E'))([[ Blink Script ]])

			end)



            Section:NewButton("Sound annoyer", "This will make some sound ppl hear it", function()

                --// Doesn't work if RespectFilteringEnabled is enabled

                print(game:GetService("SoundService").RespectFilteringEnabled)

    

                --// Get's every sound instance in workspace and play's it (Earrape btw)

                for _, sound in next, workspace:GetDescendants() do

                if sound:IsA("Sound") then

                    sound:Play()

                end

                end

                end)

                Section:NewButton("Admin (infinite yield)", "EE", function()

                loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()

                end)

            -- script

            local Tab = Window:NewTab("Other Scripts")

            local Section = Tab:NewSection("Functions")

            Section:NewButton("Kill script (need to be close/near the players)", "need to be close/near the players", function()

            loadstring(game:HttpGet("https://pastebin.com/raw/v8PX741z"))()

            end)

           

        

 --other in uni scripts


    UniversalSection:Button("Alter Hub Invisible (For PC)(Key E)[Run again after death]", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Hub/main/Alter-invis.lua"))()
    end)

    UniversalSection:Button("Alter Hub Invisible (For Mobile)", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Troll-Hub/main/mobile%20invis"))()

    end)



    UniversalSection:Seperator()

    UniversalSection:Label("Alter Hub RTX")  

    UniversalSection:Button("Alter Hub Offical RTX", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterX404/Alter-Troll-Hub/main/Alter%20Hub%20RTX"))()

    end)
    end)

    UniversalSection:Seperator()

 -- local player

        local walkspeedSlider

        local jumpHeightSlider

        local infiniteJumpEnabled = false

        local jumpRequestConnection

        local function setWalkSpeed(value)

            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value

        end

        local function setJumpHeight(value)

            game.Players.LocalPlayer.Character.Humanoid.JumpHeight = value

        end

        walkspeedSlider = UniversalSection:Slider("Walkspeed (may not work for some games)", 16, 500, 16, function(value)

            setWalkSpeed(value)

        end)

        UniversalSection:Button("Reset WalkSpeed", function()

            local defaultValue = 16

            walkspeedSlider:Change(defaultValue)

            setWalkSpeed(defaultValue)

        end)

        jumpHeightSlider = UniversalSection:Slider("JumpHeight (may not work for some games)", 16, 350, 16, function(value)

            setJumpHeight(value)

        end)

        UniversalSection:Button("Reset JumpHeight", function()

            local defaultValue = 16

            jumpHeightSlider:Change(defaultValue)

            setJumpHeight(defaultValue)

        end)

        game:GetService("UserInputService").InputChanged:Connect(function(input)

            if input.UserInputType == Enum.UserInputType.MouseMovement then

                -- Update WalkSpeed and JumpHeight continuously while dragging the slider

                setWalkSpeed(walkspeedSlider:GetValue())

                setJumpHeight(jumpHeightSlider:GetValue())

            end

        end)

        UniversalSection:Toggle("Inf Jump (may not work for some games)", false, function(enabled)

            infiniteJumpEnabled = enabled

    

            if infiniteJumpEnabled then

                jumpRequestConnection = game:GetService("UserInputService").JumpRequest:Connect(function()

                    game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")

                end)

            else

                if jumpRequestConnection then

                    jumpRequestConnection:Disconnect()

                    jumpRequestConnection = nil

                end

            end

        end)

 --uni scripts

        UniversalSection:Seperator() 

        UniversalSection:Label("Scripts")  

        UniversalSection:Seperator() 
 
        UniversalSection:Button("Rejoin", function()

            repeat
                wait()  
            until game:IsLoaded() 
            game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId,game.JobId) 
    
        end)
        UniversalSection:Button("Flight", function()

            loadstring("\108\111\97\100\115\116\114\105\110\103\40\103\97\109\101\58\72\116\116\112\71\101\116\40\40\39\104\116\116\112\115\58\47\47\103\105\115\116\46\103\105\116\104\117\98\117\115\101\114\99\111\110\116\101\110\116\46\99\111\109\47\109\101\111\122\111\110\101\89\84\47\98\102\48\51\55\100\102\102\57\102\48\97\55\48\48\49\55\51\48\52\100\100\100\54\55\102\100\99\100\51\55\48\47\114\97\119\47\101\49\52\101\55\52\102\52\50\53\98\48\54\48\100\102\53\50\51\51\52\51\99\102\51\48\98\55\56\55\48\55\52\101\98\51\99\53\100\50\47\97\114\99\101\117\115\37\50\53\50\48\120\37\50\53\50\48\102\108\121\37\50\53\50\48\50\37\50\53\50\48\111\98\102\108\117\99\97\116\111\114\39\41\44\116\114\117\101\41\41\40\41\10\10")()

        end)

        UniversalSection:Seperator()

        UniversalSection:Button("Troll Face", function()

            loadstring(game:HttpGet("https://pastebin.com/raw/saMtiek2", true))()

        end)

        UniversalSection:Seperator()

        UniversalSection:Button("Infinity Yield", function()

            loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()

        end)

        UniversalSection:Seperator()

        UniversalSection:Button("Dark Dex V5", function()

            local file = "dexV4.lua" -- cache file name (workspace folder)

            local url = "https://raw.githubusercontent.com/loglizzy/dexV4/main/source.lua"

            

            local raw = isfile and isfile(file) and readfile(file)

            raw = raw or game:HttpGet(url)

            

            if isfile then

                task.spawn(writefile, file, game:HttpGet(url))

            end

            

            loadstring(raw)()

        end)

        UniversalSection:Seperator() 

        UniversalSection:Button("Dark Dex(MOBILE)", function()

            loadstring(game:GetObjects("rbxassetid://418957341")[1].Source)()   

        end)

        UniversalSection:Seperator() 

        UniversalSection:Button("Simple Spy", function()

            loadstring(game:HttpGet('https://raw.githubusercontent.com/exxtremestuffs/SimpleSpySource/master/SimpleSpy.lua'))()

        end)

        UniversalSection:Seperator() 

        UniversalSection:Label("Script Hubs")  

        UniversalSection:Seperator() 

        UniversalSection:Button("Owl Hub(ESP/Aim Bot)", function()

            loadstring(game:HttpGet("https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt"))();

        end)

        UniversalSection:Seperator() 

        UniversalSection:Button("NukeVsCity Hub", function()

            loadstring(game:HttpGet("https://raw.githubusercontent.com/NukeVsCity/TheALLHACKLoader/main/NukeLoader"))()

        end)

        



--Project_Slayers

    local Project_SlayersSection = AlterHub:Channel("Project Slayers")

    Project_SlayersSection:Seperator()

    Project_SlayersSection:Label("Stat Boosters")



    local isRengukoMode = false

        Project_SlayersSection:Toggle("Renguko Mode(Set Your Heart Ablaze)", false, function(enabled)



        isRengukoMode = enabled

        -- Check if auto buy is enabled

         if enabled then

            RengukoMode()

         else 

            local args = {

                [1] = false

            }



            game:GetService("ReplicatedStorage").Remotes.heart_ablaze_mode_remote:FireServer(unpack(args))

        end

    end)

        

    function RengukoMode()

    local args = {

            [1] = true

        }



        game:GetService("ReplicatedStorage").Remotes.heart_ablaze_mode_remote:FireServer(unpack(args))

    end

    



    local isThunderMode = false

        Project_SlayersSection:Toggle("Thunder Mode", false, function(enabled)



        isThunderMode = enabled

        -- Check if auto buy is enabled

         if enabled then

            ThunderMode()

         else 



            local args = {

                [1] = false

            }



            game:GetService("ReplicatedStorage").Remotes.thundertang123:FireServer(unpack(args))



        end

    end)

        

    function ThunderMode()

        local args = {

            [1] = true

        }

    

        game:GetService("ReplicatedStorage").Remotes.thundertang123:FireServer(unpack(args))

    end

    local isInfStamina = false



    Project_SlayersSection:Button("InfStamina", function()
        
        local old

        old = hookfunction(getrenv()._G.Stamina, function(self, ...)

           local args = {...}

           if typeof(args[1]) == "number" then

               args[1] = 0

           end

           return old(self, unpack(args))

        end)
    end)
        

        











    local isAutoBuyEnabled = false -- Variable to track the toggle state



    Project_SlayersSection:Label("Auto Buy")

    Project_SlayersSection:Toggle("Auto Buy (Stand Infront of Item You Want To Buy)", false, function(enabled)

        isAutoBuyEnabled = enabled -- Update the toggle state

    

        -- Check if auto buy is enabled

        if enabled then

            AutoBuy()

        end

    end)

    

    -- Function to perform auto buy

    function AutoBuy()

        local vim = game:GetService('VirtualInputManager')

    

        while isAutoBuyEnabled do

            vim:SendKeyEvent(true, Enum.KeyCode.E, false, game)

            wait() -- Wait for a short period before releasing the key

            vim:SendKeyEvent(false, Enum.KeyCode.E, false, game)

            wait() -- Wait before sending the key press again

        end

    end

    

    





    Project_SlayersSection:Seperator()

    Project_SlayersSection:Label("Scripts")



    

    Project_SlayersSection:Button("Nuke HUB", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/NukeVsCity/Scripts2023/main/projslayerthingy"))()

    end)

    Project_SlayersSection:Seperator()



    Project_SlayersSection:Button("SYLVEON HUB", function()

        local LoaderUrl = "https://raw.githubusercontent.com/ogamertv12/SylveonHub/main/Mobile.lua"

        repeat wait() until game:IsLoaded()

        loadstring(game:HttpGet(LoaderUrl))()

    end)

    Project_SlayersSection:Seperator()

    Project_SlayersSection:Button("PROJECT SLAYERS (VG)", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/1201for/V.G-Hub/main/V.Ghub'))()



    end)

    Project_SlayersSection:Seperator()

    Project_SlayersSection:Button("Lead Hub", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/LeadMarker/Scripts/main/ProjectSlayer.lua"))()

    end)

    Project_SlayersSection:Seperator()

    Project_SlayersSection:Button("Carly Hub (Invis Script)", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/lmmake/fun/main/projectslayer.lua"))()

    end)

    Project_SlayersSection:Seperator()

    Project_SlayersSection:Button("Oni Hub", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/Kaa4801/OniHubV3/main/OniHubV2.txt"))()

    end)

    Project_SlayersSection:Seperator()





--Blox_Fruits

    local Blox_FruitsSection = AlterHub:Channel("Blox Fruits")



    Blox_FruitsSection:Button("OP BF Script", function()

      loadstring(game:HttpGet('https://raw.githubusercontent.com/SHAREHACK/bloxfruit/main/free'))()

    end)

    Blox_FruitsSection:Seperator()

    Blox_FruitsSection:Button("Thunder Hub", function()

     _G.ThunderVersion = "Mobile"

     loadstring(game:HttpGet("https://raw.githubusercontent.com/ThunderZ-05/HUB/main/Script"))()

    end)

    Blox_FruitsSection:Seperator()

    Blox_FruitsSection:Button("Ho-Ho Hub", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI'))()

    end)

    Blox_FruitsSection:Seperator()



    Blox_FruitsSection:Button("Auto Farm", function()

        _G.Color = Color3.fromRGB(0, 255, 17)

     loadstring(game:HttpGet(("https://raw.githubusercontent.com/PowerxCANDYYY/BFFREE/main/POWERX.lua"), true))()

    end)

    Blox_FruitsSection:Seperator()



    Blox_FruitsSection:Button("Lunar Hub", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/Cve-Hub/LnHub/main/README.md'))()

    end)

    Blox_FruitsSection:Seperator()



    Blox_FruitsSection:Button("Maruko Hub", function()

        loadstring(game:HttpGet"https://mukuroxquartyz.xyz/Lua/script.lua")()

    end)

    Blox_FruitsSection:Seperator()



    Blox_FruitsSection:Button("Black Trap", function()

        loadstring(game:HttpGet("https://pastebin.com/raw/BdvUGb2q"))()

    end)

    Blox_FruitsSection:Seperator()



-- DOORS

    local DOORSSection = AlterHub:Channel("DOORS")

    DOORSSection:Seperator()



    DOORSSection:Button("Cherry hub", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/iCherryKardes/Doors-Hub/main/Hub%202.1"))()

    end)

    DOORSSection:Seperator()

    DOORSSection:Button("DOORS Script-2", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/scriptpastebin/raw/main/Doors"))()

    end)

    DOORSSection:Seperator()

    DOORSSection:Button("MSDOORS", function()

        loadstring(game:HttpGet(("https://raw.githubusercontent.com/mstudio45/MSDOORS/main/MSDOORS.lua"), true))()

    end)

    DOORSSection:Seperator()

    DOORSSection:Button("Project-WD", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/Muhammad6196/Project-WD/main/Mainstring.lua"))()

    end)

    DOORSSection:Seperator()

    DOORSSection:Button("POOPDOORS", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/zoophiliaphobic/POOPDOORS/main/script.lua'))()

    end)







--BROOKHEAVEN

    local BROOKHEAVENSection = AlterHub:Channel("BROOKHEAVEN")

    BROOKHEAVENSection:Seperator()

    BROOKHEAVENSection:Button("ADMIN PANEL", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()

    end)

    BROOKHEAVENSection:Seperator()

    BROOKHEAVENSection:Button("BROOKHEAVEN Script (RANDOM)", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/IceMael7/NewIceHub/main/Brookhaven'))()

    end)

    BROOKHEAVENSection:Seperator()

--shindo_life

    local shindo_lifeSection = AlterHub:Channel("Shindo life")

    shindo_lifeSection:Seperator()

    shindo_lifeSection:Button("Shindo Life Script", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/PremierHub/Data/main/code.lua"))()

    end)

    shindo_lifeSection:Seperator()



--King_Legacy

    local King_LegacySection = AlterHub:Channel("King Legacy")

    King_LegacySection:Seperator()



    King_LegacySection:Button("HO-HO HUB", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI'))()

    end)

    King_LegacySection:Seperator()

    King_LegacySection:Button("OP-KL", function()

        loadstring(game:HttpGet('https://raw.githubusercontent.com/SHAREHACK/bloxfruit/main/free'))()

    end)

    King_LegacySection:Seperator()

    King_LegacySection:Button("Muruko Hub", function()

        loadstring(game:HttpGet("https://mukuroxquartyz.xyz/Lua/script.lua"))()

    end)

    King_LegacySection:Seperator()



-- DA_HOOD

    local DA_HOODSection = AlterHub:Channel("DA HOOD")

    DA_HOODSection:Seperator()

    DA_HOODSection:Button("INF HEALTH", function()

        local Player = game.Players.LocalPlayer

        Player.Character.Humanoid.Health = math.huge

    end)

    DA_HOODSection:Seperator()

    DA_HOODSection:Button("SUPER JUMP", function()

        local Player = game.Players.LocalPlayer

        Player.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)

        Player.Character.Humanoid.JumpPower = 100

    end)

    DA_HOODSection:Seperator()

    DA_HOODSection:Button("FLY", function()

        local Player = game.Players.LocalPlayer

        Player.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)

        wait()

        Player.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Freefall)

    end)

    DA_HOODSection:Seperator()





--Arsenal

    local ArsenalSection = AlterHub:Channel("Arsenal")

    ArsenalSection:Seperator()

    ArsenalSection:Button("Aimbot", function()

        local Players = game:GetService("Players")

    

        local function Aimbot()

            for _, player in ipairs(Players:GetPlayers()) do

                if player ~= Players.LocalPlayer and player.Character and player.Character:FindFirstChild("Head") then

                    local head = player.Character.Head

                    local target = head.Position + Vector3.new(0, 1, 0)

                    

                    game:GetService("Workspace").CurrentCamera.CFrame = CFrame.new(game:GetService("Workspace").CurrentCamera.CFrame.Position, target)

                end

            end

        end

        

        while true do

            wait(0.1)

            Aimbot()

        end

    end)

    ArsenalSection:Seperator()

    ArsenalSection:Button("inf damage", function()

        local DamageValue = math.huge

    

        game:GetService("ReplicatedStorage").RemoteEvent:FireServer(DamageValue)

    end)

    ArsenalSection:Seperator()



--Flee_The_Facility

    local Flee_The_FacilitySection = AlterHub:Channel("Flee The Facility")

    Flee_The_FacilitySection:Seperator()

    Flee_The_FacilitySection:Button("Flee The Facility", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/Drifty96/ftfgui/main/ftfgui", true))()

    end)

    Flee_The_FacilitySection:Seperator()





--ASTD



    local ASTDSection = AlterHub:Channel("All Star Tower Defense")

    ASTDSection:Seperator()

    ASTDSection:Label("KeyLess")  



    ASTDSection:Button("Trap Hub", function()

        repeat task.wait() until game:IsLoaded()



        loadstring(game:HttpGet("https://raw.githubusercontent.com/TrapstarKSSKSKSKKS/Main/main/TrapHub.lua"))()-- Load Notification

    end)    

    ASTDSection:Seperator()

    ASTDSection:Label("With KeySystem")   

    ASTDSection:Button("karmapanda (WITH KEY)", function()

        repeat task.wait() until game:IsLoaded()



        loadstring(game:HttpGet('https://script.karmapanda.dev/'))()

    end)

    ASTDSection:Seperator()

--Ninja_Tycoon

    local Ninja_TycoonSection = AlterHub:Channel("Ninja Tycoon")

    Ninja_TycoonSection:Seperator()

    Ninja_TycoonSection:Button("auto steal auto collect and more", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/omokom55/FreeScripts/main/Ninja%20Tycoon", true))()

    end)

    Ninja_TycoonSection:Seperator()



    Ninja_TycoonSection:Button("Ninja Tycoon", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/omokom55/FreeScripts/main/Ninja%20Tycoon", true))()

    end)

    Ninja_TycoonSection:Seperator()



    Ninja_TycoonSection:Button("Dragon hub (KEY SYSTEM)", function()

        loadstring(game:HttpGet"https://thedragonslayer2.github.io")()

        end)

        Ninja_TycoonSection:Seperator()



--FNAF_CO-OP

    local FNAFSection = AlterHub:Channel("FNAF CO-OP")

    FNAFSection:Seperator()



    FNAFSection:Button("FNAF: Coop | Animatronic Esp, Infinite Sprint & More", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/Asphronium/FnafCo-opGUI/main/fnafCo-opGUI.lua"))()

    end)

    FNAFSection:Seperator()



--Red vs Blue Plane Wars Script

    local RVBSection = AlterHub:Channel("Red vs Blue Plane Wars Script")

    RVBSection:Seperator()



    RVBSection:Button("it works when pistol is equipped!!!!!!!!!!!!!!!!!!!!!!!!", function()

        while wait() do

            pcall(function()

                for i,v in pairs(game.Players:GetPlayers()) do

                

                    if v.Team ~= game.Players.LocalPlayer.Team and v.Character.Humanoid.Health > 0 and v.Character:FindFirstChild("ForceField") == nil then

                        local args = {

                            [1] = v.Character.Head,

                        [2] = v.Character.Head.Position

                            }

            

                    game:GetService("Players").LocalPlayer.Character.Pistol.FireNow:FireServer(unpack(args))

                    end

                end

            end)

        end

    end)

    RVBSection:Seperator()




--Anime Adventures

    local AnimeAdventuresSection = AlterHub:Channel("Anime Adventures")

    AnimeAdventuresSection:Seperator()



    AnimeAdventuresSection:Button("Anime Adventures [GUI - Full Auto Farm & More!]", function()

        loadstring(game:HttpGet("https://raw.githubusercontent.com/ArponAG/Scripts/main/AnimeAdventures.lua"))()

    end)

    AnimeAdventuresSection:Seperator()

--Pilgrammed

    local PilgrammedSection = AlterHub:Channel("Pilgrammed")


    PilgrammedSection:Seperator()
    PilgrammedSection:Button("Pilgrammed [GUI - Full Auto Farm God Mode & More!]", function()
      loadstring(game:HttpGet(('https://raw.githubusercontent.com/itsyouranya/free/main/pilgrammed.lua'),true))()
    end)



   PilgrammedSection:Seperator()
    PilgrammedSection:Button("Chest Autofarm", function()
      _G.toggle=true
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Disttt/Pilgrammed/main/77-Autochest.lua"))()
    end)
   
--UTD

    local UTDSection = AlterHub:Channel("Ultimate Tower Defence")
    
    UTDSection:Button("Auto Fish", function()
        local stuff = getrenv()._G.FireNetwork
        local id = game.Players.LocalPlayer.UserId
 
        while true do
            stuff("PlayerCatchFish", id)
            wait()
           end
      end)
    UTDSection:Seperator()
    UTDSection:Button("One More Hub (Key System)", function()
        loadstring(game:HttpGet('https://gitlab.com/wspcontr/onemorehub/-/raw/main/scriptloader.lua'))()
    end)
    
--EPT

    local EPTSection = AlterHub:Channel("Elemental Powers Tycoon")
    
    EPTSection:Button("No Cooldown (Q)", function()
        

local player = game:GetService("Players").LocalPlayer
local UIS = game:GetService("UserInputService")
local toolList = {}
_G.goGO = true

local function collideWith(button) -- Acts as another firetouchinterest
    local oldSize = button.Size
    local oldT = button.Transparency
    local oldCast = button.CastShadow
    local oldCollide = button.CanCollide

    button.CastShadow = false
    button.CanCollide = false
    button.Transparency = 1
    task.wait()
    button.Size = Vector3.new(10000, 10000, 10000)
    task.wait()
    button.Size = oldSize
    button.CastShadow = oldCast
    button.CanCollide = oldCollide
    button.Transparency = oldT
end

UIS.InputBegan:Connect(function(k)
	if k.KeyCode == Enum.KeyCode.Q then
		for i, v in pairs(player.Backpack:GetChildren()) do
			if not string.find(v.Name, "Sword") or not string.find(v.Name, "Blade") or not string.find(v.Name, "Saber") or not string.find(v.Name, "Saber") then
				local name = v.Name
				v.Parent = player.Character task.wait()
			
				local args = {[1] = game:GetService("ReplicatedStorage").Magic:FindFirstChild(v.Name, true).Parent.Name, [2] = v.Name, [3] = {["Camera"] = workspace.CurrentCamera.CFrame, ["Mouse"] = player:GetMouse().Hit.Position}}
				game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("DoMagic"):FireServer(unpack(args)) task.wait(0.1)
				
				player.Character[name].Parent = player.Backpack
			end
		end
	end
end)

while _G.goGO do task.wait(1)
	for i, v in pairs(game:GetService("Workspace").Tycoons:GetChildren()) do 
		for i, v1 in pairs(v:GetChildren()) do
			if string.find(v1.Name, "Ability") then
				collideWith(v1.Button)
			end
		end
	end
end
    end)      
    EPTSection:Seperator()
    
    EPTSection:Button("Tora Hub", function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/ToraIsMe/ToraIsMe/main/0elemental", true))()
    end)

--AFSX
    local AFSXSection = AlterHub:Channel("Anime Fighting Simulator X")

--welcome message 
    Library:Notification("Welcome", "Alter-hub GUI loaded!", "Continue")
