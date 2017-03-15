---
title: "括號內的運算式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "運算式評估, 評估順序"
  - "運算式 [C++], 評估"
  - "括號"
  - "括號, 運算式"
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 括號內的運算式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將任何運算元包含在括號內，而不會變更括號內運算式的類型或值。  例如，在下列運算式中：  
  
```  
( 10 + 5 ) / 5  
```  
  
 `10 + 5` 前後的括號表示 `10 + 5` 的值會先評估，而且它會變成除法 \(**\/**\) 運算子的左運算元。  `( 10 + 5 ) / 5` 的結果會是 3。  若沒有括號，`10 + 5 / 5` 會評估為 11。  
  
 雖然括號會影響運算式中運算元分組的方式，但是無法保證所有情況下的特定評估順序。  例如，下列運算式中的括號和由左至右群組都無法保證 `i` 在任一子運算式中的值為何：  
  
```  
( i++ +1 ) * ( 2 + i )  
```  
  
 編譯器可以依任何順序自由評估乘法的兩邊。  如果 `i` 的初始值為零，則整個運算式會評估為下面這兩個陳述式的其中一個：  
  
```  
( 0 + 1 + 1 ) * ( 2 + 1 )   
( 0 + 1 + 1 ) * ( 2 + 0 )  
```  
  
 副作用所造成的例外狀況將在[副作用](../c-language/side-effects.md)中加以討論。  
  
## 請參閱  
 [C 主要運算式](../c-language/c-primary-expressions.md)