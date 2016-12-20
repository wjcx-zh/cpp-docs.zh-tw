---
title: "字元化運算子 (#@) | Microsoft Docs"
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
  - "#@"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#@ 前置處理器運算子"
  - "字元化運算子"
  - "前置處理器, 運算子"
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字元化運算子 (#@)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 字元化運算子只能搭配巨集的引數使用。  在巨集的定義中，如果 **\#@** 出現在型式參數之前，會以單引號括住實質引數，並在展開巨集時將實質引數視為字元。  例如：  
  
```  
#define makechar(x)  #@x  
```  
  
 會使陳述式  
  
```  
a = makechar(b);  
```  
  
 展開成  
  
```  
a = 'b';  
```  
  
 單一引號字元不能與字元化運算子搭配使用。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)