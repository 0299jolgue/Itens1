local itensAdicionados = {}
local encontrouItens = false

for _, obj in ipairs(workspace:GetDescendants()) do
    if obj:IsA("Tool") and not itensAdicionados[obj.Name] then
        print("Tool encontrada:", obj.Name)
        encontrouItens = true
        itensAdicionados[obj.Name] = true

        local btn = criarBotao(obj.Name, ItemsTab, function()
            pegarItem(obj.Name)
        end)
        btn.Size = UDim2.new(1, 0, 0, 35)
        btn.Parent = ItemsTab
    end
end

if not encontrouItens then
    print("Nenhuma Tool encontrada no workspace!")
end
