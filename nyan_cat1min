@echo off
setlocal EnableDelayedExpansion
title SYSTEM ERROR
color 0A

set "SELF=%~f0"
set "VID=%TEMP%\nyan.mp4"

:: =========================
:: ERROR MESSAGE BOX SPAM (SHORT)
:: =========================
for /L %%i in (1,1,5) do (
    powershell -NoProfile -Command ^
    "[System.Windows.MessageBox]::Show('Critical system error 0xNYAN%%i','Windows Error',[System.Windows.MessageBoxButton]::OK,[System.Windows.MessageBoxImage]::Error)"
)

:: =========================
:: FULLSCREEN CMD FAKE ENCRYPTION (FAST)
:: =========================
powershell -NoProfile -WindowStyle Hidden -Command ^
Add-Type @"
using System;
using System.Runtime.InteropServices;
public class W {
 [DllImport("user32.dll")] public static extern IntPtr GetForegroundWindow();
 [DllImport("user32.dll")] public static extern int SetWindowLong(IntPtr h,int i,int n);
 [DllImport("user32.dll")] public static extern bool ShowWindow(IntPtr h,int c);
}
"@; ^
$h=[W]::GetForegroundWindow(); ^
[W]::SetWindowLong($h,-16,0x80000000); ^
[W]::ShowWindow($h,3)

mode con cols=120 lines=40
cls
echo YOUR PC HACKED BY NYAAAAAAAN CAT COMPANY
echo.
timeout /t 1 >nul

for %%F in (Documents Downloads Desktop Pictures Videos Music) do (
    echo Encrypting C:\Users\%USERNAME%\%%F\*
    timeout /t 2 >nul
)

echo.
echo ENCRYPTION COMPLETE
timeout /t 1 >nul

:: =========================
:: DOWNLOAD NYAN CAT VIDEO (WITH SOUND)
:: =========================
powershell -NoProfile -Command ^
"$u='https://archive.org/download/NyanCatOriginal/NyanCatOriginal.mp4'; ^
Invoke-WebRequest $u -OutFile '%VID%'"

:: =========================
:: FULLSCREEN LOOPING VIDEO (1 MIN)
:: =========================
powershell -NoProfile -WindowStyle Hidden ^
Add-Type -AssemblyName PresentationFramework; ^
$w=New-Object Windows.Window; ^
$w.WindowStyle='None'; ^
$w.ResizeMode='NoResize'; ^
$w.WindowState='Maximized'; ^
$w.Topmost=$true; ^
$m=New-Object Windows.Controls.MediaElement; ^
$m.Source=[Uri]'%VID%'; ^
$m.LoadedBehavior='Play'; ^
$m.UnloadedBehavior='Stop'; ^
$m.Volume=1.0; ^
$m.Add_MediaEnded({$m.Position=[TimeSpan]::Zero;$m.Play()}); ^
$w.Content=$m; ^
$timer=New-Object Windows.Threading.DispatcherTimer; ^
$timer.Interval=[TimeSpan]::FromSeconds(60); ^
$timer.Add_Tick({$timer.Stop();$w.Close()}); ^
$timer.Start(); ^
$w.ShowDialog()

:: =========================
:: CLEANUP + SELF DELETE
:: =========================
del "%VID%" >nul 2>&1
del "%SELF%" >nul 2>&1
exit
