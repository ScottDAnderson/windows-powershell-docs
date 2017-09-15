---
ms.technology: powershell-mdop
ms.mktglfcycl: manage
ms.author: brianlic
ms.prod: w10
ms.sitesec: library
author: jamiejdt
description: Use this topic to help manage MDOP technologies with Windows PowerShell.
external help file: Microsoft.Uev.Commands.dll-Help.xml
keywords: powershell, cmdlet
manager: alanth 
ms.assetid: 50E966F5-4A51-4766-A2FB-0BD13C593CDA
ms.date: 12/05/2016
ms.devlang: powershell
ms.topic: reference
online version: 
schema: 2.0.0
title: Get-UevConfiguration
---

# Get-UevConfiguration

## SYNOPSIS
Gets the uev_tla configuration settings.

## SYNTAX

### ParameterSetActiveSettings (Default)
```
Get-UevConfiguration [<CommonParameters>]
```

### ParameterSetComputer
```
Get-UevConfiguration [-Computer] [<CommonParameters>]
```

### ParameterSetUser
```
Get-UevConfiguration [-CurrentComputerUser] [<CommonParameters>]
```

### ParameterSetDetails
```
Get-UevConfiguration [-Details] [<CommonParameters>]
```

## DESCRIPTION
The **Get-UevConfiguration** cmdlet gets the uev_1 configuration settings.
If you specify the *Computer* parameter, the cmdlet gets the settings for all users on the computer.
If you specify the *CurrentComputerUser* parameter, the cmdlet gets the settings for just the current user.

## EXAMPLES

### Example 1: Get the uev_tla configurationuev_tla
```
PS C:\> Get-UevConfiguration


Key                                     Value
---                                     -----
MaxPackageSizeInBytes                   700000
SettingsImportNotifyDelayInSeconds      10
SettingsImportNotifyEnabled             False
SettingsStoragePath                     \\ServerName\Path\To\CentralStore
SettingsTemplateCatalogPath
SyncEnabled                             True
SyncMethod                              OfflineFiles
SyncFromRepositoryTimeoutInMilliseconds 2000
```

This command gets the active uev_tla configuration on the computer where you run the cmdlet.

### Example 2: Get the computer-wide configuration
```
PS C:\> Get-UevConfiguration -Computer


Key                                     Value
---                                     -----
MaxPackageSizeInBytes                   700000
SettingsImportNotifyDelayInSeconds
SettingsImportNotifyEnabled
SettingsStoragePath                     \\ServerName\Path\To\CentralStore
SettingsTemplateCatalogPath
SyncEnabled
SyncMethod                              OfflineFiles
SyncFromRepositoryTimeoutInMilliseconds 2000
```

This command gets the uev_tla configuration settings for all users on the computer.
The command gets the HKey Local Machine (HKLM) configuration settings that are in the registry.

### Example 3: Get the user-specific configuration
```
PS C:\> Get-UevConfiguration -CurrentComputerUser


Key                                     Value
---                                     -----
MaxPackageSizeInBytes
SettingsImportNotifyDelayInSeconds
SettingsImportNotifyEnabled
SettingsStoragePath
SyncEnabled
SyncMethod
SyncFromRepositoryTimeoutInMilliseconds
```

This command gets the user-specific uev_tla configuration, including the HKey Current User (HKCU) configuration settings that are in the registry.

## PARAMETERS

### -Computer
Indicates that the cmdlet gets the uev_tla configuration settings for all users on the computer.

```yaml
Type: SwitchParameter
Parameter Sets: ParameterSetComputer
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CurrentComputerUser
Indicates that the cmdlet gets the uev_tla configuration settings for the current user only.

```yaml
Type: SwitchParameter
Parameter Sets: ParameterSetUser
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Details
Indicates that the cmdlet gets the uev_tla configuration settings, including all of the details.

```yaml
Type: SwitchParameter
Parameter Sets: ParameterSetDetails
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### System.Collections.Generic.Dictionary, System.Collections.Generic.KeyValuePair
This cmdlet generates a **KeyValuePair** object that represents the setting name and value, if you specify a setting name.
Otherwise, this cmdlet generates a list of all of the settings.

## NOTES
* A setting value can be from four sources (in order of precedence): group policy settings for the current user, group policy settings for the local computer, the current user, and the local computer. If no setting value is found in any of the sources, uev_tla uses the default setting.

## RELATED LINKS

[Set-UevConfiguration](./Set-UevConfiguration.md)

[Clear-UevConfiguration](./Clear-UevConfiguration.md)

[Import-UevConfiguration](./Import-UevConfiguration.md)

[Export-UevConfiguration](./Export-UevConfiguration.md)

