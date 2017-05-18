---
title: "bad_exception 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bad_exception
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7870c00b019718188b80a64e0102638deb76f588
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="badexception-class"></a>bad_exception 類別
此類別描述可以從非預期處理常式擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>備註  
 如果 `bad_exception` 包含在函式的擲回清單中，則 [unexpected](../standard-library/exception-functions.md#unexpected) 會擲回 `bad_exception`，而不是終止或呼叫使用 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 所指定的另一個函式。  
  
 **what** 所傳回的值是一個實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。  
  
 如需 `bad_exception` 類別所繼承的成員清單，請參閱 [exception 類別](../standard-library/exception-class.md)。  
  
## <a name="example"></a>範例  
 如需擲回 `bad_exception` 的 [unexpected](../standard-library/exception-functions.md#unexpected) 用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<exception>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
[exception 類別](../standard-library/exception-class.md)
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


