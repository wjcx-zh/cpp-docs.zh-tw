---
title: "編譯器警告 （層級 3） C4636 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4636
dev_langs:
- C++
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
caps.latest.revision: 10
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
ms.openlocfilehash: 9435d246ea0a6f957196c4ac6f7a6855d725c1c3
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4636"></a>編譯器警告 (層級 3) C4636
套用至 'construct' 的 XML 文件註解: 標記必須是非空白的 '' 屬性。  
  
 標記 (如 `cref`) 沒有值。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4636。  
  
```  
// C4636.cpp  
// compile with: /clr /doc /W3 /c  
/// <see cref=''/>  
// /// <see cref='System::Exception'/>  
ref struct A {   // C4636  
   void f(int);  
};  
  
// OK  
/// <see cref='System::Exception'/>  
ref struct B {  
   void f(int);  
};  
```
