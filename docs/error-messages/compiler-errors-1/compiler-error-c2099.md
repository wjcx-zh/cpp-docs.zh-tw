---
title: "編譯器錯誤 C2099 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 74fdc75470600c29029c52e38ab2073e484dbde6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2099"></a>編譯器錯誤 C2099
初始設定式不是常數  
  
 這個錯誤只能由 C 編譯器發出，而且只發生在非自動變數。  編譯器會在程式開始時初始化非自動變數，而所初始化的值必須是常數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2099。  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## <a name="example"></a>範例  
 C2099 也可能是因為編譯器無法執行下的運算式執行常數摺疊**/fp: strict**因為浮點精確度的環境設定 (請參閱[_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)如需詳細資訊) 編譯到執行階段，可能會有所不同。  
  
 當常數摺疊失敗時，編譯器會叫用動態初始化，這在 C 中不被允許。  
  
 若要解決這個錯誤，請將模組編譯為 .cpp 檔或簡化運算式。  
  
 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
 下列範例會產生 C2099。  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```
