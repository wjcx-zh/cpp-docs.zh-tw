---
title: "編譯器錯誤 C3155 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3155
dev_langs:
- C++
helpviewer_keywords:
- C3155
ms.assetid: b04a42e1-64e7-40f8-81fe-c7945348b2cf
caps.latest.revision: 8
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
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 651eb1a03eed55a3d383a32f027991a4a56d4371
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3155"></a>編譯器錯誤 C3155
屬性索引子中不允許有屬性  
  
索引的屬性宣告不正確。 如需詳細資訊，請參閱[How to︰ 使用屬性，在 C + + /cli CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3155。  
  
```  
// C3155.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct R {  
   property int F[[ParamArray] int] {   // C3155  
   // try the following line instead  
   // property int F[ int] {   // OK  
      int get(int i) {   
         return 0;   
      }  
   }  
};  
```
