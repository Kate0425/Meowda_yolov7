# Meowda 專題
## About YOLO_V7 to detect cat's detail (by Windows)
### 環境建造-Anaconda Navigator
- 安裝 Anaconda(依自己的OS進行安裝)
    - https://www.anaconda.com/products/distribution/start-coding-immediately
   ![Anaconda](https://github.com/Kate0425/Meowda_yolov7/blob/main/Anaconda.png)


- 安裝後打開"開始"並搜尋"Anaconda Prompt (anaconda3)"
- 點開後輸入指令 cd desktop 進入到桌面 並開始建立Yolov7 的環境
### Yolov7 環境建置與起動
- 在 Anaconda Prompt 中輸入 -n yolov7 python=3.9 後按下 Enter
    - (該指示為在 Anaconda 中建立一個名為 yolov7的環境名稱 並指定安裝python 3.9)
- 安裝成功後 在 Anaconda Prompt 中輸入 conda activate yolov7 這樣就可以進入到我們所建立的 yolov7 環境中
### Yolov7 專案下載
- 到 Github 下載 Yolov7 官方程式碼及參數
(https://github.com/WongKinYiu/yolov7)
- 將下載檔放到桌面並解壓縮 
- 回到 Anaconda Prompt 並輸入 cd yolov7 進到放置 Yolov7 官方程式碼及參數資料夾內
### Yolov7 參數變更
- Yolov7 資料夾內打開 **requirements.txt** 並編輯
  - 將torch>=1.7.6 , !=1.12.0 這行刪除
  - 將torchversion>=0.8 , !=0.13.0 這行刪除 並儲存
- 新增文件 並將之命名"**requirements_gpu**"
  - A. 到 https://pytorch.org/get-started/previous-versions/#linux-and-windows-1 該網頁的"_Linux and Windows_" 選擇 **# CUDA 11.3**下列的指令將其複製並貼在文件內
  -  B. 將剛剛複製指令當中的 _pip install_ 刪除 , 然後 url 後面的 https....整行剪下並貼到原 先指令上方 且輸入 -i 變成 -i https...
  -  C.拆解剩餘指令
     - -> _torch==1.12.1+cu113_ 
     - -> _torchvision == 0.13.1+cu113 torchaudio==0.12.1_
   - D.最後該文件的指令依序為:
     - -> -i https://download.pytorch.org/whl/cu113
     - ->  torch==1.12.1+cu113
     - ->  torchvision == 0.13.1+cu113 torchaudio==0.12.1
### 安裝 Yolov7 參數設定 
- 在 Anaconda Prompt 中輸入 _pip install -r requirements.txt_ 並按 Enter 安裝內部套件
- 安裝後 , 輸入 _pip install -r requirements_gpu.txt_ 並按 Enter 安裝 Pytorch
### 照片預先的處理
- 在 Anaconda Prompt 中輸入 _pip install labelimg_ 安裝標籤照片的套件