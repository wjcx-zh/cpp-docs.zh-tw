---
title: "編譯器警告 （層級 1） C4606 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 059d50ab268e3f8905e997b28216655af5e3ba1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4606"></a>編譯器警告 (層級 1) C4606
\#pragma 警告: 'warning_number' 忽略;程式碼分析警告不會支援警告層級產生關聯  
  
 程式碼分析警告，只有`error`， `once`，和`default`支援[警告](../../preprocessor/warning.md)pragma。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4606。  
  
```  
// C4606.cpp  
// compile with: /c /W1  
#pragma warning(1: 6001)   // C4606  
#pragma warning(once: 6001)   // OK  
```