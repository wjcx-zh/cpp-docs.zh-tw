---
title: "運算錯誤 M6111 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 204df0df4855fd2628a96ac326dd39c0d65151e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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