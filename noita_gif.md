
# 0.25MB (1.6% of original)
https://github.com/Madrawn/convenience/assets/1095756/bb5e6f3f-c24a-47d1-b0c0-a3db56677135

# 1MB (6% of original)
[nita.webm](https://github.com/Madrawn/convenience/assets/1095756/532c722b-7b7f-4fd7-bac5-b1727020ca9e)

# 5MB (33% of original)
![nita](https://github.com/Madrawn/convenience/assets/1095756/4c4d86aa-da7f-4166-a415-2318b9f2430c)


``` script.bat
@echo off
setlocal

REM Get the newest gif file in the script's folder
setlocal enabledelayedexpansion
for /f "delims=" %%G in ('dir /b /o-d "%~dp0\*.gif"') do (
    set "newestGif=%%~fG"
    goto :next
)
:next

REM Check if a gif file exists
if defined newestGif (
    REM Construct the output file path
    for %%F in ("!newestGif!") do (
        set "outputFile=%%~dpnF.webm"
    )
    echo outputFile: !outputFile!
)

    REM Run the ffmpeg command
    ffmpeg -i "%newestGif%" -vf "scale=iw/2:ih/2:flags=neighbor,scale=2*iw:2*ih:flags=neighbor" -c:v libvpx-vp9 -b:v 0 -crf 41 "%outputFile%"
    REM ffmpeg -i "%newestGif%" -c:v libvpx-vp9 -b:v 0 -crf 41 "%outputFile%"
)
endlocal

```
