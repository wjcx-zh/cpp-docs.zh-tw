---
title: "連結器工具錯誤 LNK1104 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1104"
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟檔案 'filename'  
  
 此工具無法開啟指定的檔案。  
  
 您可以檢查下列可能的原因來進行修正：  
  
-   磁碟空間不足。  
  
-   檔案不存在。  
  
-   在專案的屬性頁對話方塊中指定程式庫時，程式庫名稱應以空格 \(而不是逗號\) 分隔。  
  
-   檔案名稱或路徑不正確。  
  
-   磁碟機規格不正確。  
  
-   檔案權限不足。  
  
-   `filename` 的路徑超過 260 個字元。  
  
-   如果指定的檔案以連結器為暫存檔所產生的檔案名稱 `LNKn` 命名，在 TMP 環境變數中指定的目錄可能不存在，或為 TMP 環境變數指定了一個以上的目錄 \(應該只為 TMP 環境變數指定一個目錄路徑\)。  
  
-   如果錯誤訊息是因某程式庫名稱而出現，且您最近才移植了一個舊版 Microsoft Visual C\+\+ 開發系統的 .mak 檔，該程式庫可能不再有效。 請確定該程式庫在這個情況下仍然存在。  
  
-   其他程式可能開啟該檔案，而使連結器無法寫入。  
  
-   LIB 環境變數不正確。 如需如何更新 LIB 環境變數的相關資訊，請參閱 [VC\+\+ 目錄屬性頁](../../ide/vcpp-directories-property-page.md)。 請確定您所需之程式庫的任何目錄皆列於此處。  
  
 連結器在幾種情況下會使用暫存檔。 即使在足夠的磁碟空間下，大規模的連結仍會耗盡或分割位址空間。  
  
 使用下列可能的解決方式來進行修正  
  
-   使用 [\/OPT \(最佳化\)](../../build/reference/opt-optimizations.md)；刪除可轉移的 Comdat 可以多次讀取所有目的檔。  
  
-   升級至 Windows XP。