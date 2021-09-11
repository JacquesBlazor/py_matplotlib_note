# 如何修正 python 中 matplotlib 套件顯示中文的問題

請參考以下快速可行的方案:

0) 請確認您有安裝 matplotlib 套件。

1) 打開命令提示字元 Command Prompt, 輸入下列指令:

   python -c "print(\_\_import\_\_('matplotlib').matplotlib_fname())"

   或是在命令提示字元輸入 python (或 python3) 按下 Enter，然後在 >>> 的提示字元
   後，分別輸入以下兩行指令：

      import matplotlib
      print(matplotlib.matplotlib_fname())

2) 檢視上述的輸出結果。這是 matplotlib 的設定檔。輸出結果會類似於:

   C:\Users\<username>\AppData\Local\Programs\Python\Python38\lib
     \site-packages\matplotlib\mpl-data\matplotlibrc

3) 用 Notepad 或文字編輯器開啟上述的 matplotlibrc 設定檔，找到開頭為：

　　　#font.serif
　　　#font.sans-serif

   這兩行。

4) 編輯這個檔案。移除這兩行前面的 #。
5) 在上述兩行的 "DejaVu Serif" 前加入

      "Microsoft JhengHei, "
      (不含引號)。

6) 接著繼續找到下列開頭為 # axes 這行：

      #axes.unicode_minus

7) 移除這行前的 #。
8) 修改這行結尾的 True 為 False (這樣圖片中可以顯示負號)。
9) 將修改上述內容後的 matplotlibrc 設定檔存檔。
10) 在開始功能表，按右鍵，選[執行]。輸入 %userprofile%。按下[確定]。
11) 找到 %userprofile%\.matplotlib 目錄。這是快取檔案。刪除這個目錄。
12) 到步驟2)的

    lib\site-packages\matplotlib\__pycache__

    這個__pycache__目錄。這是快取檔案。刪除這個目錄。

13) 在開始功能表，按右鍵，選[執行]。輸入 fonts。按下[確定]。
14) 在搜尋輸入 "Microsoft JhengHei"。找到後點取它後，按右鍵，選[複製]。
15) 開啟在步驟2)的

   lib\site-packages\matplotlib\mpl-data\ 下的 fonts\ttf 目錄資料夾。

16) 貼上剛才的 "Microsoft JhengHei" 字形檔案(可能有3個)。

17) 好了。重新啟動你的程式。套件會重新產生步驟 11 和 步驟 12 的目錄。
