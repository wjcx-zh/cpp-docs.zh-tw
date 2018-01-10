---
title: "運算錯誤 M6201 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6201
dev_langs: C++
helpviewer_keywords: M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17de7fab7b41a5a8acc2fed2f3c8185f66aadd9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6201"></a>運算錯誤 M6201
'function': _DOMAIN 錯誤  
  
 指定的函式的引數不合法的輸入值，該函式的網域中。  
  
## <a name="example"></a>範例  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 這個錯誤呼叫`_matherr`函式名稱、 其引數，與錯誤類型的函式。 您可以重新撰寫`_matherr`函式來自訂特定執行階段浮點數學錯誤的處理。