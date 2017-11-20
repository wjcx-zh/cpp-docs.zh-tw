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
ms.openlocfilehash: f0402e03d77968de3b4c1addf58c481ec85a61b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910
'\<識別項 >': '__declspec （dllexport）' 和 'extern' 不相容的明確具現化  
  
 名為的明確樣板具現化*\<識別碼 >*修改由`__declspec(dllexport)`和`extern`關鍵字。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。  
  
## <a name="see-also"></a>另請參閱  
 [明確具現化](../../cpp/explicit-instantiation.md)   
 [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)   
 [一般規則和限制](../../cpp/general-rules-and-limitations.md)