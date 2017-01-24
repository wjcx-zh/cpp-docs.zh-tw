---
title: "C++ 陳述式概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陳述式, C++"
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 陳述式概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 陳述式會依序執行，但運算式陳述式、選取陳述式、反覆項目陳述式或跳躍陳述式明確修改該序列時除外。  
  
 陳述式可以是下列任何一種類型：  
  
```  
  
        labeled-statement  
expression-statement  
compound-statement  
selection-statement  
iteration-statement  
jump-statement  
declaration-statement  
try-throw-catch  
```  
  
 在大部分情況下，C\+\+ 陳述式語法與 ANSI C 的語法相同。  兩者的主要差異是，在 C 中只能在區塊的開頭宣告；C\+\+ 則新增了 *declaration\-statement*，能夠有效地移除這項限制。  這可讓您在程式中可以計算預先計算過的初始化數值時引入變數。  
  
 在區塊內部宣告變數也可讓您精確地控制這些變數的範圍和存留期。  
  
 陳述式的相關主題描述下列 C\+\+ 關鍵字：  
  
|||||  
|-|-|-|-|  
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[\_\_if\_exists](../cpp/if-exists-statement.md)|[\_\_try](../cpp/structured-exception-handling-c-cpp.md)|  
|[case](../cpp/switch-statement-cpp.md)|[\_\_except](../cpp/structured-exception-handling-c-cpp.md)|[\_\_if\_not\_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[\_\_leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[\_\_finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## 請參閱  
 [陳述式](../cpp/statements-cpp.md)