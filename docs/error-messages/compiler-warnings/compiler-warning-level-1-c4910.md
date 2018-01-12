---
title: "編譯器警告 （層級 1） C4910 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f758e2e15d5492724e9b819622202831d4e9f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910
'\<識別項 >': '__declspec （dllexport）' 和 'extern' 不相容的明確具現化  
  
 名為的明確樣板具現化*\<識別碼 >*修改由`__declspec(dllexport)`和`extern`關鍵字。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。  
  
## <a name="see-also"></a>請參閱  
 [明確具現化](../../cpp/explicit-instantiation.md)   
 [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)   
 [一般規則和限制](../../cpp/general-rules-and-limitations.md)