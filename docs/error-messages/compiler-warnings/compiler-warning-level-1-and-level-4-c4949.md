---
title: "編譯器警告 （層級 1 和層級 4） C4949 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d23a6d6e030007289cc50ce0372acc8f99e7ed3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>編譯器警告 (層級 1 和層級 4) C4949
pragma 'managed' 和 'unmanaged' 時才有意義的編譯 ' / /clr [: 選項]'  
  
 編譯器會忽略[管理](../../preprocessor/managed-unmanaged.md)和 unmanaged pragma，如果以不編譯原始碼[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 這個警告僅供參考。  
  
 下列範例會產生 C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 當**#pragma unmanaged**使用，而沒有**/clr**，C4949 是層級 4 警告。  
  
 下列範例會產生 C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```