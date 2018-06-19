---
title: 編譯器警告 （層級 2） C4056 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf5a5855d0b4291105826679e2ae81ed6d69e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290562"
---
# <a name="compiler-warning-level-2-c4056"></a>編譯器警告 （層級 2） C4056
在浮點常數算術中溢位  
  
 浮點常數算術會產生超過允許的最大值的結果。  
  
 這個警告可能因常數算術期間執行的編譯器最佳化。 如果它消失時關閉最佳化，您可以放心忽略這個警告 ([/Od](../../build/reference/od-disable-debug.md))。  
  
 下列範例會產生 C4056:  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```