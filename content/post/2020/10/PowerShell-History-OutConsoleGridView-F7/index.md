---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PowerShell History Out-ConsoleGridView F7"
titlelink: ""
subtitle: "Get a GUI for your commandline history in Powershell when pressing F7 or Shift + F7"
summary: "Get a GUI for your commandline history in Powershell when pressing F7 or Shift + F7"
authors: []
tags: [PowerShell, GUI, Out-Gridview, Out-ConsoleGridView]
categories: [PowerShell]
date: 2020-10-06T17:27:26+02:00
lastmod: 2020-10-06T17:27:26+02:00
featured: false
draft: false
profile: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

# Example of posting a picture with shortcode
#
# {{< figure src="images/BackgroundEffectTeams-007.png" title="" lightbox="true" >}}
#
---

### Intro

Did you know that you can use F7 and Shift F7 to get a list of all your commanline history? But now with the new Out-ConsoleGridView you can even get it in a nice GUI format where you can select you command from the history list.

{{< figure src="images/PowerShell-History-OutConsoleGridView-F7-001.png" title="" lightbox="true" >}}

### How-To Step by Step

You start WindowsTerminal or PowerShell prompt, then on the prompt you type:

```powershell
code $profile
```

For the Visual Studio Code or

```powershell
code-insiders $profile
```

for the Visual Studio Code Insiders version.

This will open Visual Studio Code when you have installed this on your device. Else I recommend to install it right a way by going to download it from [here](https://code.visualstudio.com/). 

Add the following code to you PowerShell profile file that you just opened in the previous step.

```powershell
function ocgv_history {
    $line = $null
    $cursor = $null
    [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line, [ref]$cursor)
    $selection = $history | Out-ConsoleGridView -Title "Select CommandLine from History" -OutputMode Single -Filter $line
    if ($selection) {
        [Microsoft.PowerShell.PSConsoleReadLine]::DeleteLine()
        [Microsoft.PowerShell.PSConsoleReadLine]::Insert($selection)
        if ($selection.StartsWith($line)) {
            [Microsoft.PowerShell.PSConsoleReadLine]::SetCursorPosition($cursor)
        }
        else {
            [Microsoft.PowerShell.PSConsoleReadLine]::SetCursorPosition($selection.Lenght)
        }
    }
}

$parameters = @{
    Key = 'F7'
    BriefDescription = 'ShowMatchingHistoryOcgv'
    LongDescription = 'Show Matching History using Out-ConsoleGridView'
    ScriptBlock = {
        param($key, $arg)  # The arguments are Ignored in the example

        $history = Get-History | Sort-Object -Descending -Property Id -Unique | Select-Object CommandLine -ExpandProperty CommandLine
        $history | ocgv_history
    }
}
Set-PSReadLineKeyHandler @parameters

$parameters = @{
    Key = 'Shift-F7'
    BriefDescription = 'ShowMatchingGlobalHistoryOcgv'
    LongDescription = "Show Matching History for all PowerShell instances using Out-ConsoleGridView"
    ScriptBlock = {
        param($key, $arg)   # The arguments are ignored in the example
        $history = [Microsoft.PowerShell.PSConsoleReadLine]::GetHistoryItems().CommandLine
        # reverse the items to most recent is on top
        [array]::Reverse($history)
        $history | Select-Object -Unique | ocgv_history
    }
}
Set-PSReadLineKeyHandler @parameters
```

And save it, the close you Windows Terminal or PowerShell commandline and open it again, when you then press on F7 of Shift + F7 you will get GUI for you commandline history.

# Conclusion

I like it very much, and it's very handy to use. I also put the code on my [github](https://github.com/aavdberg/PowerShell-F7GUI/blob/main/History-F7.ps1)
