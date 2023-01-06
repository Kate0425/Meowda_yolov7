# Meowda 專題
## About YOLO_V7 to detect cat's detail (by Windows)
## 訓練前準備
### 環境建造-Anaconda Navigator
- 安裝 Anaconda(依自己的OS進行安裝)
    - https://www.anaconda.com/products/distribution/start-coding-immediately
   
![Anaconda](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/Anaconda.png)


- 安裝後打開"開始"並搜尋 **Anaconda Prompt (anaconda3)**
  
   ![prompt](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/prompt.png)

- 點開後輸入指令 cd desktop 按下 Enter 進入到桌面 並開始建立Yolov7 的環境

  ![cd desktop](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/cd%20desktop.png)

### Yolov7 環境建置與起動
- 在 Anaconda Prompt 中輸入 conda create -n yolov7 python=3.9 後按下 Enter
    - (該指示為在 Anaconda 中建立一個名為 yolov7的環境名稱 並指定安裝python 3.9)
    
    ![create yolov7](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/create%20yolov7.png)
- 安裝成功後 在 Anaconda Prompt 中輸入 **conda activate yolov7** 這樣就可以進入到我們所建立的 yolov7 環境中
### Yolov7 專案下載
- 到 Github 下載 Yolov7 官方程式碼及參數
(https://github.com/WongKinYiu/yolov7)

![git](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/git.png)

- 將下載檔放到桌面並解壓縮 
- 回到 Anaconda Prompt 並輸入 cd yolov7 進到放置 Yolov7 官方程式碼及參數資料夾內

  ![cdyolov7](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/cd%20yolov7.png)

### Yolov7 參數變更
- Yolov7 資料夾內打開 **requirements.txt** 並編輯
  - 將torch>=1.7.6 , !=1.12.0 這行刪除
  - 將torchversion>=0.8 , !=0.13.0 這行刪除 並儲存
 
![requirement](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/requirement.png)
  
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
    
![requirement_gpu](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/requirements_gpu.png)
  
### 安裝 Yolov7 參數設定 
- 在 Anaconda Prompt 中輸入 _pip install -r requirements.txt_ 並按 Enter 安裝內部套件
- 安裝後 , 輸入 _pip install -r requirements_gpu.txt_ 並按 Enter 安裝 Pytorch
### 照片的預先處理
- 在 Anaconda Prompt 中輸入 _pip install labelimg_ 並按 Enter 安裝標籤照片的套件

  ![installabelimg](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/install%20labelimg.png)

- 安裝後 在 Anaconda Prompt 輸入 labelimg 並按 Enter 開啟套件
- 開啟後 點開 "Open Dir" 選擇存放照片位置的資料夾 及 "Change Save Dir" 選擇存放標籤位置的資料夾

![dir](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/open%20dir.png)

- 開啟後 即可開始為照片標籤  *[註] 記得切換 YOLO 模式

![labelsop](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/label%20sop.png)
  

### 照片與標籤的分類
- 在 "YOLOV7 資料夾" 選擇 "data 資料夾" 新增 *train* 跟 *val* 資料夾
- 在兩個資料夾內 各自新增 _images_ 跟 _labels_ 資料夾存放照片及標籤

  ![image&label](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/image%26labels.png)

- train 跟 val 照片標籤比例 可以 **1:4 或 1:5** 甚至更多
### 參數編輯
- 複製 _data_ 資料夾內的 **coco.yaml** 並更改成自己習慣的名稱後 開始編輯
  - 編輯內容如下圖
  
![coco yaml](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/coco%20yaml.png)

- 更改 **coco.yaml** 結束後 , 到 _cfg_ 資料夾內部的 _training_ 資料夾 複製 **yolov7.yaml** 一樣更改成自己習慣的名稱並開始編輯
  - 編輯內容如下圖
  
![yolov7yaml](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/yolov7%20yaml.png)

***
## 開始訓練

- 重新打開 _Anaconda prompt_ 輸入 **conda activate yolov7** 進入前面所設定的環境 
- 接著輸入 **cd desktop** 從使用者端進入到桌面 再輸入 **cd yolov7** 進入到檔案存放的資料夾內部
### 指令輸入
- **python train.py --workers 10 --device 0 --batch-size 10 --epochs 600 --img 640 640 --data data/coco_cat.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7_cat.yaml --name yolov7_cat --weights yolov7.pt**

#### 指令介紹
- python train.py : 要用來訓練的 python 檔
- batch size 10 : 依 GPU 大小做設定 如果超出容量 則會跳出 Error , 可以再次修改
- epochs : 訓練次數 通常次數越多 訓練的結果會比較好 , 但不絕對
- img 640 640 : 照片大小為 640 X 640
- data : 將自己 _data_ 資料夾複製的 yaml 檔位置放上
- cfg : 將 _training_ 資料夾複製的 yaml 檔位置放上
- weights : yolov7.pt 為 yolov7 初始權重

#### 訓練過程

![trainig](https://github.com/Kate0425/Meowda_yolov7/blob/main/Meowda_Sop_picture/training.png)



