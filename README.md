-- Booting Library

local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

-- Values & Functions

_G.Key = "KeySystem"

_G.KeyInput = ""

_G.AdminKey = "BYADMIN"

_G.IsAdmin = false

function CorrectKey()

    OrionLib:MakeNotification({

        Name = "Key!",

        Content = "You have entered the correct key!",

        Image = "",

        Time = 4

    })

end

function CorrectAdminKey()

    OrionLib:MakeNotification({

        Name = "Admin Key!",

        Content = "You have entered the correct admin key!",

        Image = "",

        Time = 4

    })

    _G.IsAdmin = true

end

-- Creating Window

local Window = OrionLib:MakeWindow({Name = "Key System Tutorial", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest", IntroEnabled = false})

-- Tabs

local tab1 = Window:MakeTab({

    Name = "Key System",

    Icon = "",

    PremiumOnly = false

})

local tab2 = Window:MakeTab({

    Name = "Admin",

    Icon = "",

    PremiumOnly = false

})

-- Define tab1

local section1 = tab1:AddSection({

    Name = "Key"

})

local adminSection = tab2:AddSection({

    Name = "Admin Key"

})

tab1:AddTextbox({

    Name = "Enter Key",

    Default = "",

    TextDisappear = false,

    Callback = function(Value)

        _G.KeyInput = Value

    end      

})

tab1:AddButton({

    Name = "Check Key!",

    Callback = function()

        if _G.KeyInput == _G.Key then

            wait(0.5)

            CorrectKey()

        end

    end

})

tab2:AddTextbox({

    Name = "Enter Admin Key",

    Default = "",

    TextDisappear = false,

    Callback = function(Value)

        if Value == _G.AdminKey then

            wait(0.5)

            CorrectAdminKey()

        end

    end      

})

-- Define autofarm section

local autofarmSection = tab1:AddSection({

    Name = "Autofarm"

})

autofarmSection:AddToggle({

    Name = "Autofarm Enabled",

    Default = false,

    Callback = function(Value)

        if _G.IsAdmin and Value then

            print("Autofarm started!")

            -- your autofarm code here

        else

            print("You don't have permission to use this feature.")

        end

    end

})

-- Define auto island tp section

local autoIslandSection = tab1:AddSection({

    Name = "Auto Island TP"

})

autoIslandSection:AddButton({

    Name = "Teleport to Random Island",

    Callback = function()

        if _G.IsAdmin then

            print("Teleporting to random island!")

            -- your auto island tp code here

        else

            print("You don't have permission to use this feature.")

        end

    end

})

