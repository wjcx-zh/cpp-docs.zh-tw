---
title: "使用加法類運算子 | Microsoft Docs"
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
  - "加法類運算子"
  - "運算子 [C++], 加法"
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用加法類運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列範例 \(其中說明加法和減法運算子\) 使用這些宣告：  
  
```  
int i = 4, j;  
float x[10];  
float *px;  
```  
  
 這些陳述式是相同的：  
  
```  
px = &x[4 + i];  
px = &x[4] + i;    
```  
  
 `i` 的值乘以 **float** 的長度並加入至 `&x[4]`。  產生的指標值為 `x[8]` 的位址。  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 在此範例中，`x` 第三個元素的位址 \(由 `x[i–2]` 指定\) 是減去 `x` 第五個元素的位址 \(由 `x[i]` 指定\) 而得。  其差異值再除以 **float** 的長度，結果為整數值 2。  
  
## 請參閱  
 [C 加法類運算子](../c-language/c-additive-operators.md)