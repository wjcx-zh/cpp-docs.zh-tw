---
title: "將整數轉型為浮點值 | Microsoft Docs"
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
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 5635ddf0e940e1f374bfd97d7d6f53dc1b57daec
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="casting-integers-to-floating-point-values"></a>將整數轉型為浮點值
**ANSI 3.2.1.3**：當整數轉換成無法正確地表示原始值的浮點數時，其截斷的方向  
  
 當整數轉型成無法正確地表示其值的浮點值時，會將其值捨入 (向上或向下捨入) 為最接近的適當值。  
  
 例如，將 **unsigned long**(具有 32 位元精確度) 轉型為 **float** (其尾數具有 23 位元精確度) 時，會將數字捨入至最接近 256 的倍數。 **long** 值 4,294,966,913 到 4,294,967,167 都會捨入為 **float** 值 4,294,967,040。  
  
## <a name="see-also"></a>另請參閱  
 [浮點數學](../c-language/floating-point-math.md)
