---
title: "exception 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 6983a0e24f7422b708d7fbbfca6689bec629cb06
ms.lasthandoff: 02/24/2017

---
# <a name="exception-class"></a>exception 類別
此類別可作為特定運算式和 C++ 標準程式庫所擲回之所有例外狀況的基底類別。  
  
## <a name="syntax"></a>語法  
```  
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };  
``` 
## <a name="remarks"></a>備註  
 具體來說，這個基底類別是 [\<stdexcept>](../standard-library/stdexcept.md) 中定義之標準例外狀況類別的根本。 預設建構函式不會指定 `what` 所傳回的 C 字串值，但特定衍生類別的建構函式可能會將其定義為由實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。  
  
 如果不應配置任何記憶體，可使用 `int` 參數來指定。 系統會忽略 `int` 值。  
  
> [!NOTE]
>  建構函式 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 Microsoft 的 C++ 標準程式庫延伸模組。  
  
## <a name="example"></a>範例  
 如需繼承自 `exception` 類別之標準例外狀況類別的用法範例，請參閱 [\<stdexcept>](../standard-library/stdexcept.md) 中定義的任何類別。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<exception>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




