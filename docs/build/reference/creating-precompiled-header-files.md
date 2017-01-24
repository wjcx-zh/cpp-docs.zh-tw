---
title: "建立先行編譯標頭檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - ".pch 檔案, 建立"
  - "cl.exe 編譯器, 先行編譯程式碼"
  - "PCH 檔案, 建立"
  - "先行編譯標頭檔, 建立"
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建立先行編譯標頭檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft C 和 C\+\+ 編譯器 \(Compiler\) 提供先行編譯任一 C 或 C\+\+ 程式碼 \(包括內嵌程式碼\) 的選項。  利用這項效能特性，您可編譯穩定的程式碼主體、在檔案中儲存程式碼的已編譯狀態，並在後續的編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。  每一項後續的編譯都會更快，因為穩定的程式碼即無需再重新編譯。  
  
 本章節說明下列先行編譯標頭的問題：  
  
-   [先行編譯原始程式碼的時機](../../build/reference/when-to-precompile-source-code.md)  
  
-   [先行編譯程式碼的兩個選擇](../../build/reference/two-choices-for-precompiling-code.md)  
  
-   [先行編譯標頭的一致性規則](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [在專案中使用先行編譯的標頭](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 如需與先行編譯的標頭相關的編譯器選項之參考資訊，請參閱[\/Y \(先行編譯標頭\)](../../build/reference/y-precompiled-headers.md)。  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [編譯器選項](../../build/reference/compiler-options.md)