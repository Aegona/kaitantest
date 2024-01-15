_G.Auto_Farm = true

    function checklevel()
    local lv = game:GetService("Players").LocalPlayer.Data.Level.Value
    if lv == 1 or lv <= 9 then
        Mon = "Bandit [Lv. 5"
        Title = "Bandit"
        QuestNumber = 1
            CFrameQuest = CFrame.new(1061.15271, 16.7367725, 1548.93018, -0.836085379, -3.89774577e-08, 0.548599303, -1.17575967e-08, 1, 5.31300408e-08, -0.548599303, 3.79710414e-08, -0.836085379)
            CFrameMon = CFrame.new(1151.11829, 16.7761021, 1599.73499, -0.999999762, 0, -0.000701809535, 0, 1, 0, 0.000701809535, 0, -0.999999762)
            --CFramePuk = CFrame.new(1101.75903, 67.6758957, 1617.50391, -0.399259984, -5.24373327e-08, -0.916837752, -1.74068084e-08, 1, -4.96134582e-08, 0.916837752, -3.84945009e-09, -0.399259984)
    end
    end

    spawn(function()
        while task.wait(.1) do
            pcall(function()
                if _G.Auto_Farm then
                checklevel()
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then

    wait(.3)
    local args = {
        [1] = "StartQuest",
        [2] = QuestName,
        [3] = QuestNumber
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
            for i,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
            if v.Name == Mon and v2.Name == Mon then
                totarget(v.HumanoidRootPart.CFrame * CFrame.new(0,1,15))
                v.HumanoidRootPart.Size = Vector3.new(60,2.5,60)
                v.HumanoidRootPart.CFrame = CFrameMon
                game:GetService'VirtualUser':CaptureController()
                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                v2.HumanoidRootPart.CanCollide = false
                sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
            end
            end
        end
                    end
                end
            end)
        end
    end)
