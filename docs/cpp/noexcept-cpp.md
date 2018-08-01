---
title: noexcept （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 01/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f964e5b05999aeaf51a92f0c91479aaa17dd5b37
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401742"
---
# <a name="noexcept-c"></a>noexcept (C++)
**C + + 11:** 指定函式是否可能擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
> *noexcept 運算式*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept(** *constant-expression* **)**  
  
### <a name="parameters"></a>參數  
 *constant-expression*  
 類型的常數運算式**bool** ，表示是否可能的例外狀況類型是空的。 無條件的版本就相當於`noexcept(true)`。  
  
## <a name="remarks"></a>備註  
 A *noexcept 運算式*是一種類型的*例外狀況規格*，代表一組可能會比對結束的任何例外狀況的例外狀況處理常式的類型的函式宣告的尾碼函式。 條件運算子的一元`noexcept(` *constant_expression* `)`位置*constant_expression* yeilds **true**，及其無條件的同義字**noexcept**，指定可能的例外狀況型別可以結束函式的 set 是空的。 也就是說，函式永遠不會擲回例外狀況，而且絕不允許使用其範圍外傳播例外狀況。 運算子`noexcept(` *constant_expression* `)`位置*constant_expression* yeilds **false**，或例外狀況規格不存在（除了解構函式或解除配置函式），表示可能可以結束函式的例外狀況的集合是所有類型的集合。  
 
 將標示為函式**noexcept**也是它會呼叫，直接或間接的所有函式時，才**noexcept**或是**const**。 編譯器不一定是檢查例外狀況的可能事件反昇最多每個程式碼路徑**noexcept**函式。 如果例外狀況會結束標記為函式的外部範圍`noexcept`， [std:: terminate](../standard-library/exception-functions.md#terminate)會立即叫用，而且沒有任何範圍內物件的解構函式會叫用不保證。 使用**noexcept**而不是動態的例外狀況規範`throw()`，現在已過時的標準。 我們建議您套用`noexcept`任何函式永遠不允許在呼叫堆疊散佈例外狀況。 當宣告的函式**noexcept**，它可讓編譯器產生更有效率的程式碼中的數個不同的內容。 如需詳細資訊，請參閱 <<c0> [ 例外狀況規格](exception-specifications-throw-cpp.md)。   
  
## <a name="example"></a>範例  
複製引數的樣板函式可能會宣告**noexcept**的所複製物件是一般舊資料類型 (POD)。 這類函式可以宣告如下：  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 例外狀況處理](cpp-exception-handling.md)  
 [例外狀況規格 （throw、 noexcept）](exception-specifications-throw-cpp.md)