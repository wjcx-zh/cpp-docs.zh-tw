---
title: "bad_exception 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exception/std::bad_exception
dev_langs: C++
helpviewer_keywords: bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5b91f3019a46aa011f95ae26434456d1e41de08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
[例外狀況類別](../standard-library/exception-class.md) [c + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

