local Tool = script.Parent
local Handle = Tool:WaitForChild("Handle")

-- Damage variable
local DAMAGE_AMOUNT = 10

-- Function to handle when the sword is activated (clicked)
local function onActivated()
    local player = game.Players:GetPlayerFromCharacter(Tool.Parent)
    if player then
        -- Raycasting to detect hit
        local mouse = player:GetMouse()
        local target = mouse.Target
        
        if target and target:IsA("Model") then
            local character = target
            
            -- Check for humanoid to deal damage
            local humanoid = character:FindFirstChildOfClass("Humanoid")
            if humanoid then
                humanoid:TakeDamage(DAMAGE_AMOUNT) -- Inflict damage on the target
                print(player.Name .. " dealt " .. DAMAGE_AMOUNT .. " damage to " .. humanoid.Parent.Name)
            end
        end
    end
end

-- Connect the function to the Activated event of the Tool
Tool.Activated:Connect(onActivated)

