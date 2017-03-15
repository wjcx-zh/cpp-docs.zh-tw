---
title: "副作用 | Microsoft Docs"
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
  - "運算式評估, 副作用"
  - "運算式評估的副作用"
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 副作用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

運算式的評估順序是由特定實作定義，但語言保證特定評估順序者除外 \(如[評估的優先順序和順序](../c-language/precedence-and-order-of-evaluation.md)中所述\)。  例如，副作用會在下列函式呼叫中發生：  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 函式呼叫的引數可以依照任何順序進行評估。  運算式 `i + 1` 可以在 `i = j + 2` 之前評估，或者 `i = j + 2` 也可以在 `i + 1` 之前評估。  每種情況產生的結果各不相同。  同樣，都無法保證實際會傳遞什麼字元至 `myproc`。  由於一元的遞增和遞減作業與指派相關，因此這類作業可能會造成副作用，如下列範例所示：  
  
```  
x[i] = i++;  
```  
  
 在此範例中，無法預期 `x` 修改過的值。  下標的值可以是 `i` 的新值或舊值。  結果可能會依不同的編譯器或不同的最佳化層級而異。  
  
 由於 C 不會定義副作用的評估順序，因此以上所討論的兩種評估方法均正確，並且可以實作其中任何一種。  若要確定程式碼的可攜性和明確性，請避免使用依賴特定副作用評估順序的陳述式。  
  
## 請參閱  
 [運算式評估](../c-language/expression-evaluation-c.md)