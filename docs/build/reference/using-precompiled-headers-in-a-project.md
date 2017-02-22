---
title: "在專案中使用先行編譯的標頭 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "先行編譯的標頭"
ms.assetid: 95010260-a035-4327-9d61-222016ac146c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 在專案中使用先行編譯的標頭
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前面章節呈現先行編譯標頭之概觀：\/Yc 和 \/Yu、\/Fp 選項與 [hdrstop](../../preprocessor/hdrstop.md) Pragma。  本章節說明在專案中使用手動先行編譯標頭選項的方法；結尾列示 Makefile 範例及其管理的程式碼。  
  
 至於在專案中使用手動先行編譯標頭選項之另一個方法，請探究其中一個 Makefile，位於在 Visual C\+\+ 的預設設定期間所建立的 MFC\\SRC 目錄中。  這些 Makefile 採行類似於出現在本章節中的方法，但更進一步利用 Microsoft Program Maintenance Utility \(NMAKE\) 巨集，並提供對建置程序更大的控制。  
  
 本節包含下列主題：  
  
-   [建置程序中的 PCH 檔](../../build/reference/pch-files-in-the-build-process.md)  
  
-   [PCH 的 Makefile 範例](../../build/reference/sample-makefile-for-pch.md)  
  
-   [PCH 範例程式碼](../../build/reference/example-code-for-pch.md)  
  
## 請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)