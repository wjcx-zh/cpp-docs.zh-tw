---
title: 編譯器警告 （層級 1） C4910 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed2ec16f579b05a572cf6bfc236cd8d5743f63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290344"
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910
'\<識別項 >': '__declspec （dllexport）' 和 'extern' 不相容的明確具現化  
  
 名為的明確樣板具現化*\<識別碼 >* 修改由`__declspec(dllexport)`和`extern`關鍵字。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。  
  
## <a name="see-also"></a>另請參閱  
 [明確具現化](../../cpp/explicit-instantiation.md)   
 [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)   
 [一般規則和限制](../../cpp/general-rules-and-limitations.md)