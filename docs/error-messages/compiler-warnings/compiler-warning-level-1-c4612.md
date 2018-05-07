---
title: 編譯器警告 （層級 1） C4612 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0983f5d0bb89eaf1daee94468b318557bc83cd05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4612"></a>編譯器警告 (層級 1) C4612
Include 檔檔名錯誤  
  
 當檔案名稱不正確或遺漏時， **#pragma include_alias** 會發生這個錯誤。  
  
 引數 **#pragma include_alias**陳述式可以使用引號 (**"***filename***"**) 或角括弧格式 ( **\< ***filename***>**)，但兩端都必須使用相同的格式。  
  
## <a name="example"></a>範例  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```