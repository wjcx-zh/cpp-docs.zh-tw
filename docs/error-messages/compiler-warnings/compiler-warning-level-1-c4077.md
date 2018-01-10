---
title: "編譯器警告 （層級 1） C4077 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4077
dev_langs: C++
helpviewer_keywords: C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2301e1ee077adee35706a4f80d8b2a738743851e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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