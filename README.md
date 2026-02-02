# Song1~Song10OGG編排器使用手冊(中英雙版本)

>注意:本工具需要FFmpeg可用。建議先完成FFmpeg8.0.1安裝與PATH設定，並在命令列確認ffmpeg -version可正常輸出。

---

## 中文

### 1) 用途
把多個音訊/影片檔指派到Song1.ogg~Song10.ogg，並批次轉成.ogg(可選Vorbis或Opus)。可用拖曳指派、也可用自動填入。可選擇不輸出某些SongX。

### 2) 環境需求
- Windows10/11
- FFmpeg已可在命令列使用(建議FFmpeg8.0.1)
- 若你使用的是exe版工具:不需要Python
- 若你使用的是.py原始碼:需要Python3.13與PySide6(開發用途)

### 3) 介面區塊說明
① 匯入檔案
- 加入檔案:可一次選多個檔案
- 支援拖曳檔案進清單
- 清單內可拖曳排序(影響自動填入順序)
- 可把左邊清單項目直接拖到右邊Song槽位完成指派

② 指派方式
- 自動填入:依左側清單順序，且只填入「已勾選輸出」的Song槽位
- 手動指派:直接把左邊檔案拖到右邊指定Song槽位
- 清空Song指派:把Song1~Song10的指派全部清空

③ Song1~Song10
- 每一列有一個「輸出SongX.ogg」勾選框
- 右側框顯示目前指派的檔案路徑
- 拖曳指派:把左邊檔案拖到該列右側框即可
- 清除單一Song:雙擊該列右側框可清除指派(若你有保留此功能)

④ 輸出設定
- 輸出資料夾:選擇要輸出的資料夾
- 編碼:
- Vorbis:相容性最好，使用q值(0~10，建議4~6)
- Opus:效率較高，使用bitrate(例如64k/96k/128k)

⑤ 開始轉檔
- 按下後會把「已勾選輸出」且「已指派檔案」的Song轉出
- 輸出檔名固定為Song1.ogg~Song10.ogg
- 進度條會顯示目前完成比例

### 4) 標準操作流程(建議)
1) 確認FFmpeg可用
在PowerShell/CMD輸入:
ffmpeg -version2)匯入檔案
按「加入檔案...」選取檔案，或把檔案拖進左側清單

3) 指派Song順序(二選一)
A.自動填入
- 先取消勾選不想輸出的Song
- 整理左側清單順序(用拖曳排序)
- 按「自動填入」

B.手動拖曳指派
- 把左邊清單的檔案拖到右邊指定Song列的框

4) 設定輸出資料夾與編碼
- 選擇輸出資料夾
- 選擇Vorbis或Opus並調整q或bitrate5)開始轉檔
- 按「開始轉檔」
- 完成後到輸出資料夾確認Song1.ogg~Song10.ogg

### 5) 常見問題排除
Q1:開啟程式顯示「找不到FFmpeg」
- 請先安裝FFmpeg並加入PATH，再重新開啟程式
- 用命令列確認ffmpeg -version可輸出

Q2:拖曳指派出現禁止符號
- 確認你拖的是左側清單中的檔案項目(不是清單空白區)
- 確認右側槽位允許拖放(如果你改動過UI，請檢查setAcceptDrops是否仍為True)

Q3:轉檔失敗
- 先用命令列手動測試該檔案:
ffmpeg -i "你的檔案" -vn -c:a libvorbis -q:a5 "test.ogg"
- 若命令列也失敗，代表是輸入檔或FFmpeg環境問題
- 若命令列成功但程式失敗，請把錯誤訊息貼出來

---

## English

### 1) Purpose
Assign media files toSong1.ogg~Song10.oggand batch convert to.ogg(VorbisorOpus). Supports drag-and-drop assignment, auto-fill, and skipping selectedSongXoutputs.

### 2) Requirements
- Windows10/11
- FFmpeg available in terminal(recommendFFmpeg8.0.1)
- Exe build: noPython required
- .py source: requiresPython3.13andPySide6(for development)

### 3) UILayout
① ImportList
- Add files(multi-select) or drag files into the list
- Reorder items by dragging(the order affects auto-fill)
- Drag an item from the left list and drop it onto aSong slot on the right to assign

② AssignmentMode
- AutoFill: uses the left list order and fills only theSong slots that are checked for output
- Manual: drag a file from the left list to a specificSong slot
- ClearSlots: clearsSong1~Song10assignments

③ Song1~Song10Slots
- Each row has anOutputSongX.oggcheckbox
- The right field shows the assigned file path
- Drag-and-drop: drop a file onto the targetSong row field
- Clear a slot: double-click the field(if this feature is enabled)

④ OutputSettings
- OutputFolder: choose where to save outputs
- Codec:
- Vorbis: best compatibility, usesq(0~10, recommend4~6)
- Opus: higher efficiency, usesbitrate(e.g.,64k/96k/128k)

⑤ Convert
- Converts only slots that are checked and assigned
- Output names are fixed:Song1.ogg~Song10.ogg
- Progress bar shows completion percentage

### 4) StandardWorkflow1)VerifyFFmpeg
Run inPowerShell/CMD:
ffmpeg -version2)ImportFiles
ClickAddfiles...or drag files into the left list3)AssignSongs
A. AutoFill
- Uncheck anySong you do not want to output
- Reorder the left list by dragging
- ClickAutoFill

B. ManualDragAssign
- Drag a file from the left list and drop it onto the desiredSong slot field4)SetOutput
- Choose output folder
- SelectVorbisorOpusand setq/bitrate5)Convert
- ClickConvert
- Check outputs in the output folder:Song1.ogg~Song10.ogg

### 5) Troubleshooting
- FFmpegnot found: install FFmpeg and add to PATH, then verifyffmpeg -version
- Drag shows blocked icon: drag a list item(not empty area) and ensure the target field accepts drops
- Conversion failed: test the same input with a terminalFFmpegcommand; if terminal fails, fix the input/FFmpeg; if terminal succeeds, share the app error output
