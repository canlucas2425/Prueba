-- LocalScript dentro de StarterPlayerScripts o StarterCharacterScripts

-- Función para encontrar un jugador al azar
function getRandomPlayer()
    local players = game:GetService("Players"):GetPlayers()
    local randomPlayer = players[math.random(1, #players)]
    return randomPlayer
end

-- Función para sentarse en la cabeza del jugador
function sitOnHead(targetPlayer)
    local character = game.Players.LocalPlayer.Character
    if character and targetPlayer.Character then
        local head = targetPlayer.Character:FindFirstChild("Head")
        if head then
            -- Asegúrate de que el personaje esté sentado
            local humanoid = character:FindFirstChildOfClass("Humanoid")
            if humanoid then
                -- Puedes ajustar la posición para que esté justo en la cabeza
                character:SetPrimaryPartCFrame(head.CFrame * CFrame.new(0, 3, 0)) -- Ajusta '3' según sea necesario
                humanoid.Sit = true
            end
        end
    end
end

-- Función para enviar el mensaje "zamu" tres veces
function sayZamu()
    for i = 1, 3 do
        game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("SayMessageRequest"):FireServer("zamu", "All")
        wait(1) -- Espera 1 segundo entre los mensajes
    end
end

-- Código principal
local randomPlayer = getRandom
