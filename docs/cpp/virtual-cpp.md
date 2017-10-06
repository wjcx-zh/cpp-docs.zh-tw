---
title: "虛擬 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
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
ms.openlocfilehash: 851f911dd7c49df1d685afe63ef5134cf0d5f175
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="virtual-c"></a>virtual (C++)
`virtual` 關鍵字宣告虛擬函式或虛擬基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>參數  
 `type-specifiers`  
 指定虛擬成員函式的傳回型別。  
  
 `member-function-declarator`  
 宣告成員函式。  
  
 `access-specifier`  
 定義對基底類別的存取層級：`public`、`protected` 或 `private`。 可能出現在 `virtual` 關鍵字之前或之後。  
  
 `base-class-name`  
 識別先前宣告的類別類型。  
  
## <a name="remarks"></a>備註  
 請參閱[虛擬函式](../cpp/virtual-functions.md)如需詳細資訊。  
  
 另請參閱下列關鍵字：[類別](../cpp/class-cpp.md)，[私人](../cpp/private-cpp.md)，[公用](../cpp/public-cpp.md)，和[保護](../cpp/protected-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)
