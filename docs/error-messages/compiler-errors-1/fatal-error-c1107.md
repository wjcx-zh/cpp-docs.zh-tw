---
title: "嚴重錯誤 C1107 | Microsoft Docs"
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
  - "C1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1107"
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到組件 'file': 請使用 \/AI 或設定 LIBPATH 環境變數來指定組件搜尋路徑  
  
 中繼資料檔被傳遞給編譯器找不到的 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞。  
  
 LIBPATH \(`#using` 主題中有說明\) 和 [\/AI](../../build/reference/ai-specify-metadata-directories.md) 編譯器選項可以讓您指定編譯器要在其中尋找參考之中繼資料檔的目錄。