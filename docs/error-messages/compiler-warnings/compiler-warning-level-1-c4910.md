---
title: "編譯器警告 （層級 1） C4910 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: b8416e456a7d985eb7a3c40addb716ba5c30bf96
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910
'\<識別碼 >': '__declspec （dllexport）' 和 'extern' 不相容的明確具現化  
  
 名為的明確樣板具現化*\<識別碼 >*修改由`__declspec(dllexport)`和`extern`關鍵字。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。  
  
## <a name="see-also"></a>另請參閱  
 [明確具現化](../../cpp/explicit-instantiation.md)   
 [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)   
 [一般規則和限制](../../cpp/general-rules-and-limitations.md)
