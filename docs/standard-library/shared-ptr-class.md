---
title: "shared_ptr 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "shared_ptr"
  - "tr1::shared_ptr"
  - "memory/std::tr1::shared_ptr"
  - "std::tr1::shared_ptr"
  - "std.tr1.shared_ptr"
  - "tr1.shared_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared_ptr 類別"
  - "shared_ptr 類別 [TR1]"
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# shared_ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將參考計數的智慧型指標環繞動態配置物件。  
  
## 語法  
  
```  
template<class Ty>  
   class shared_ptr {  
public:  
    typedef Ty element_type;  
  
    shared_ptr();  
    shared_ptr(nullptr_t);   
    shared_ptr(const shared_ptr& sp);  
    shared_ptr(shared_ptr&& sp);  
    template<class Other>  
        explicit shared_ptr(Other * ptr);  
    template<class Other, class D>  
        shared_ptr(Other * ptr, D dtor);  
    template<class D>  
        shared_ptr(nullptr_t, D dtor);  
    template<class Other, class D, class A>  
        shared_ptr(Other *ptr, D dtor, A alloc);  
    template<class D, class A>  
        shared_ptr(nullptr_t, D dtor, A alloc);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>&& sp);  
    template<class Other>  
        explicit shared_ptr(const weak_ptr<Other>& wp);  
    template<class Other>  
        shared_ptr(auto_ptr<Other>& ap);  
    template<class Other, class D>  
        shared_ptr(unique_ptr<Other, D>&& up);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp, Ty *ptr);  
    ~shared_ptr();  
    shared_ptr& operator=(const shared_ptr& sp);  
    template<class Other>   
        shared_ptr& operator=(const shared_ptr<Other>& sp);  
    shared_ptr& operator=(shared_ptr&& sp);  
    template<class Other>   
        shared_ptr& operator=(shared_ptr<Other>&& sp);  
    template<class Other>   
        shared_ptr& operator=(auto_ptr< Other >&& ap);  
    template <class Other, class D>   
        shared_ptr& operator=(const unique_ptr< Other, D>& up) = delete;  
    template <class Other, class D>  
        shared_ptr& operator=(unique_ptr<Other, D>&& up);  
    void swap(shared_ptr& sp);  
    void reset();  
    template<class Other>  
        void reset(Other *ptr);  
    template<class Other, class D>  
        void reset(Other *ptr, D dtor);  
    template<class Other, class D, class A>  
        void reset(Other *ptr, D dtor, A alloc);  
    Ty *get() const;  
    Ty& operator*() const;  
    Ty *operator->() const;  
    long use_count() const;  
    bool unique() const;  
    operator bool() const;  
  
    template<class Other>  
        bool owner_before(shared_ptr<Other> const& ptr) const;  
    template<class Other>  
        bool owner_before(weak_ptr<Other> const& ptr) const;  
    template<class D, class Ty>   
        D* get_deleter(shared_ptr<Ty> const& ptr);  
};  
  
```  
  
#### 參數  
 `Ty`  
 共用指標所控制的類型。  
  
 `Other`  
 引數指標所控制的類型。  
  
 `ptr`  
 要複製的指標。  
  
 `D`  
 刪除者的類型。  
  
 `A`  
 配置器的類型。  
  
 `dtor`  
 刪除者。  
  
 `alloc`  
 配置器。  
  
 `sp`  
 要複製或移動的智慧型指標。  
  
 `wp`  
 要複製或移動的弱式指標。  
  
 `ap`  
 要複製或移動的自動指標。  
  
 `up`  
 要移動的唯一指標。  
  
## 備註  
 樣板類別描述使用參考計數來管理資源的物件。  `shared_ptr`物件實際上存放了它擁有之資源的指標，或是存放 null 指標。  資源可以由多個 `shared_ptr` 物件擁有；當擁有特定資源的最後一個 `shared_ptr` 物件終結時，會釋放資源。  
  
 `shared_ptr` 會在重新指派或重設時停止擁有資源。  
  
 樣板引數 `Ty` 可能是不完整的類型，針對特定成員函式註明者除外。  
  
 當 `shared_ptr<Ty>` 物件是從 `G*` 類型的資源指標或是從`shared_ptr<G>`建構時，指標類型 `G*` 必須可轉換為 `Ty*`。  否則將不會編譯程式碼。  例如:  
  
```cpp  
class F {};  
class G : public F {};  
```  
  
```cpp  
  
#include <memory>  
  
using namespace std;  
  
shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*  
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>  
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*  
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>  
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>  
shared_ptr<int> sp5(new G); // error, G* not convertible to int*  
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>  
```  
  
 `shared_ptr` 物件在下列情況下會擁有資源：  
  
-   如果它是使用該資源的指標建構，  
  
-   如果它是從擁有該資源的 `shared_ptr` 物件建構，  
  
-   如果它是從指向該資源的 [weak\_ptr 類別](../standard-library/weak-ptr-class.md) 物件建構，或  
  
-   如果該資源的擁有權指派給它，不論是藉由 [shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md) 或藉由呼叫成員函式 [shared\_ptr::reset](../Topic/shared_ptr::reset.md)。  
  
 擁有資源的 `shared_ptr` 物件也會共用控制區塊。  控制區塊會存放：  
  
-   擁有資源的 `shared_ptr` 物件數目、  
  
-   指向資源的 `weak_ptr` 物件數目、  
  
-   如果有的話，該資源的刪除者、  
  
-   如果有的話，控制區塊的自訂配置器。  
  
 使用 null 指標初始化的 `shared_ptr` 物件具有控制區塊，且不是空的。  在 `shared_ptr` 物件釋放資源之後，它不再擁有該資源。  在 `weak_ptr` 物件釋放資源之後，它不再指向該資源。  
  
 當擁有資源的 `shared_ptr` 物件數目變成零時，會藉由刪除資源或將資源的位址傳遞至刪除者來釋放資源，視原先建立資源擁有權的方式而定。  當擁有資源的 `shared_ptr` 物件數目為零，且指向該資源的 `weak_ptr`物件為零時，會使用控制區塊的自訂配置器來釋放控制區塊，如果有的話。  
  
 空的 `shared_ptr` 物件未擁有任何資源，也沒有控制區塊。  
  
 刪除者是具有成員函式 `operator()` 的函式物件。  它的類型必須是可複製建構，且其複製建構函式和解構函式不能擲回例外狀況。  它接受一個參數，也就是要刪除的物件。  
  
 有些函式接受引數清單，其中定義所產生之 `shared_ptr<Ty>` 或 `weak_ptr<Ty>` 物件的內容。  您可以透過數種方法指定這類引數清單：  
  
 無引數 \-\- 產生的物件是空白的 `shared_ptr` 物件或是空白的 `weak_ptr` 物件。  
  
 `ptr` \-\- `Other*` 類型的待管理資源指標。  `Ty` 必須是完整的類型。  如果函式失敗 \(因為無法配置控制區塊\)，它會評估運算式 `delete ptr`。  
  
 `ptr, dtor` \-\- `Other*` 類型的待管理資源指源，以及該資源的刪除者。  如果函式失敗 \(因為無法配置控制區塊\)，它會呼叫 `dtor(ptr)`，這必須妥善定義。  
  
 `ptr, dtor, alloc` \-\- `Other*` 類型的待管理資源指標、該資源的刪除者，以及管理任何必須配置和釋放之儲存體的配置器。  如果函式失敗 \(因為無法配置控制區塊\)，它會呼叫 `dtor(ptr)`，這必須妥善定義。  
  
 `sp` \-\- 擁有待管理資源的 `shared_ptr<Other>` 物件。  
  
 `wp` \-\- 指向待管理資源的 `weak_ptr<Other>` 物件。  
  
 `ap` \-\- 存放待管理資源指標的 `auto_ptr<Other>` 物件。  如果函式成功，它會呼叫 `ap.release()`；否則它會維持 `ap` 不變。  
  
 在所有情況下，指標類型 `Other*` 必須可轉換為 `Ty*`。  
  
## 執行緒安全  
 多個執行緒可以同時讀取和寫入不同的 `shared_ptr` 物件，即使物件是共用擁有權的複本時也是一樣。  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[shared\_ptr::shared\_ptr](../Topic/shared_ptr::shared_ptr.md)|建構 `shared_ptr`。|  
|[shared\_ptr::~shared\_ptr](../Topic/shared_ptr::~shared_ptr.md)|終結 `shared_ptr`。|  
  
### 方法  
  
|||  
|-|-|  
|[shared\_ptr::element\_type](../Topic/shared_ptr::element_type.md)|項目的類型。|  
|[shared\_ptr::get](../Topic/shared_ptr::get.md)|取得擁有的資源位址。|  
|[shared\_ptr::owner\_before](../Topic/shared_ptr::owner_before.md)|如果這個 `shared_ptr` 排序在所提供的指標之前 \(或小於\)，則傳回 true。|  
|[shared\_ptr::reset](../Topic/shared_ptr::reset.md)|取代所擁有的資源。|  
|[shared\_ptr::swap](../Topic/shared_ptr::swap.md)|交換兩個 `shared_ptr` 物件。|  
|[shared\_ptr::unique](../Topic/shared_ptr::unique.md)|測試擁有的資源是否唯一。|  
|[shared\_ptr::use\_count](../Topic/shared_ptr::use_count.md)|計算資源擁有者的數目。|  
  
### 運算子  
  
|||  
|-|-|  
|[shared\_ptr::operator boolean\-type](../Topic/shared_ptr::operator%20boolean-type.md)|測試擁有的資源是否存在。|  
|[shared\_ptr::operator\*](../Topic/shared_ptr::operator*.md)|取得指定的值。|  
|[shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md)|取代所擁有的資源。|  
|[shared\_ptr::operator\-\>](../Topic/shared_ptr::operator-%3E.md)|取得指定值的指標。|  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [weak\_ptr 類別](../standard-library/weak-ptr-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)