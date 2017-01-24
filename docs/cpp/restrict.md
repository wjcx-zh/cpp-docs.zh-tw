---
title: "restrict | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "restrict"
  - "restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], restrict"
  - "restrict __declspec 關鍵字"
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 套用至會傳回指標類型的函式宣告或定義，並告知編譯器該函式會傳回物件，且該物件不具有任何其他指標的別名。  
  
## 語法  
  
```  
__declspec(restrict) return_type f();  
```  
  
## 備註  
 編譯器會散佈 `__declspec(restrict)`。  例如，CRT `malloc` 函式會以 `__declspec(restrict)` 裝飾，因此，以 `malloc` 初始化至記憶體位置的指標也是隱含不具別名。  
  
 編譯器不會檢查指標實際上有沒有別名。  開發人員必須負責確保程式不會對以 `restrict __declspec` 修飾詞標記的指標使用別名。  
  
 如需變數的類似語法，請參閱 [\_\_restrict](../cpp/extension-restrict.md)。  
  
## 範例  
 如需 `restrict` 的使用範例，請參閱 [noalias](../cpp/noalias.md)。  
  
 如需有關屬於 C\+\+ AMP 之限制關鍵字的詳細資訊，請參閱[restrict \(C\+\+ AMP\)](../cpp/restrict-cpp-amp.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)