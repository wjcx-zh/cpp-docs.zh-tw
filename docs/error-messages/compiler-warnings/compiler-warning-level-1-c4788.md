---
title: "編譯器警告 (層級 1) C4788 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4788"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4788"
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 1) C4788
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 識別項被截斷成 'number' 個字元  
  
 編譯器限制了函式名稱所允許的最大長度。  當編譯器為 EH\/SEH 程式碼產生 Funclet 時，它會在函式名稱之前加上一些文字，例如 "\_\_catch"、"\_\_unwind" 或另一個字串，以組成 Funclet 名稱。  
  
 所產生的 Funclet 名稱可能會太長，而編譯器會將它截斷並產生 C4788。  
  
 若要解除這項警告，請縮短原來的函式名稱。  如果函式是 C\+\+ 樣板函式或方法，請使用 typedef 做為部分名稱。  例如：  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 可以取代成：  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 這個警告在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯器才會發生。