---
title: 編譯器警告 （層級 1） C4470 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4470
dev_langs:
- C++
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57fa405f1137c8627b439110514f63fd3e62d83b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4470"></a>編譯器警告 (層級 1) C4470
浮點控制 pragma 在 /clr 下會忽略  
  
 浮點控制 pragma:  
  
-   [fenv_access](../../preprocessor/fenv-access.md)  
  
-   [float_control](../../preprocessor/float-control.md)  
  
-   [fp_contract](../../preprocessor/fp-contract.md)  
  
 在不影響[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下列範例會產生 C4470:  
  
```  
// C4470.cpp  
// compile with: /clr /W1 /LD  
#pragma float_control(except, on)   // C4470  
```