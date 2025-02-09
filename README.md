# SmUtility
Proxy Server | Velocity Utility plugin

[![CodeFactor](https://www.codefactor.io/repository/github/smuddgge/smutility/badge)](https://www.codefactor.io/repository/github/smuddgge/smutility)

## Links
Main Github Page: https://github.com/smuddgge/SmUtility

## Commands

| Default Command       | Default Permission                           | Usage                                           |
|-----------------------|----------------------------------------------|-------------------------------------------------|
| `/alert <message>`    | `smutility.alert`                            | Sends a message to everyone on the servers      |
| `/sc` | `smutility.staffChat`                        | Toggles the staff chat                          |
| `/sc <message>`       | `smutility.staffChat`                        | Sends a message to players with the permission  |
| `/find <player name>` | `smutility.find`                             | Used to find a player on the servers            |                  
| `/list` | `smutility.list`                             | List of players on the servers                  |
| `/smutilityreload` | `smutility.reload`                           | Used to reload the commands and messages        |
| `/report <message>` | `smutility.report.use` `smutility.report.see` | Used to report somthing to staff                |
| `/send <from> <to>` | `smutility.send` | Used to teleport players to a server            |
| `/servers` | `smutility.servers` | Used to see how many players are on the servers |
| `/history <player name>` | `smutility.history` | Used to see what servers a player has been on   |

## Configuration

Commands.yml
```yaml
# -----------------------------------------
# Thank you for downloading this plugin! <3
#
# Author : Smudge
# -----------------------------------------

# 1.19 chat doesn't let velocity cancel messages being sent, there for the toggle
# for chats cannot be used. To disable the chat toggle set this to true
1.19 chat: true

alert:

  # The commands name /alert
  name: 'alert'

  # A list of other names for the command
  # This can be put for all commands
  aliases: ['broadcast']

  # The permission for using the command
  # smutility.alert
  permission: 'alert'

  # {prefix} - The prefix set in message.yml
  # {message} - The message sent
  message: '&8&l[&f&lAlert&8&l] &a{message}'

find:
  name: 'find'
  permission: 'find'
  message: '{prefix} &f{player}&a is on &f{server}'

servers:
  name: 'servers'
  permission: 'servers'

  # The order of the servers on the list
  # Any servers that are not in this list will not show
  order:
    - name_of_a_server
  
  header: '&8&m&l------&r &6&lServers &8&m&l------'
  server: '{server} &f{online} &7Online Players'
  footer: '&8&m&l---------------------'

report:
  name: 'report'
  permission: 'report.use'
  permissionToSee: 'report.see'
  message: '&f{player} &chas reported &7: &f{message}'

chats:
  StaffChat:
    name: 'sc'
    aliases: ['staffchat']
    permission: 'staffChat'

    # {server} : The server they are on
    # {rank} : Players rank
    # {name} : Players name
    # {chat} : Chat colour when vanished
    # {message} : The message
    format: '{server} {rank}{name} &7: {chat}{message}'

list:
  name: 'staff'
  permission: 'staff'
  header: '&8&m&l-----&r &6&lStaff List &8&m&l-----'
  footer: '&8&m&l---------------------'

  list:
    # smutility.rank.<name>
    admin:
      header: '&7[&f{amount}&7] &c&lAdmins'
      section: '&7- &f{player} {server}'

history:
  # Should player history be disabled?
  # This will stop the plugin connecting to a database
  disable: false

  name: 'history'
  permission: 'history'
  header: '&8&m&l---&r &e&l{player} &6&lHistory &8&m&l---'
  # {event} = JOIN, LEAVE
  format: '&r{event} &f{server} &7{date}'
  footer: '&8&m&l---------------------'
  # Amount of history to show
  limit: 10
```

Messages.yml
```yaml
# -----------------------------------------
# Thank you for downloading this plugin! <3
#
# Author : Smudge
# -----------------------------------------

prefix: '&8&l[&f&lServer&8&l]&a'

# Chat colour
default: '&#ffffee'
vanished: '&#c0fce6'

# Command messages
reloaded: '{prefix} Reloaded all configs! <3'
playerIsOffline: '{prefix} Player is offline'
requiresArguments: '&7&l> &7This command requires arguments. /<commands> <args>'

# Make your servers colourised!
# When ever the plugin mentions a server it will format it
# using this list of servers
# <Server Name>: 'What it should be replaced with'
servers:
  TestingServer: '&a&lTest Server'
  Default: '&f&l{server}'

# Rank Colours
# smutility.rank.<name>
ranks:
  Default: '&f'
```