---
title: "&lt;exception&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<exception>"
  - "std::<exception>"
  - "std.<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception 標頭"
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;exception&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義數個與例外狀況處理有關的類型和函式。 在系統可從錯誤復原的情況下，使用例外狀況處理。 它提供方式，將控制從函式傳回至程式。 併入例外狀況處理的目標是增加程式穩定性，同時以有次序的方式從錯誤復原。  
  
## <a name="syntax"></a>語法  
  
```  
#include <exception>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[exception_ptr](../Topic/%3Cexception%3E%20typedefs.md#exception_ptr)|描述例外狀況指標的類型。|  
|[terminate_handler](../Topic/%3Cexception%3E%20typedefs.md#terminate_handler)|類型，描述適合做為 `terminate_handler` 之函式的指標。|  
|[unexpected_handler](../Topic/%3Cexception%3E%20typedefs.md#unexpected_handler)|類型，描述適合做為 `unexpected_handler` 之函式的指標。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[current_exception](../Topic/%3Cexception%3E%20functions.md#current_exception)|取得目前例外狀況的指標。|  
|[get_terminate](../Topic/%3Cexception%3E%20functions.md#get_terminate)|取得目前的 `terminate_handler` 函式。|  
|[get_unexpected](../Topic/%3Cexception%3E%20functions.md#get_unexpected)|取得目前的 `unexpected_handler` 函式。|  
|[make_exception_ptr](../Topic/%3Cexception%3E%20functions.md#make_exception_ptr)|建立持有例外狀況複本的 `exception_ptr` 物件。|  
|[rethrow_exception](../Topic/%3Cexception%3E%20functions.md#rethrow_exception)|擲回做為參數傳遞的例外狀況。|  
|[set_terminate](../Topic/%3Cexception%3E%20functions.md#set_terminate)|建立新 `terminate_handler`，在程式終止時呼叫。|  
|[set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected)|建立新的 `unexpected_handler`，當未預期的例外狀況發生時擲回。|  
|[終止](../Topic/%3Cexception%3E%20functions.md#terminate)|呼叫終止處理常式。|  
|[uncaught_exception](../Topic/%3Cexception%3E%20functions.md#uncaught_exception)|傳回 **true** 只有當正在處理擲回的例外狀況。|  
|[非預期](../Topic/%3Cexception%3E%20functions.md#unexpected)|呼叫未預期的處理常式。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[bad_exception 類別](../standard-library/bad-exception-class.md)|此類別描述從 `unexpected_handler` 所擲回的例外狀況。|  
|[例外狀況類別](Exception%20Class.xml)|此類別做為由某些運算式和 Standard C++ 程式庫所擲回的所有例外狀況的基底類別。|  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

