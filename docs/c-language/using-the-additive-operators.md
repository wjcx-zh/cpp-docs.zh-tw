---
title: "使用加法類運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 9f2bdbc6a22754587dce3cb2a4c9b2baf12a1a1f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="using-the-additive-operators"></a>使用加法類運算子
下列範例 (其中說明加法和減法運算子) 使用這些宣告：  
  
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
  
 `i` 的值乘以 **float** 的長度，並新增至 `&x[4]`。 產生的指標值為 `x[8]` 的位址。  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 在此範例中，`x` 第三個元素的位址 (由 `x[i-2]` 指定) 是減去 `x` 第五個元素的位址 (由 `x[i]` 指定) 而得。 其差異值再除以 **float** 的長度，結果為整數值 2。  
  
## <a name="see-also"></a>另請參閱  
 [C 加法類運算子](../c-language/c-additive-operators.md)
