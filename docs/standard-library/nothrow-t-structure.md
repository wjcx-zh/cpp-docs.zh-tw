---
title: "nothrow_t 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 1070820b63319cd3f08abbf3d5cd1adf02891cbb
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="nothrowt-structure"></a>nothrow_t 結構
此類別可用來作為 new 運算子的函式參數，以指出函式應該要傳回 Null 指標來回報配置失敗，而非擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>備註  
 此結構可協助編譯器選取正確的建構函式版本。 [nothrow](../standard-library/new-functions.md#nothrow) 與 `std::nothrow_t` 類型的物件同義。  
  
## <a name="example"></a>範例  
 如需如何使用 `std::nothrow_t` 作為函式參數的範例，請參閱 [operator new](../standard-library/new-operators.md#op_new) 和 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<new>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




