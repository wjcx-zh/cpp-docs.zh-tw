---
title: "unique_ptr 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unique_ptr"
  - "std.unique_ptr"
  - "std::unique_ptr"
  - "memory/std::unique_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique_ptr 類別"
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# unique_ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

儲存自有物件或陣列的指標。  沒有任何其他 `unique_ptr` 擁有此物件\/陣列。  當 `unique_ptr` 終結時，物件\/陣列也會終結。  
  
## 語法  
  
```  
template< class T, class Del = default_delete<T> >  
    class unique_ptr {  
public:  
    unique_ptr( );  
    unique_ptr( nullptr_t Nptr );  
    explicit unique_ptr( pointer Ptr );  
    unique_ptr( pointer Ptr,  
        typename conditional<is_reference<Del>::value,   
            Del,  
            typename add_reference<const Del>::type>::type Deleter);  
    unique_ptr (pointer Ptr,  
        typename remove_reference<Del>::type&& Deleter);  
    unique_ptr (unique_ptr&& Right);  
    template<class T2, Class Del2> unique_ptr( unique_ptr<T2, Del2>&& Right );  
    unique_ptr( const unique_ptr& Right    ) = delete;  
    unique_ptr& operator=(const unique_ptr& Right     ) = delete;  
};  
  
```  
  
```  
//Specialization for arrays:  
template <class T, class D> class unique_ptr<T[], D>   
{   public:       
     typedef pointer;  
     typedef T element_type;  
     typedef D deleter_type;  
  
     constexpr unique_ptr() noexcept;  
     template <class U> explicit unique_ptr(U p) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     unique_ptr(unique_ptr&& u) noexcept;  
     constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }  
     template <class U, class E>  
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
     template <class U> void reset(U p) noexcept = delete;  
     void swap(unique_ptr& u) noexcept;  
  
    // disable copy from lvalue  
     unique_ptr(const unique_ptr&) = delete;  
     unique_ptr& operator=(const unique_ptr&) = delete;  
   };  
 }  
  
```  
  
#### 參數  
 `Right`  
 `unique_ptr`。  
  
 `Nptr`  
 類型為 `rvalue` 的 `std::nullptr_t`。  
  
 `Ptr`  
 `pointer`。  
  
 `Deleter`  
 繫結至 `deleter` 的 `unique_ptr` 函式。  
  
## 例外狀況  
 `unique_ptr` 未產生任何例外狀況。  
  
## 備註  
 `unique_ptr` 類別會取代 `auto_ptr`，而且可以當做 STL 容器的項目。  
  
 使用 [make\_unique](../Topic/make_unique.md) 協助程式函式，有效率地建立 `unique_ptr` 的新執行個體。  
  
 `unique_ptr` 唯一管理資源。  每個 `unique_ptr` 物件儲存自有物件的指標或存放 null 指標。  資源只能為一個 `unique_ptr` 物件所有；  當擁有特定資源的 `unique_ptr` 物件終結時，就會釋放資源。  `unique_ptr` 可以移動，但不能夠複製；  如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 資源是透過呼叫 `deleter` 類型之預存 `Del` 物件釋放 \(這個物件知道如何針對特定 `unique_ptr` 配置資源\)。  預設 `deleter` `default_delete``<T>` 假設，`_Ptr` 指向的資源是以 `new` 配置的，而且可以透過呼叫 `delete _``Ptr` 釋放   \(部分特製化 `unique_ptr<T[]>` 管理 `new[]` 配置的陣列物件，而且有預設 `deleter` `default_delete<T[]>`，特製化以呼叫 delete\[\] `_Ptr`\)。  
  
 自有資源的儲存指標 `stored_ptr` 具有類型 `pointer`。  如果已定義，則為 `Del::pointer`，否則為 `T *` 。  如果 `deleter` 是無狀態，預存 `stored_deleter` 物件 `deleter` 不會佔用物件的空間。  請注意，`Del` 可以是參考類型。  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[unique\_ptr::unique\_ptr](../Topic/unique_ptr::unique_ptr.md)|`unique_ptr` 有七個建構函式。|  
  
### Typedefs  
  
|||  
|-|-|  
|[deleter\_type](../Topic/deleter_type.md)|`Del` 樣板參數的同義字。|  
|[element\_type](../Topic/element_type.md)|`T` 樣板參數的同義字`.`|  
|[指標](../Topic/pointer.md)|如果已定義，`Del::pointer` 的同義字，否則為 `T *`。|  
  
### 成員函式  
  
|||  
|-|-|  
|[unique\_ptr::get](../Topic/unique_ptr::get.md)|傳回 `stored_ptr`。|  
|[unique\_ptr::get\_deleter](../Topic/unique_ptr::get_deleter.md)|傳回 `stored_deleter` 的參考。|  
|[unique\_ptr::release](../Topic/unique_ptr::release.md)|將 `pointer()` 儲存在 `stored_ptr`，並傳回其之前的內容。|  
|[unique\_ptr::reset](../Topic/unique_ptr::reset.md)|釋放目前擁有的資源並接受新的資源。|  
|[unique\_ptr::swap](../Topic/unique_ptr::swap.md)|與所提供的 `deleter` 交換資源和 `unique_ptr`。|  
  
### 運算子  
  
|||  
|-|-|  
|`operator bool`|運算子會傳回可以轉換成 `bool` 的類型值。  如果是 `bool`，轉換為 `true` 的結果是 `get() != pointer()`，否則為 `false`。|  
|`operator->`|成員函式傳回 `stored_ptr``.`|  
|`operator*`|成員函式傳回 \*`stored_ptr``.`|  
|[unique\_ptr operator\=](../Topic/unique_ptr%20operator=.md)|將 `unique_ptr`  \(或 `pointer-type`\) 的值指派至目前 `unique_ptr`。|  
  
## 需求  
 **標頭：**\<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<memory\>](../standard-library/memory.md)