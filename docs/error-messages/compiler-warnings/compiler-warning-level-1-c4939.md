---
title: 編譯器警告 （層級 1） C4939 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 459674bb4e6899563a18943f7ba510a6168d0e28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296880"
---
# <a name="compiler-warning-level-1-c4939"></a>編譯器警告 (層級 1) C4939
\#pragma vtordisp 已被取代，將在未來的 Visual c + + 版本中移除  
  
 [vtordisp](../../preprocessor/vtordisp.md) pragma 會在未來的 Visual C++ 版本中予以移除。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4939。  
  
```  
// C4939.cpp  
// compile with: /c /W1  
#pragma vtordisp(off)   // C4939  
```