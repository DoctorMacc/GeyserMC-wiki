This page covers basic information about the Geyser config and what each option does. Though they are explained in the configuration itself, this explains what each option does in more detail.

## Bedrock Section
The options for Geyser on the bedrock-facing end. Mostly contains options for how bedrock edition will see the server.

**`address`**: The address of Geyser on the bedrock end. In most all scenarios, this should not need to be changed.

**`port`**: The port Geyser will run on. By default, it is 19132 in bedrock.

**`motd1`**: The first line of the MOTD for Geyser. 

**`motd2`**: The second line of the MOTD for Geyser. **Please keep in mind, this option will only work if Geyser is shown in the Friends tab!**

## Remote Section
Options for the remote (java) server. 

**`address`**: The address of the Minecraft: Java Edition server you want to join.

**`port`**: The port of the Minecraft: Java Edition server you specified in the `address` section.

**`auth-type`**: The authentication type of the Minecraft: Java Edition server. Valid options are `online`, `offline`, and `floodgate`.

**Please keep in mind, what you specify in the Geyser `auth-type` option MUST be the same as what the remote server has (with the exception of Geyser being in online mode and remote being in offline mode). You simply cannot join an online mode server without a genuine account. If you want to allow Minecraft: Bedrock Edition accounts to join without a Minecraft: Java Edition account, see the [Floodgate](https://github.com/GeyserMC/Geyser/wiki/Floodgate) page.**

## General Options
General Geyser options that are mostly specific to Geyser itself.

**`floodgate-key-file`**: The key file path for Floodgate. Requires that you have [Floodgate](https://github.com/GeyserMC/Floodgate) installed and the `auth-type` set to `floodgate`.

**`userAuths`**: A section where you can put the authentication information for your Minecraft: Java Edition account for immediate login when joining Geyser. **It is advised you ONLY use this option if you are running Geyser locally and that ONLY you have access to the config as it requires you put your Minecraft: Java Edition credentials in plain text!**

**`ping-passthrough`**: If the MOTD, player count, and max players should be relayed from the remote server. Causes the `motd1` and `motd2` options in the bedrock section to no longer have a use.

**`max-players`**: The maximum amount of players that can join through Geyser.

**`debug-mode`**: If debug messages should be printed in console. Useful if you run into an error and need more context.

**`general-thread-pool`**: The amount of threads Geyser will be able to use. Higher is not always better :P.
 
**`allow-third-party-capes`**: If third party (Optifine, 7zig, LabyMod, etc.) capes should be displayed to the bedrock player.

Default Geyser Config:
```yml
# --------------------------------
# Geyser Configuration File
#
# A bridge between Minecraft: Bedrock Edition and Minecraft: Java Edition.
#
# GitHub: https://github.com/GeyserMC/Geyser
# Discord: https://discord.geysermc.org/
# --------------------------------

bedrock:
  # The IP address that will listen for connections
  address: 0.0.0.0
  # The port that will listen for connections
  port: 19132
  # The MOTD that will be broadcasted to Minecraft: Bedrock Edition clients
  motd1: "GeyserMC"
  motd2: "Another GeyserMC forced host."
remote:
  # The IP address of the remote (Java Edition) server
  address: 127.0.0.1
  # The port of the remote (Java Edition) server
  port: 25565
  # Authentication type. Can be offline, online, or floodgate (see https://github.com/GeyserMC/Geyser/wiki/Floodgate).
  auth-type: online

# Floodgate uses encryption to ensure use from authorised sources.
# This should point to the public key generated by Floodgate (Bungee or CraftBukkit)
# You can ignore this when not using Floodgate.
floodgate-key-file: public-key.pem

## the Xbox/MCPE username is the key for the Java server auth-info
## this allows automatic configuration/login to the remote Java server
## if you are brave/stupid enough to put your Mojang account info into
## a config file
#userAuths:
#  bluerkelp2: # MCPE/Xbox username
#    email: not_really_my_email_address_mr_minecrafter53267@gmail.com # Mojang account email address
#    password: "this isn't really my password"
#
#  herpderp40300499303040503030300500293858393589:
#    email: herpderp@derpherp.com
#    password: dooooo

# Relay the MOTD, player count and max players from the remote server
ping-passthrough: false

# Maximum amount of players that can connect
max-players: 100

# If debug messages should be sent through console
debug-mode: false

# Thread pool size
general-thread-pool: 32

# Allow third party capes to be visible. Currently allowing:
# OptiFine capes, LabyMod capes, 5Zig capes and MinecraftCapes
allow-third-party-capes: true

# bStats is a stat tracker that is entirely anonymous and tracks only basic information
# about Geyser, such as how many people are online, how many servers are using Geyser,
# what OS is being used, etc. You can learn more about bStats here: https://bstats.org/.
# https://bstats.org/plugin/server-implementation/GeyserMC
metrics:
  # If metrics should be enabled
  enabled: true
  # UUID of server, don't change!
  uuid: generateduuid
```