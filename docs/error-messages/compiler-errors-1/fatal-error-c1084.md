---
title: "嚴重錯誤 C1084 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1084"
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 嚴重錯誤 C1084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法閱讀 filetype 檔案：'file' : 訊息  
  
 此錯誤通常因編譯器呼叫內部系統 API 失敗所導致。  遇到此錯誤時顯示的訊息通常由 [\_wcserror\_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 或 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx) \(英文\) 產生。  
  
 執行下列步驟，可能有助於解決 C1084：  
  
-   確保指定的檔案存在。  
  
-   確保設定適當的權限，以存取指定的檔案。  
  
-   確保命令列語法符合[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)下所概述的規則。  
  
-   確保環境變數 **TMP** 和 **TEMP** 設定正確，且設定適當的權限，以存取這些環境變數所參考的目錄。  同時請確保 **TMP** 和 **TEMP** 環境變數所參考的磁碟機包含足夠的可用空間量。  
  
-   如果訊息指出「錯誤的檔案號碼」，則指定的檔案可能已在前景關閉，而在背景編譯。  
  
 在執行上述診斷之後，執行清除組建。