---
title: 運算錯誤 M6111 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b03937ed442b169b960d573b44c0eb6ebca9660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6111"></a>運算錯誤 M6111
堆疊反向溢位  
  
 浮點運算導致 8087/287/387 副處理器或模擬器上的堆疊反向溢位。  
  
 這個錯誤通常因呼叫`long double`沒有傳回值的函式。 例如，下列會產生這個錯誤編譯並執行時：  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 程式終止，結束代碼 139。