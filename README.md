
  _G.Farm = true
  _G.BringMob = true






	

function CheckQuest()
   local Lv =  game.Players.LocalPlayer.Data.Level.Value
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
   elseif  Lv == 1 or Lv <= 9 then
       Ms = "Bandit [Lv. 5]"
       CQ = CFrame.new(1061.15271, 16.7367725, 1548.93018, -0.836085379, -3.89774577e-08, 0.548599303, -1.17575967e-08, 1, 5.31300408e-08, -0.548599303, 3.79710414e-08, -0.836085379)
       CM = CFrame.new(1151.11829, 16.7761021, 1599.73499, -0.999999762, 0, -0.000701809535, 0, 1, 0, 0.000701809535, 0, -0.999999762)
       NQ = "BanditQuest1"
       NM = "Bandit"
       LQ = 1
end
end




function TP(P)
    NoClip = true
    Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    if Distance < 10 then
        Speed = 1000
    elseif Distance < 170 then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = P
        Speed = 350
    elseif Distance < 1000 then
        Speed = 350
    elseif Distance >= 1000 then
        Speed = 280
    end
    game:GetService("TweenService"):Create(
        game.Players.LocalPlayer.Character.HumanoidRootPart,
        TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
        {CFrame = P}
    ):Play()
    NoClip = false
end


spawn(function()

    while wait() do
        if _G.Farm then
            CheckQuest()
            if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                wait(.3)
                TP(CQ)
                wait(0.5)
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NQ,LQ)
                
            elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == Ms then
                        posmon = v.HumanoidRootPart.CFrame
                        posmon = v.HumanoidRootPart.CFrame
                        TP(v.HumanoidRootPart.CFrame * CFrame.new(0,25,0))
                        end
                    end
                end
            end    
        end
    end)

spawn(function()
    pcall(function()
        while task.wait() do
            if _G.Farm then
                if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    local Noclip = Instance.new("BodyVelocity")
                    Noclip.Name = "BodyClip"
                    Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
                    Noclip.MaxForce = Vector3.new(100000,100000,100000)
                    Noclip.Velocity = Vector3.new(0,0,0)
                end
            else
                if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
                end
            end
        end
    end)
end)



spawn(function()

    while task.wait() do
        if _G.Farm then
        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
            if v.Name == Ms then
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CanCollide = false
                sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                end
            end
        end
    end
end)


             while _G.BringMob do wait()
            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                 for i2,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == MON and v2.Name == MON then
                        v2.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                        v2.HumanoidRootPart.CanCollide = false
                           game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * Method
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                    end
                 end
            end
             end




local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
local p13 = CbFw2.activeController
local ret = p13.blades[1]
if not ret then return end
while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
return ret
end
function AttackNoCD() 
local AC = CbFw2.activeController
for i = 1, 1 do 
local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
    plr.Character,
    {plr.Character.HumanoidRootPart},
    60
)
local cac = {}
local hash = {}
for k, v in pairs(bladehit) do
    if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
        table.insert(cac, v.Parent.HumanoidRootPart)
        hash[v.Parent] = true
    end
end
bladehit = cac
if #bladehit > 0 then
    local u8 = debug.getupvalue(AC.attack, 5)
    local u9 = debug.getupvalue(AC.attack, 6)
    local u7 = debug.getupvalue(AC.attack, 4)
    local u10 = debug.getupvalue(AC.attack, 7)
    local u12 = (u8 * 798405 + u7 * 727595) % u9
    local u13 = u7 * 798405
    (function()
        u12 = (u12 * u9 + u13) % 1099511627776
        u8 = math.floor(u12 / u9)
        u7 = u12 - u8 * u9
    end)()
    u10 = u10 + 1
    debug.setupvalue(AC.attack, 5, u8)
    debug.setupvalue(AC.attack, 6, u9)
    debug.setupvalue(AC.attack, 4, u7)
    debug.setupvalue(AC.attack, 7, u10)
    pcall(function()
        for k, v in pairs(AC.animator.anims.basic) do
            v:Play()
        end                  
    end)
    if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
        game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
        game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
        game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
    end
end
end
end

require(game.ReplicatedStorage.Util.CameraShaker):Stop()
spawn(function()
while task.wait() do
pcall(function()
  if UseFast then
      if _G.F then
        AttackNoCD() 
      end
  end
end)
end
end)

local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
for i,v in pairs(getreg()) do
if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
for x,w in pairs(debug.getupvalues(v)) do
     if typeof(w) == "table" then
        task.spawn(function() 
            game:GetService("RunService").RenderStepped:Connect(function()
                if _G.F then
                    pcall(function()
                        if game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") then
                            w.activeController.increment = 3
                        else
                            w.activeController.increment = 4
                        end             
                        CameraShaker:Stop()
                        w.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                        w.activeController.attacking = false
                        w.activeController.timeToNextBlock = 0
                        w.activeController.blocking = false                            
                        w.activeController.hitboxMagnitude = 50
                        w.activeController.humanoid.AutoRotate = true
                          w.activeController.focusStart = 0
                    end)
                end
            end)
        end)
    end
end
end
end

task.spawn(function() 
while task.wait() do
if _G.F then
    pcall(function()
        wait(0.1)
        local AC = CbFw2.activeController
        for i = 1,1 do 
            local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
                plr.Character,
                {plr.Character.HumanoidRootPart},
                60
         )
local cac = {}
local hash = {}
for k, v in pairs(bladehit) do
    if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
        table.insert(cac, v.Parent.HumanoidRootPart)
        hash[v.Parent] = true
    end
end
bladehit = cac
if #bladehit > 0 then
    local u8 = debug.getupvalue(AC.attack, 5)
    local u9 = debug.getupvalue(AC.attack, 6)
    local u7 = debug.getupvalue(AC.attack, 4)
    local u10 = debug.getupvalue(AC.attack, 7)
    local u12 = (u8 * 798405 + u7 * 727595) % u9
    local u13 = u7 * 798405
    (function()
        u12 = (u12 * u9 + u13) % 1099511627776
        u8 = math.floor(u12 / u9)
        u7 = u12 - u8 * u9
    end)()
    u10 = u10 + 1
    debug.setupvalue(AC.attack, 5, u8)
    debug.setupvalue(AC.attack, 6, u9)
    debug.setupvalue(AC.attack, 4, u7)
    debug.setupvalue(AC.attack, 7, u10)
    pcall(function()
        for k, v in pairs(AC.animator.anims.basic) do
            v:Play()
        end                  
    end)
    if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
        game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
        game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
        game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
                end
            end
        end
    end)
end
end
end)

require(game.ReplicatedStorage.Util.CameraShaker):Stop()
spawn(function()
while task.wait() do
pcall(function()
  if UseFast then
      if _G.F then
        AttackNoCD() 
      end
  end
end)
end
end)
   spawn(function()
        while task.wait(0.1) do
            if _G.F then
                pcall(function()
                    local plr = game.Players.LocalPlayer

                    local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
                    local CbFw2 = CbFw[2]
                    
                    function GetCurrentBlade() 
                        local p13 = CbFw2.activeController
                        local ret = p13.blades[1]
                        if not ret then return end
                        while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
                        return ret
                    end
                    function AttackNoCD() 
                        local AC = CbFw2.activeController
                        for i = 1, 1 do 
                            local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
                                plr.Character,
                                {plr.Character.HumanoidRootPart},
                                60
                            )
                            local cac = {}
                            local hash = {}
                            for k, v in pairs(bladehit) do
                                if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                                    table.insert(cac, v.Parent.HumanoidRootPart)
                                    hash[v.Parent] = true
                                end
                            end
                            bladehit = cac
                            if #bladehit > 0 then
                                local u8 = debug.getupvalue(AC.attack, 5)
                                local u9 = debug.getupvalue(AC.attack, 6)
                                local u7 = debug.getupvalue(AC.attack, 4)
                                local u10 = debug.getupvalue(AC.attack, 7)
                                local u12 = (u8 * 798405 + u7 * 727595) % u9
                                local u13 = u7 * 798405
                                (function()
                                    u12 = (u12 * u9 + u13) % 1099511627776
                                    u8 = math.floor(u12 / u9)
                                    u7 = u12 - u8 * u9
                                end)()
                                u10 = u10 + 1
                                debug.setupvalue(AC.attack, 5, u8)
                                debug.setupvalue(AC.attack, 6, u9)
                                debug.setupvalue(AC.attack, 4, u7)
                                debug.setupvalue(AC.attack, 7, u10)
                                pcall(function()
                                    for k, v in pairs(AC.animator.anims.basic) do
                                        v:Play()
                                    end                  
                                end)
                                if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                                    game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
                                end
                            end
                        end
                    end
                    function AttackNoCD2() 
                        local AC = CbFw2.activeController
                        for i = 1, 1 do 
                            local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
                                plr.Character,
                                {plr.Character.HumanoidRootPart},
                                60
                            )
                            local cac = {}
                            local hash = {}
                            for k, v in pairs(bladehit) do
                                if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                                    table.insert(cac, v.Parent.HumanoidRootPart)
                                    hash[v.Parent] = true
                                end
                            end
                            bladehit = cac
                            if #bladehit > 0 then
                                local u8 = debug.getupvalue(AC.attack, 5)
                                local u9 = debug.getupvalue(AC.attack, 6)
                                local u7 = debug.getupvalue(AC.attack, 4)
                                local u10 = debug.getupvalue(AC.attack, 7)
                                local u12 = (u8 * 798405 + u7 * 727595) % u9
                                local u13 = u7 * 798405
                                (function()
                                    u12 = (u12 * u9 + u13) % 1099511627776
                                    u8 = math.floor(u12 / u9)
                                    u7 = u12 - u8 * u9
                                end)()
                                u10 = u10 + 1
                                debug.setupvalue(AC.attack, 5, u8)
                                debug.setupvalue(AC.attack, 6, u9)
                                debug.setupvalue(AC.attack, 4, u7)
                                debug.setupvalue(AC.attack, 7, u10)
                                pcall(function()
                                    for k, v in pairs(AC.animator.anims.basic) do
                                        v:Play()
                                    end                  
                                end)
                                if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                                    game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
                                end
                            end
                        end
                    end
                    spawn(function()
                        while wait(.5) do
                            pcall(function()
                                if _G.F then
                                    repeat wait(0.3)

                                    until not F
                                end
                            end)
                        end
                    end)
                end)
            end
        end
    end)
