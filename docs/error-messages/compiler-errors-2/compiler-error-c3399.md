---
title: "編譯器錯誤 C3399 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3399
dev_langs:
- C++
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
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
ms.openlocfilehash: 1ef4492e3984ae66c4dc6bd41b0dc7c40c734c8a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3399"></a>編譯器錯誤 C3399
'type': 建立泛型參數的執行個體時無法提供引數  
  
 當您指定 `gcnew()` 條件約束時，即指定了無參數建構函式的條件約束類型。 因此，它是嘗試具現化該類型並傳遞參數的錯誤。  
  
 請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3399。  
  
```  
// C3399.cpp  
// compile with: /clr /c  
generic <class T>   
where T : gcnew()  
void f() {  
   T t = gcnew T(1);   // C3399  
   T t2 = gcnew T();   // OK  
}  
```
