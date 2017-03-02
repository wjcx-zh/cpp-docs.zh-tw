---
title: "編譯器錯誤 C3609 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3609
dev_langs:
- C++
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ffb46df64ac0a18847c3595f9fb3fffc3bd26c51
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3609"></a>編譯器錯誤 C3609
'member'：密封或最終函式必須為虛擬  
  
 [密封](../../windows/sealed-cpp-component-extensions.md)和[最終](../../cpp/final-specifier.md)關鍵字只允許在標示的類別、 結構或成員函式`virtual`。  
  
 下列範例會產生 C3609：  
  
```  
// C3609.cpp  
// compile with: /clr /c  
ref class C {  
   int f() sealed;   // C3609  
   virtual int f2() sealed;   // OK  
};  
```  

