---
title: "編譯器錯誤 C3299 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: 4
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
ms.openlocfilehash: f18264be0d3fcc6ff0e5287b0a1592ddfca95fba
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3299"></a>編譯器錯誤 C3299
'member_function' : 無法指定條件約束，因為它們是繼承自基底方法  
  
 在覆寫泛型成員函式時，您無法指定條件約束子句 (重複條件約束表示不會繼承條件約束)。  
  
 將會繼承您正在覆寫的泛型函式上的條件約束子句。  
  
 如需詳細資訊，請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3299：  
  
```  
// C3299.cpp  
// compile with: /clr /c  
public ref struct R {  
   generic<class T>   
   where T : R  
   virtual void f();  
};  
  
public ref struct S : R {  
   generic<class T>   
   where T : R   // C3299  
   virtual void f() override;  
};  
```
