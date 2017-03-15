---
title: "編譯器錯誤 C2567 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2567"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2567"
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 編譯器錯誤 C2567
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 'file' 中無法開啟中繼資料，檔案已刪除或移動  
  
 在與編譯器後端處理序及與編譯器前端處理序相同的目錄中，找不到在原始程式碼中 \(用 `#using`\) 參考的中繼資料檔。  如需詳細資訊，請參閱[\#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。  
  
 如果您以 **\/c** 在一部電腦上編譯，然後嘗試要在另一部電腦上執行連結時間產生程式碼，可能會產生 C2567。  如需詳細資訊，請參閱[\/LTCG \(連結時間產生程式碼\)](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 它也可能表示您的電腦已經沒有記憶體了。  
  
 若要更正這項錯誤，則務必要確定中繼資料檔在建置程序的所有階段都位於相同的目錄位置。