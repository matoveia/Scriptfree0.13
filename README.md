local player = game.Players.LocalPlayer  
local char = player.Character or player.CharacterAdded:Wait()  
local noclipAtivo = false  

-- Função para ativar ou desativar o NoClip  
local function toggleNoClip()  
    noclipAtivo = not noclipAtivo  

    while noclipAtivo do  
        task.wait()  -- Pequena pausa para evitar lag  
        if char then  
            for _, part in pairs(char:GetDescendants()) do  
                if part:IsA("BasePart") and part.CanCollide then  
                    part.CanCollide = false  -- Desativa colisão  
                end  
            end  
        end  
    end  

    -- Quando desligado, reativa a colisão  
    if char then  
        for _, part in pairs(char:GetDescendants()) do  
            if part:IsA("BasePart") then  
                part.CanCollide = true  
            end  
        end  
    end  
end  

-- Conectar o botão à função de NoClip  
script.Parent.Frame.NoClipButton.MouseButton1Click:Connect(toggleNoClip)
