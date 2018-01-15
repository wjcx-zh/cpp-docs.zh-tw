---
title: "unique_ptr 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
dev_langs: C++
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba6ac8e50764801052c051703a211c4605a33601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="uniqueptr-class"></a>unique_ptr 類別
儲存自有物件或陣列的指標。 沒有任何其他 `unique_ptr` 擁有此物件/陣列。 當 `unique_ptr` 終結時，物件/陣列也會終結。  
  
## <a name="syntax"></a>語法  
```  
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:  
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;


    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;  
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```  
  
#### <a name="parameters"></a>參數  
 `Right`  
 `unique_ptr`。  
  
 `Nptr`  
 類型為 `rvalue` 的 `std::nullptr_t`。  
  
 `Ptr`  
 `pointer`。  
  
 `Deleter`  
 繫結至 `deleter` 的 `unique_ptr` 函式。  
  
## <a name="exceptions"></a>例外狀況  
 `unique_ptr` 未產生任何例外狀況。  
  
## <a name="remarks"></a>備註  
 `unique_ptr` 類別會取代 `auto_ptr`，且可做為 C++ 標準程式庫容器的項目使用。  
  
 使用 [make_unique](../standard-library/memory-functions.md#make_unique) Helper 函式，有效率地建立 `unique_ptr` 的新執行個體。  
  
 `unique_ptr` 唯一管理資源。 每個 `unique_ptr` 物件儲存自有物件的指標或存放 null 指標。 資源只能由不超過一個 `unique_ptr` 物件擁有；當擁有特定資源的 `unique_ptr` 物件終結時，會釋放資源。 `unique_ptr` 物件可以移動，但不能複製；如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 資源是透過呼叫 `deleter` 類型之預存 `Del` 物件釋放 (這個物件知道如何針對特定 `unique_ptr` 配置資源)。 預設值`deleter``default_delete<T>`假設該資源所指`ptr`配置具有`new`，而且可以藉由呼叫釋出`delete _Ptr`。 (部分特製化 `unique_ptr<T[]>` 管理 `new[]` 配置的陣列物件，而且有預設 `deleter` `default_delete<T[]>`，特製化以呼叫 delete[] `ptr`)。  
  
 自有資源的儲存指標 `stored_ptr` 具有類型 `pointer`。 如果已定義，則為 `Del::pointer`，否則為 `T *`。 如果 `deleter` 是無狀態，預存 `stored_deleter` 物件 `deleter` 不會佔用物件的空間。 請注意，`Del` 可以是參考類型。  
  
## <a name="members"></a>成員  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[unique_ptr](#unique_ptr)|`unique_ptr` 有七個建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[deleter_type](#deleter_type)|`Del` 樣板參數的同義字。|  
|[element_type](#element_type)|`T` 樣板參數的同義字。|  
|[pointer](#pointer)|如果已定義，`Del::pointer` 的同義字，否則為 `T *`。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[get](#get)|傳回 `stored_ptr`。|  
|[get_deleter](#get_deleter)|傳回 `stored_deleter` 的參考。|  
|[release](#release)|將 `pointer()` 儲存在 `stored_ptr`，並傳回其之前的內容。|  
|[reset](#reset)|釋放目前擁有的資源並接受新的資源。|  
|[swap](#swap)|與所提供的 `deleter` 交換資源和 `unique_ptr`。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|`operator bool`|運算子會傳回可以轉換成 `bool` 的類型值。 如果是 `bool`，轉換為 `true` 的結果是 `get() != pointer()`，否則為 `false`。|  
|`operator->`|成員函式會傳回 `stored_ptr`。|  
|`operator*`|成員函式會傳回 `*stored_ptr`。|  
|[unique_ptr operator=](#unique_ptr_operator_eq)|將 `unique_ptr` (或 `pointer-type`) 的值指派至目前的 `unique_ptr`。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
##  <a name="deleter_type"></a>  deleter_type  
 此類型是範本參數 `Del`的同義字。  
  
```  
typedef Del deleter_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Del`的同義字。  
  
##  <a name="element_type"></a>  element_type  
 此類型是範本參數 `Type`的同義字。  
  
```  
typedef Type element_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Ty`的同義字。  
  
##  <a name="get"></a>  unique_ptr::get  
 傳回 `stored_ptr`。  
  
```  
pointer get() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `stored_ptr`。  
  
##  <a name="get_deleter"></a>  unique_ptr::get_deleter  
 傳回 `stored_deleter` 的參考。  
  
```  
Del& get_deleter();

const Del& get_deleter() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會將參考傳回 `stored_deleter`。  
  
##  <a name="unique_ptr_operator_eq"></a>  unique_ptr operator=  
 將提供的 `unique_ptr` 位址指派給目前的位址。  
  
```  
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>  
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```  
  
### <a name="parameters"></a>參數  
 `unique_ptr` 參考用來將該值指派給目前的 `unique_ptr`。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫 `reset(right.release())` 並移動 `right.stored_deleter` 至 `stored_deleter`，然後傳回 `*this`。  
  
##  <a name="pointer"></a>  pointer  
 如果已定義，`Del::pointer` 的同義字，否則為 `Type *`。  
  
```  
typedef T1 pointer;  
```  
  
### <a name="remarks"></a>備註  
 如果已定義，則這個類型與 `Del::pointer` 同義，否則為 `Type *`。  
  
##  <a name="release"></a>  unique_ptr::release  
 將傳回已儲存指標的擁有權釋放給呼叫者，並將已儲存的指標值設為 `nullptr`。  
  
```  
pointer release();
```  
  
### <a name="remarks"></a>備註  
 使用 `release` 接管 `unique_ptr` 所儲存的原始指標之擁有權。 呼叫端會負責刪除傳回的指標。 `unique-ptr` 已設為空白的預設建構狀態。 呼叫 `unique_ptr` 之後，您可以將相容類型的另一個指標指派至 `release`。  
  
### <a name="example"></a>範例  
  此範例顯示釋放呼叫者為何需負責傳回的物件：  
  
```cpp  
// stl_release_unique.cpp  
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp  
#include <iostream>  
#include <memory>  
  
struct Sample {  
   int content_;  
   Sample(int content) : content_(content) {  
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;  
   }  
   ~Sample() {  
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;  
   }  
};  
  
void ReleaseUniquePointer() {  
   // Use make_unique function when possible.    
   auto up1 = std::make_unique<Sample>(3);  
   auto up2 = std::make_unique<Sample>(42);  
  
   // Take over ownership from the unique_ptr up2 by using release  
   auto ptr = up2.release();  
   if (up2) {  
      // This statement does not execute, because up2 is empty.  
      std::cout << "up2 is not empty." << std::endl;  
   }  
   // We are now responsible for deletion of ptr.  
   delete ptr;  
   // up1 deletes its stored pointer when it goes out of scope.     
}  
  
int main() {  
   ReleaseUniquePointer();  
}  
```  
  
  電腦輸出：  
  
```Output  
Constructing Sample(3)  
Constructing Sample(42)  
Deleting Sample(42)  
Deleting Sample(3)  
  
```  
  
##  <a name="reset"></a>  unique_ptr::reset  
 取得指標參數的擁有權，然後刪除原始的已儲存指標。 如果新的指標是與原始的已儲存指標相同，`reset` 會刪除指標，並將已儲存的指標設定為 `nullptr`。  
  
```  
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`ptr`|欲取得擁有權之資源的指標。|  
  
### <a name="remarks"></a>備註  
 請使用 `reset` 來將 `unique_ptr` 擁有的已儲存[指標](#pointer)變更為 `ptr`，然後再刪除原始儲存的指標。 如果 `unique_ptr` 不是空白，`reset` 會叫用 [get_deleter](#get_deleter) 在原始已儲存指標上所傳回的刪除者函式。  
  
 因為 `reset` 會先儲存新指標 `ptr`，然後再刪除原始儲存的指標，所以 `reset` 有可能立即刪除 `ptr` (如果它與原始儲存的指標相同的話)。  
  
##  <a name="swap"></a>  unique_ptr::swap  
 在兩個 `unique_ptr` 物件之間交換指標。  
  
```  
void swap(unique_ptr& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 使用 `unique_ptr` 交換指標。  
  
### <a name="remarks"></a>備註  
 成員函式會交換 `stored_ptr` 與 `right.stored_ptr`，以及交換 `stored_deleter` 與 `right.stored_deleter`。  
  
##  <a name="unique_ptr"></a>  unique_ptr::unique_ptr  
 `unique_ptr` 有七個建構函式。  
  
```  
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,  
    typename conditional<
    is_reference<Del>::value, 
    Del, 
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>  
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`ptr`|指向要指派給 `unique_ptr.` 之資源的指標。|  
|`_Deleter`|要指派給 `unique_ptr` 的 `deleter`。|  
|`right`|`rvalue reference` 指向 `unique_ptr`，而 `unique_ptr` 欄位從其中移動指派為新的已建構 `unique_ptr`。|  
  
### <a name="remarks"></a>備註  
 前兩個建構函式建構不管理任何資源的物件。 第三個建構函式儲存 `stored_ptr` 中的 `ptr`。 第四個建構函式儲存 `stored_ptr` 中的 `ptr` 和 `stored_deleter` 中的 `deleter`。  
  
 第五個建構函式儲存 `stored_ptr` 中的 `ptr`，並將 `deleter` 移動至 `stored_deleter`。 第六個和第七個建構函式儲存 `stored_ptr` 中的 `right.release()`，並將 `right.get_deleter()` 移動至 `stored_deleter`。  
  
##  <a name="dtorunique_ptr"></a>  unique_ptr ~unique_ptr  
 `unique_ptr` 的解構函式，會終結 `unique_ptr` 物件。  
  
```  
~unique_ptr();
```  
  
### <a name="remarks"></a>備註  
 此解構函式會呼叫 `get_deleter()(stored_ptr)`。  
  
## <a name="see-also"></a>請參閱  
 [\<memory>](../standard-library/memory.md)


