---
title: "編譯器警告 (層級 4) C4837 | Microsoft Docs"
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
  - "C4837"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4837"
ms.assetid: 9a3c7b6b-ffe4-443d-96af-43deb80d85b4
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4837
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵測到三併詞: '??%c' 已由 '%c' 取代  
  
 偵測到的三併詞 \(Trigraph\) 已由指定的字元取代。  
  
 編譯器 \(Compiler\) 會在完成其他處理之前轉譯三併詞。  您可以使用字元逸出序列 `\?`，避免錯誤解譯類似三併詞的字元序列。  如需三併詞的詳細資訊，請參閱[三併詞](../../c-language/trigraphs.md)。  如需逸出序列的詳細資訊，請參閱[逸出序列](../../c-language/escape-sequences.md)。  
  
 C4837 預設為關閉。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
### 更正這個錯誤  
  
1.  在原始程式碼中使用字元逸出序列 `\?`，而不是使用其中一個 '?' 字元。  
  
## 請參閱  
 [三併詞](../../c-language/trigraphs.md)   
 [逸出序列](../../c-language/escape-sequences.md)   
 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)