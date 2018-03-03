---
title: "編譯器警告 （層級 1） C4939 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2714963f2b6538805e2352ccb96a19f01f843e73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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