---
title: 編譯器警告 （層級 1） C4618 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4618
dev_langs:
- C++
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e53f8542983a6e15f353ff181efa280815fea9d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4618"></a>編譯器警告 (層級 1) C4618
pragma 參數包含空白的字串。已忽略 pragma  
  
 做為引數提供 null 字串 **#pragma**。  
  
 Pragma 已處理沒有引數。  
  
 下列範例會產生 C4618:  
  
```  
// C4618.cpp  
// compile with: /W1 /LD  
#pragma code_seg("")   // C4618  
```