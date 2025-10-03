[![](https://github.com/TechTutoPPT/Display-and-Control-Android-Device/blob/main/IMG_8243.PNG)](https://youtu.be/9WATchwZ1Ao)

scrcpy可以將Android裝置透過USB或TCP/IP將聲音及畫面鏡像投射到PC, 並允許使用電腦的鍵盤和鼠標進行控制.
它不需要Root的權限, 但對Android版本有要求, 最好是Andaroid 12以上能使用全部功能, 最低版本不能低於5.

以下是操作流程:
手機需要做以下設定:
進入手機設定>關於手機>連續點擊版本號7次以開啟開發者選項>
於設定中搜尋開發者選項並進入該設定>啟用USB偵錯>透過USB線連接手機與電腦.

於官網下載最新的scrcpy:
'''
https://github.com/Genymobile/scrcpy/releases
'''
下載回來後透過檔案總管移動至下載位置並將之解壓, 於解壓目錄(有顯示adb.exe及scrcpy.exe等檔案的那頁)上方路徑位置輸入cmd並執行進入終端機,
先執行以下指令查看是否已連接裝置(裝置上彈出允許USB調試權限時請按允許):
'''
adb devices
'''
再執行以下指令便可進行投屏:
'''
scrcpy
'''

而scrcpy強大之處是它不僅能夠有線連接, 亦可進行無線連接(Android裝置及PC在同一WiFi網段), 
先執行以下指令將Android裝置的調試模式切換成TCP/IP, 並指定5555端口作為ADB的連接端口:
'''
adb tcpip 5555
'''
成功後, 便可斷開USB連線, 並執行以下指令將PC與Android裝置進行無線連接:
'''
adb connect 裝置IP地址
'''
最後執行投屏指令:
'''
scrcpy
'''

只有投屏效果可能未必滿足到大家的需要, 那就再多講一些參數及應用例子供大家參考:
全屏顯示(Alt+f切換):
'''
scrcpy --fullscreen
'''
將電腦滑鼠的移動及點擊操作直接輸入給裝置(Alt切換):
'''
scrcpy --mouse=uhid
'''
投屏時關閉裝置屏幕(Alt+o關閉, Alt+Shift+o開啟):
'''
scrcpy --turn-screen-off
'''
投屏時視窗永遠最上層顯示:
'''
scrcpy --always-on-top
'''
投屏時於終端上提供FPS資訊(Alt+i切換):
'''
scrcpy --print-fps
'''
錄製螢幕:
'''
scrcpy --record demo.mp4
'''
而各參數亦可混合使用, 例如以H.265制式捕捉螢幕(更佳質素), 解像度設為 1920, 幀率設為 60fps:
'''
scrcpy --video-codec=h265 --max-size=1920 --max-fps=60
'''
假如你組合出的指令非常長, 建議將這指令以記事簿記錄後另存為.bat批處理檔保存於scrcpy資料夾中, 這樣更方便執行.


