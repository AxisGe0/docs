### AXFW Personal Menu Configuration Documentation for FiveM Servers

#### Introduction

This documentation provides an overview and guidance for configuring the AXFW Personal Menu system within FiveM servers. The menu is an interactive in-game interface allowing players to access a variety of features. Configuration is accomplished through a Lua table with specific properties, enabling server administrators to tailor the menu to their needs.

#### Configuration Overview

The `Config` table is the core of the AXFW Personal Menu system. It defines the structure and content of the menu, with each entry representing a menu item. The configuration allows for nested items, creating a hierarchical menu structure.

#### Properties of Menu Items

Each menu item within the `Config` table can have the following properties:

- `title` (String): The label displayed for the menu item.
- `icon` (String): A FontAwesome icon class that visually represents the menu item.
- `onclick` (Function): A callback function that is executed when the menu item is selected.
- `nested` (Table): A table of nested menu items, allowing for the creation of sub-menus.
- `canaccess` (Function): Optional. A function returning a boolean value to determine if the menu item should be accessible to the current player based on custom conditions like job roles or permissions.

#### Example Configuration

Here is a simple example demonstrating how to configure a menu with several items, including nested items and access control:

```lua
Config = {
    {
        title = 'Character',
        icon = 'fas fa-user-circle',
        nested = {
            {
                title = 'Inventory',
                icon = 'fas fa-backpack',
                nested = {
                    { 
                        title = 'Weapons', 
                        icon = 'fas fa-sword', 
                        onclick = function() 
                            print('Weapons Inventory') 
                        end 
                    },
                    { 
                        title = 'Armor', 
                        icon = 'fas fa-shield-alt', 
                        onclick = function() 
                            print('Armor Inventory') 
                        end 
                    },
                }
            },
            -- Additional character-related items...
        },
        canaccess = function()
            return IsPlayerAbleToAccessCharacterMenu()
        end
    },
    -- Additional top-level items...
}
```

In the above example, the `canaccess` function `IsPlayerAbleToAccessCharacterMenu` would contain the logic to determine whether the player has access to the 'Character' menu, such as checking the player's job or role.
#### Job-Based Access Configuration

The `canaccess` function is key to job-based access control. It should return `true` if the player's job matches the required job for the menu item and `false` otherwise.

#### Example Configuration with Job Check

Below is an example configuration for a 'Police Actions' menu item that is only accessible to players with the 'police' job:

#### **QBCore**
```lua
Config = {
    {
        title = 'Police Actions',
        icon = 'fas fa-shield-alt',
        nested = {
            {
                title = 'Check ID',
                icon = 'fas fa-id-card',
                onclick = function()
                    -- Logic to check ID
                end
            },
            {
                title = 'Search Citizen',
                icon = 'fas fa-search',
                onclick = function()
                    -- Logic to search a citizen
                end
            },
            -- Additional police-specific actions...
        },
        canaccess = function()
            local PlayerData = exports['qb-core']:GetPlayerData() -- QBCore example; replace with ESX or other framework as needed
            return PlayerData.job and PlayerData.job.name == 'police'
        end
    },
    -- Additional top-level menu items...
}
```
#### **ESX**
```lua
Config = {
    {
        title = 'Police Actions',
        icon = 'fas fa-shield-alt',
        nested = {
            {
                title = 'Check ID',
                icon = 'fas fa-id-card',
                onclick = function()
                    -- Add logic to check ID here
                end
            },
            {
                title = 'Search Citizen',
                icon = 'fas fa-search',
                onclick = function()
                    -- Add logic to search a citizen here
                end
            },
            -- More police-specific actions can be added here
        },
        canaccess = function()
            local playerData = ESX.GetPlayerData()
            return playerData.job and playerData.job.name == 'police'
        end
    },
    -- Other top-level menu items...
}
```

### Expanded Emote Menu Configuration Documentation

#### Introduction

This details the process of expanding the emote options available to players through the AXFW Personal Menu in a FiveM server. It allows players to use the `ExecuteCommand` function to express themselves with in-game emotes via a user-friendly menu interface.

#### Sample Emote Menu Configuration

Here's an expanded configuration for the emote menu, featuring a variety of options:

```lua
{
    title = 'Emotes',
    icon = 'fas fa-theater-masks',
    nested = {
        {
            title = 'Wave',
            icon = 'fas fa-hand-wave',
            onclick = function()
                ExecuteCommand('e wave')
            end
        },
        {
            title = 'Salute',
            icon = 'fas fa-hand-sparkles',
            onclick = function()
                ExecuteCommand('e salute')
            end
        },
        {
            title = 'Dance',
            icon = 'fas fa-dance',
            onclick = function()
                ExecuteCommand('e dance')
            end
        },
        {
            title = 'Clap',
            icon = 'fas fa-clapping-hands',
            onclick = function()
                ExecuteCommand('e slowclap')
            end
        },
        {
            title = 'Sit',
            icon = 'fas fa-chair',
            onclick = function()
                ExecuteCommand('e sit')
            end
        },
        {
            title = 'Lean',
            icon = 'fas fa-leanpub',
            onclick = function()
                ExecuteCommand('e lean')
            end
        },
        {
            title = 'Cheer',
            icon = 'fas fa-hands-cheering',
            onclick = function()
                ExecuteCommand('e cheer')
            end
        },
        {
            title = 'Laugh',
            icon = 'fas fa-face-laugh',
            onclick = function()
                ExecuteCommand('e laugh')
            end
        },
        {
            title = 'Drink',
            icon = 'fas fa-glass-whiskey',
            onclick = function()
                ExecuteCommand('e drink')
            end
        },
        {
            title = 'Facepalm',
            icon = 'fas fa-hand-over-face',
            onclick = function()
                ExecuteCommand('e facepalm')
            end
        },
        -- Additional emote items can be added below:
        {
            title = 'Think',
            icon = 'fas fa-think',
            onclick = function()
                ExecuteCommand('e think')
            end
        },
        {
            title = 'Laugh',
            icon = 'fas fa-laugh-beam',
            onclick = function()
                ExecuteCommand('e laugh2')
            end
        },
        {
            title = 'Photography',
            icon = 'fas fa-camera',
            onclick = function()
                ExecuteCommand('e photo')
            end
        },
        {
            title = 'Notes',
            icon = 'fas fa-clipboard-list',
            onclick = function()
                ExecuteCommand('e notes')
            end
        },
        {
            title = 'Chill',
            icon = 'fas fa-smile-beam',
            onclick = function()
                ExecuteCommand('e chill')
            end
        },
        {
            title = 'Highfive',
            icon = 'fas fa-hands',
            onclick = function()
                ExecuteCommand('e highfive')
            end
        },
        {
            title = 'Shrug',
            icon = 'fas fa-shoulder-shrug',
            onclick = function()
                ExecuteCommand('e shrug')
            end
        },
        {
            title = 'Surrender',
            icon = 'fas fa-white-flag',
            onclick = function()
                ExecuteCommand('e surrender')
            end
        },
        {
            title = 'Facepalm2',
            icon = 'fas fa-facepalm',
            onclick = function()
                ExecuteCommand('e facepalm2')
            end
        },
        {
            title = 'Yoga',
            icon = 'fas fa-peace',
            onclick = function()
                ExecuteCommand('e yoga')
            end
        }
        -- Ensure all emote command strings match those defined within your server's emote script.
    }
},
```