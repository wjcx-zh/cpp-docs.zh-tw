---
title: "編譯器錯誤 C3298 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
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
ms.openlocfilehash: f425cec7ff93bbf98f63b0ebd8e197d7b9b153c2
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3298"></a>編譯器錯誤 C3298
'constraint_1': 無法將 'constraint_2' 當做條件約束使用，因為 'constraint_2' 具有 ref 條件約束，而且 'constraint_1' 具有值條件約束  
  
 您不能指定條件約束的互斥特性。 例如，泛型類型參數不能同時限制為實值類型和參考類型。  
  
 如需詳細資訊，請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3298。  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```
