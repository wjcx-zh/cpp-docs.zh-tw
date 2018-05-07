---
title: 編譯器警告 （層級 1） C4077 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4077
dev_langs:
- C++
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a558ff0ae3c33f25c4f07dc642607fd8a840c70c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4077"></a>編譯器警告 (層級 1) C4077
未知的 check_stack 選項  
  
 搭配未知引數使用 **check_stack** pragma 的舊格式。 此引數必須是 `+`、 `-`、 `(on)`、 `(off)`或空白。  
  
 編譯器會忽略 pragma，並且不會變更堆疊檢查。  
  
## <a name="example"></a>範例  
  
```  
// C4077.cpp  
// compile with: /W1 /LD  
#pragma check_stack yes // C4077  
#pragma check_stack +    // Correct old form  
#pragma check_stack (on) // Correct new form  
```