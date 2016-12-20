---
title: "C++ 專案中 IntelliSense 的疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ncb 檔案"
  - "IntelliSense, C++ 專案中錯誤的疑難排解"
  - "ncb 檔案"
  - "IntelliSense 疑難排解"
  - "Visual C++ 疑難排解, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# C++ 專案中 IntelliSense 的疑難排解
IntelliSense 在特定情況下可能會停止運作。  請利用下列步驟，判斷 IntelliSense 在 C\+\+ 專案上無法運作的原因。  
  
### 若要調查 C\+\+ 專案中的 IntelliSense 錯誤  
  
1.  確定 Visual C\+\+ 專案沒有編譯錯誤。  
  
    1.  如果專案是 Makefile 專案，請參閱 [如何：在 Makefile 專案中啟用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)。  
  
2.  確定 stdafx.h 位於 Include 路徑中。  如需 Visual C\+\+ 專案中 Include 路徑的詳細資訊，請參閱 [\#include 指示詞](../preprocessor/hash-include-directive-c-cpp.md) 和 [\/I \(其他 Include 目錄\)](../build/reference/i-additional-include-directories.md)。  
  
## IntelliSense 的限制  
 在下列情況下，IntelliSense 無法在 C\+\+ 專案中運作︰  
  
-   游標位於程式碼註解內。  
  
-   您正在撰寫字串常值 \(String Literal\)。  
  
-   游標上方出現語法錯誤。  
  
-   方案包含 Managed C\+\+ 語法或更早的 Managed Extensions for C\+\+ 語法。  
  
-   當您使用 `#include` 指示詞參考某個標頭檔多次時，而且該標頭檔的意義會因為不同的巨集狀態 \(透過 `#define` 指示詞定義\) 而變更，就不完全支援 IntelliSense。  換句話說，當您包含標頭檔多次，而且標頭用法會在不同的巨集狀態下變更，則 IntelliSense 將無法永遠正常運作。  
  
## 請參閱  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/zh-tw/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [如何：組織組建的專案輸出檔案](../ide/how-to-organize-project-output-files-for-builds.md)