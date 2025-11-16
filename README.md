local cfg = require(game.ReplicatedStorage.HitboxConfig) -- mesmo ModuleScript de antes

local openBtn = script.Parent.OpenButton
local panel   = script.Parent.Panel
local slider  = panel.Slider
local toggle  = panel.Toggle
local close   = panel.CloseButton

local dragging = false

-- abre / fecha o painel
openBtn.MouseButton1Click:Connect(function() panel.Visible = true end)
close.MouseButton1Click:Connect(function() panel.Visible = false end)

-- slider de tamanho (funciona com toque)
slider.InputBegan:Connect(function(inp)
    if inp.UserInputType == Enum.UserInputType.Touch then dragging = true end
end)
slider.InputEnded:Connect(function() dragging = false end)

game.UserInputService.InputChanged:Connect(function(inp)
    if dragging and inp.UserInputType == Enum.UserInputType.Touch then
        local size = math.clamp((inp.Position.X - slider.AbsolutePosition.X) / slider.AbsoluteSize.X, 0.1, 2)
        cfg.Size = Vector3.new(size*4, size*4, size*4)
    end
end)

-- toggle da hitbox
toggle.MouseButton1Click:Connect(function()
    cfg.Enabled = not cfg.Enabled
    toggle.Text = cfg.Enabled and "Desativar" or "Ativar"
end)
