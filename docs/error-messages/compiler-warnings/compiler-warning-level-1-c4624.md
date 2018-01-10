---
title: "編譯器警告 （層級 1） C4624 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4624
dev_langs: C++
helpviewer_keywords: C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a3acf93e1609b6a53f6654afb83a51bad49da84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4624"></a>編譯器警告 (層級 1) C4624
'derived class'：解構函式已隱含定義為被刪除，因為基底類別解構函式無法存取或已遭刪除  
  
 解構函式無法在基底類別中存取或已遭刪除，因此無法對衍生類別產生解構函式。 在此堆疊上建立此類型物件的任何嘗試都會導致編譯器錯誤。  
  
 下列範例會產生 C4624，並顯示如何修正此問題：  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```