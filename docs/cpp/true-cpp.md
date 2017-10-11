---
title: "true （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b10cf33ff93a01347ee8c8e7fc56bb5be8058f3a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>語法  
  
```  
  
      bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>備註  
 這個關鍵字是兩個類型的變數值的其中一個[bool](../cpp/bool-cpp.md)或條件運算式 （條件運算式是現在，則為 true 的布林運算式）。 如果`i`的型別`bool`，then 陳述式`i = true;`指派**true**至`i`。  
  
## <a name="example"></a>範例  
  
```  
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)
