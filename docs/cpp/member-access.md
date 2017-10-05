---
title: "成員存取 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators
- pointers, smart
- member access, overloaded operators
- operator overloading, member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 21cdc3de990a8b23645bb09f9f093fb0f2498254
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="member-access"></a>成員存取
多載成員存取運算子也可以控制類別成員存取 (**->**)。 在這種用法中，這個運算子會視為一元運算子，而多載運算子函式必須是類別成員函式。 因此，這類函式的宣告如下：  
  
## <a name="syntax"></a>語法  
  
```  
  
class-type *operator->()  
```  
  
## <a name="remarks"></a>備註  
 其中*類別類型*是這個運算子所屬的類別的名稱。 成員存取運算子函式必須是非靜態成員函式。  
  
 這個運算子 (通常會搭配指標取值運算子) 會用來實作「智慧型指標」，這類指標會在取值或計數用法之前驗證指標。  
  
 **.** 成員存取運算子無法多載。  
  
## <a name="see-also"></a>另請參閱  
 [運算子多載](../cpp/operator-overloading.md)
