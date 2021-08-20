# Get-Process
$P | Out-File -FilePath .\Process.txt
#include <Constants.au3>
  #include <WindowsConstants.au3>
  #AutoIt3Wrapper_Add_Constants=n
  #include <winapi.au3>
  
  $Parent = GUICreate("main", 500, 500)
  GUISetState()
  
  $ch1 = GUICreate("child1", 200, 200, 0, 0, $WS_CHILD, -1, $Parent)
  GUISetBkColor(0xff0000, $ch1)
  GUISetState()
  
  $ch2 = GUICreate("child2", 300, 300, 100, 100, $WS_CHILD, -1, $Parent)
  GUISetBkColor(0x00FF00, $ch2)
  GUISetState()
  
  $gch1 = GUICreate("grandchild1", 200, 200, 60, 60, $WS_CHILD, -1, $ch2)
  GUISetBkColor(0xffffff)
  GUISetState()
  
  $ch3 = GUICreate("child 3", 200, 200, 300, 300, $WS_CHILD, -1, $Parent);$WS_EX_TOPMOST has no effect
  GUISetBkColor(0xFFFF00, $ch3)
  GUISetState()
  
  $iFlags = BitOR($SWP_SHOWWINDOW, 0);, $SWP_NOSIZE, $SWP_NOMOVE)
  _WinAPI_SetWindowPos($ch3, $HWND_TOPMOST, 0, 0, 0, 0, $iFlags);$HWND_TOP no different---I assume I'm doing something wrong here
;winsetontop($ch3,"",1);no effect but I assume it just uses SetWindowPos
  
  While GUIGetMsg() <> -3
  WEnd
