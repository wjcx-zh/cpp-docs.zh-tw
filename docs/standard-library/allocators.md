---
title: "配置器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
caps.latest.revision: 8
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 74e453298857b94c2c4eb62c5387d4e727f7bb7c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="allocators"></a>配置器
C++ 標準程式庫使用配置器來配置和解除配置容器中所儲存的元素。 所有 C++ 標準程式庫容器 (std:: array 除外) 都有一個 `allocator<Type>` 類型的範本參數，其中 `Type` 代表容器元素的類型。 例如，vector 類別的宣告方式如下：  
  
```  
template <  
    class Type,  
    class Allocator = allocator<Type>  
>  
class vector  
```  
  
 C++ 標準程式庫提供配置器的預設實作。 在 C++11 和更新版本中，預設配置器已更新為公開一個較小的介面；新的配置器稱為「最小配置器」。 尤其是，最小配置器的 `construct()` 成員支援移動語意，可大幅改善效能。 在大部分情況下，此預設配置器應該很足夠。 在 C++11 中，所有接受配置器類型參數的標準程式庫類型和函式都支援最小配置器介面，包括 `std::function`、`shared_ptr, allocate_shared()` 和 `basic_string`。  如需預設配置器的詳細資訊，請參閱 [allocator 類別](../standard-library/allocator-class.md)。  
  
## <a name="writing-your-own-allocator-c11"></a>撰寫您自己的配置器 (C++11)  
 預設配置器使用 `new` 和 `delete` 來配置和取消配置記憶體。 如果您想要使用不同的記憶體配置方法，例如使用共用記憶體，則必須建立您自己的配置器。 如果您的目標是 C++11，而且需要撰寫新的自訂配置器，請儘可能撰寫成最小配置器。 即使您已實作舊式的配置器，還是請考慮修改為「最小配置器」，以善用自動為您提供的更有效率 `construct()` 方法。  
  
 最小配置器需要極少的樣板，可讓您專注於執行所有工作的 `allocate` 和 `deallocate` 成員函式。 建立最小配置器時，以下範例所示的成員除外，請勿實作任何成員：  
  
1.  轉換複製建構函式 (請參閱範例)  
  
2.  operator==  
  
3.  operator!=  
  
4.  allocate  
  
5.  取消配置  
  
 為您提供的 C++11 預設 `construct()` 成員可執行完美的轉送並啟用移動語意，在許多情況下比舊版更有效率。  
  
> [!WARNING]
>  在編譯時期，C++ 標準程式庫會使用 allocator_traits 類別來偵測您明確提供的成員，並且為任何不存在的成員提供預設實作。 請不要為配置器提供特製化的 allocator_traits 而干擾這項機制！  
  
 下列範例示範配置器使用 `malloc` 和 `free` 時的最小實作 請注意，我們使用新的例外狀況類型 `std::bad_array_new_length`，當陣列大小低於零或大於允許的大小上限時會擲回此例外狀況。  
  
```  
#pragma once  
#include <stdlib.h> //size_t, malloc, free  
#include <new> // bad_alloc, bad_array_new_length  
#include <memory>  
template <class T>  
struct Mallocator  
{  
    typedef T value_type;  
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library  
  
    // A converting copy constructor:  
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}  
    template<class U> bool operator==(const Mallocator<U>&) const noexcept  
    {  
        return true;  
    }  
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept  
    {  
        return false;  
    }  
    T* allocate(const size_t n) const;  
    void deallocate(T* const p, size_t) const noexcept;  
};  
  
template <class T>  
T* Mallocator<T>::allocate(const size_t n) const  
{  
    if (n == 0)  
    {  
        return nullptr;  
    }  
    if (n > static_cast<size_t>(-1) / sizeof(T))  
    {  
        throw std::bad_array_new_length();  
    }  
    void* const pv = malloc(n * sizeof(T));  
    if (!pv) { throw std::bad_alloc(); }  
    return static_cast<T*>(pv);  
}  
  
template<class T>  
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept  
{  
    free(p);  
}  
```  
  
## <a name="writing-your-own-allocator-c03"></a>撰寫您自己的配置器 (C++03)  
 在 C++03 中，任何與 C++ 標準程式庫容器搭配使用的配置器都必須實作下列類型定義：  
  
|||  
|-|-|  
|`const_pointer`|`rebind`|  
|`const_reference`|`reference`|  
|`difference_type`|`size_type`|  
|`pointer`|`value_type`|  
  
 此外，任何與 C++ 標準程式庫容器搭配使用的配置器都必須實作下列方法：  
  
|||  
|-|-|  
|建構函式|`deallocate`|  
|複製建構函式|`destroy`|  
|解構函式|`max_size`|  
|`address`|`operator==`|  
|`allocate`|`operator!=`|  
|`construct`||  
  
 如需這些類型定義和方法的詳細資訊，請參閱 [allocator 類別](../standard-library/allocator-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)





