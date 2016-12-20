---
title: "編譯器錯誤 C2220 | Microsoft Docs"
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
  - "C2220"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2220"
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2220
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將警告視為錯誤處理 \- 沒有產生 object 檔案  
  
 [\/WX](../../build/reference/compiler-option-warning-level.md) 會通知編譯器 \(Compiler\) 將所有的警告視為錯誤。  因為如果發生了錯誤，就無法產生任何目的檔 \(Object File\) 或可執行檔。  
  
 這個錯誤只會在 **\/WX** 旗標在編譯期間是設置狀態才會出現警告。  若要更正這個錯誤，您必須排除專案中每個警告。  
  
### 若要修正，請使用下列其中一種技術  
  
-   解決在專案中產生警告的問題。  
  
-   在較低的警告層級編譯。例如，使用 **\/W3** 而非 **\/W4**。  
  
-   使用 [warning](../../preprocessor/warning.md) 編譯指示來關閉或刪除特定警告。  
  
-   不要使用 **\/WX** 來進行編譯。