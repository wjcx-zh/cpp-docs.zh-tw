---
title: 編譯器警告 （層級 1） C4083 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0d0d7baa0e521484841c638cef4332001a65e78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4083"></a>編譯器警告 （層級 1） C4083
必須是 'token';找到識別項 'identifier'  
  
 識別項，就會發生在錯誤的位置中 **#pragma**陳述式。  
  
## <a name="example"></a>範例  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 請檢查語法[#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)指示詞。