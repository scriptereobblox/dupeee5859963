-- Put this in a LocalScript inside StarterPlayerScripts
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Assuming your tools are stored in ReplicatedStorage.Tools
local toolsFolder = ReplicatedStorage:WaitForChild("Tools")

UserInputService.InputBegan:Connect(function(input, isProcessed)
	if isProcessed then return end
	
	if input.KeyCode == Enum.KeyCode.E then
		local tool = character:FindFirstChildOfClass("Tool")
		if tool then
			local clone = tool:Clone()
			clone.Parent = player.Backpack
		end
	end
end)
