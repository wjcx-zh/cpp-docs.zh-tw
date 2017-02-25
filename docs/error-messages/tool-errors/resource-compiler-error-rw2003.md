---
title: "資源編譯器錯誤 RW2003 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2003"
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器錯誤 RW2003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生錯誤  
  
### 若要修正，請檢查下列可能原因  
  
1.  **錯誤：點陣圖檔資源 \- 檔案不是 3.00 的格式**  
  
     使用 Windows 2.x 版本格式的點陣圖無法使用在 3.x 版的資源檔。  必須重繪點陣圖，或將其轉換成 3.x 格式。  
  
2.  **錯誤：資源名稱中有舊的 DIB。  透過 SDKPAINT 傳遞**  
  
     指定資源中的裝置獨立式點陣圖 \(DIB\) 與 Windows 3.0 格式不相容。  必須重繪點陣圖，或將其轉換成 3.x 格式。  
  
3.  **錯誤：資源檔的資源名稱不是 3.00 格式**  
  
     指定資源中的圖示或游標使用了前一版 Windows 的格式。  必須重繪圖示或游標，或將其轉換成 3.x 格式。  
  
4.  **未知的 DIB 標頭格式**  
  
     點陣圖標頭不是 BITMAPCOREHEADER 或 BITMAPINFOHEADER 結構。  
  
5.  **無法初始化符號資訊**  
  
     這項錯誤只發生在 Visual C\+\+。  可能的原因是您開啟太多檔案，或是您無法開啟或寫入 Visual C\+\+ 將符號匯入指令碼時所需的資料檔案。  如果沒有特別指定，Visual C\+\+ 會嘗試在 **TMP** 環境變數所指定的目錄中或目前的目錄中來建立這些檔案。  
  
6.  **無法儲存符號資訊**  
  
     這項錯誤只發生在 Visual C\+\+。  可能的原因是您開啟太多檔案，或是您無法關閉或寫入 Visual C\+\+ 將符號匯入指令碼時所需的資料檔案。  如果沒有特別指定，Visual C\+\+ 會嘗試使用 **TMP** 環境變數所指定的目錄或目前目錄中的這些檔案。  
  
7.  **點陣圖檔的資源檔名不是 2.03 的格式**  
  
     點陣圖使用了 2.03 版之前版本的格式。  必須利用 3.00 版或以後版本的格式來轉換或重繪點陣圖。  
  
8.  **資源太大**  
  
     在 Windows 3.1 中，資源不能超過約 65000 個位元組。  若超過此上限，您將無法利用 Visual C\+\+ 或命令列資源編譯器來進行編譯。  此上限不適用於游標、圖示、點陣圖或是其他以檔案為基礎的資源。  
  
9. **資源檔不是 3.00 的格式**  
  
     游標或圖示使用了 3.00 版之前版本的格式。  必須利用 3.00 版或以後版本的格式來轉換或重繪資源。  
  
10. **無法開啟暫存檔**  
  
     資源編譯器 \/Visual C\+\+ 無法開啟暫存檔。  這可能是因為您未擁有此目錄的寫入許可，或是此目錄不存在。  如果沒有特別指定，資源編譯器 \/Visual C\+\+ 會嘗試使用 **TMP** 環境變數所指定的目錄或目前目錄中的檔案。