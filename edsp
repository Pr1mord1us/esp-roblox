local SCesp_settings = { ---- table for esp settings 
    textsize = 12,
    colour = 255,255,255
}

local SCgui = Instance.new("BillboardGui")
local SCesp = Instance.new("TextLabel",SCgui) ---- new instances to make the billboard gui and the textlabel


SCgui.Name = "SimpChad esp"; ---- properties of the esp
SCgui.ResetOnSpawn = false
SCgui.AlwaysOnTop = true;
SCgui.LightInfluence = 0;
SCgui.Size = UDim2.new(2, 0, 2, 0);
SCesp.BackgroundColor3 = Color3.fromRGB(255, 255, 255);
SCesp.Text = ""
SCesp.Size = UDim2.new(0.0001, 0.00001, 0.0001, 0.00001);
SCesp.BorderSizePixel = 5;
SCesp.BorderColor3 = Color3.new(SCesp_settings.colour)
SCesp.BorderSizePixel = 0
SCesp.Font = "GothamSemibold"
SCesp.TextSize = SCesp_settings.textsize
SCesp.TextColor3 = Color3.fromRGB(SCesp_settings.colour) -- text colour

game:GetService("RunService").RenderStepped:Connect(function() ---- loops faster than a while loop :)
    for i,v in pairs (game:GetService("Players"):GetPlayers()) do
        if v ~= game:GetService("Players").LocalPlayer and v.Character.Head:FindFirstChild("SimpChad esp")==nil  then -- craeting checks for team check, local player etc
            SCesp.Text = ""..v.Name..""
            SCgui:Clone().Parent = v.Character.Head
    end
end
end)

local dwEntities = game:GetService("Players")
local dwLocalPlayer = dwEntities.LocalPlayer 
local dwRunService = game:GetService("RunService")

local settings_tbl = {
    ESP_Enabled = true,
    ESP_TeamCheck = false,
    Chams = true,
    Chams_Color = Color3.fromRGB(255,255,255),
    Chams_Transparency = 0.5,
    Chams_Glow_Color = Color3.fromRGB(255,255,255)
}

function destroy_chams(char)

    for k,v in next, char:GetChildren() do 

        if v:IsA("BasePart") and v.Transparency ~= 0.5 then

            if v:FindFirstChild("Glow") and 
            v:FindFirstChild("Chams") then

                v.Glow:Destroy()
                v.Chams:Destroy() 

            end 

        end 

    end 

end

dwRunService.Heartbeat:Connect(function()

    if settings_tbl.ESP_Enabled then

        for k,v in next, dwEntities:GetPlayers() do 

            if v ~= dwLocalPlayer then

                if v.Character and
                v.Character:FindFirstChild("HumanoidRootPart") and 
                v.Character:FindFirstChild("Humanoid") and 
                v.Character:FindFirstChild("Humanoid").Health ~= 0 then

                    if settings_tbl.ESP_TeamCheck == false then

                        local char = v.Character 

                        for k,b in next, char:GetChildren() do 

                            if b:IsA("BasePart") and 
                            b.Transparency ~= 0.5 then
                                
                                if settings_tbl.Chams then

                                    if not b:FindFirstChild("Glow") and
                                    not b:FindFirstChild("Chams") then

                                        local chams_box = Instance.new("BoxHandleAdornment", b)
                                        chams_box.Name = "Chams"
                                        chams_box.AlwaysOnTop = true 
                                        chams_box.ZIndex = 4 
                                        chams_box.Adornee = b 
                                        chams_box.Color3 = settings_tbl.Chams_Color
                                        chams_box.Transparency = settings_tbl.Chams_Transparency
                                        chams_box.Size = b.Size + Vector3.new(0.02, 0.02, 0.02)

                                        local glow_box = Instance.new("BoxHandleAdornment", b)
                                        glow_box.Name = "Glow"
                                        glow_box.AlwaysOnTop = false 
                                        glow_box.ZIndex = 3 
                                        glow_box.Adornee = b 
                                        glow_box.Color3 = settings_tbl.Chams_Glow_Color
                                        glow_box.Size = chams_box.Size + Vector3.new(0.13, 0.13, 0.13)

                                    end

                                else

                                    destroy_chams(char)

                                end
                            
                            end

                        end

                    else

                        if v.Team == dwLocalPlayer.Team then
                            destroy_chams(v.Character)
                        end

                    end

                else

                    destroy_chams(v.Character)

                end

            end

        end

    else 

        for k,v in next, dwEntities:GetPlayers() do 

            if v ~= dwLocalPlayer and 
            v.Character and 
            v.Character:FindFirstChild("HumanoidRootPart") and 
            v.Character:FindFirstChild("Humanoid") and 
            v.Character:FindFirstChild("Humanoid").Health ~= 0 then
                
                destroy_chams(v.Character)

            end

        end

    end

end)
