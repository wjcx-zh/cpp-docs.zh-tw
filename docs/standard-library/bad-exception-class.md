---
title: "bad_exception 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.bad_exception"
  - "bad_exception"
  - "std::bad_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_exception 類別"
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# bad_exception 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別描述可以從非預期的處理常式中擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>備註  
 [非預期](../Topic/%3Cexception%3E%20functions.md#unexpected) 將會擲回 `bad_exception` 而非終止或而不是呼叫另一個函式，以指定 [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) 如果 `bad_exception` 包含函式擲回清單中。  
  
 所傳回的值 **什麼** 為實作所定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。  
  
 如需繼承的成員的清單 `bad_exception` 類別，請參閱 [例外狀況類別](../standard-library/exception-class1.md)。  
  
## <a name="example"></a>範例  
 請參閱 [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) 的使用範例 [預期](../Topic/%3Cexception%3E%20functions.md#unexpected) 擲回 `bad_exception`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 例外狀況>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
[例外狀況類別](../standard-library/exception-class1.md)
 [c + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

