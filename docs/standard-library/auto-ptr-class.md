---
title: "auto_ptr 類別 | Microsoft Docs"
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
  - "std::auto_ptr"
  - "std.auto_ptr"
  - "auto_ptr"
  - "memory/std::auto_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_ptr 類別"
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
caps.latest.revision: 26
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# auto_ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以智慧型指標包裝資源，確保當控制離開區塊時，會自動終結該資源。  
  
 更適用的 `unique_ptr` 類別會取代 `auto_ptr`。  如需詳細資訊，請參閱 [unique\_ptr 類別](../standard-library/unique-ptr-class.md)。  
  
 如需 `throw()` 和例外狀況處理的詳細資訊，請參閱[例外狀況規格 \(throw\)](../cpp/exception-specifications-throw-cpp.md)。  
  
## 語法  
  
```  
template<class Type>  
    class auto_ptr {  
public:  
    typedef Type element_type;  
    explicit auto_ptr(Type *_Ptr = 0) throw();  
    auto_ptr(auto_ptr<Type>& _Right) throw();  
    template<class Other>  
        operator auto_ptr<Other>() throw();  
    template<class Other>  
        auto_ptr<Type>& operator=(auto_ptr<Other>& _Right) throw();  
    template<class Other>  
        auto_ptr(auto_ptr<Other>& _Right);  
    auto_ptr<Type>& operator=(auto_ptr<Type>& _Right);  
    ~auto_ptr();  
    Type& operator*() const throw();  
    Type *operator->()const throw();  
    Type *get() const throw();  
    Type *release()throw();  
    void reset(Type *_Ptr = 0);  
};  
```  
  
#### 參數  
 `_Right`  
 要從中取得現有資源的 `auto_ptr`。  
  
 `_Ptr`  
 此指標指定了要取代的已儲存指標。  
  
## 備註  
 這個樣板類別描述一個智慧型指標，可對配置物件呼叫 `auto_ptr,`。  這個指標必須是 null，或指定 `new` 所配置的物件。  如果將 `auto_ptr` 的儲存值指派給另一個物件，則會轉移擁有權。  \(轉移後，會以 null 指標取代儲存值。\) `auto_ptr<Type>` 的解構函式會刪除配置物件。  `auto_ptr<Type>` 可確保當控制離開區塊時 \(即使是透過擲回例外狀況\)，會自動刪除配置物件。  您不應該建構兩個擁有相同物件的 `auto_ptr<Type>` 物件。  
  
 您可以將 `auto_ptr<Type>` 物件當做函式呼叫的引數，以傳值方式來傳遞。  `auto_ptr` 不能是任何標準程式庫容器的項目。  您無法透過標準範本程式庫容器可靠地管理 `auto_ptr<Type>` 物件序列。  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[auto\_ptr](../Topic/auto_ptr::auto_ptr.md)|`auto_ptr` 類型物件的建構函式。|  
  
### Typedefs  
  
|||  
|-|-|  
|[element\_type](../Topic/auto_ptr::element_type.md)|這個類型與範本參數 `Type` 同義。|  
  
### 成員函式  
  
|||  
|-|-|  
|[取得](../Topic/auto_ptr::get.md)|這個成員函式會傳回儲存的指標 `myptr`。|  
|[發行](../Topic/auto_ptr::release.md)|這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。|  
|[重設](../Topic/auto_ptr::reset.md)|這個成員函式只有在儲存的指標值 `myptr` 因函式呼叫而變更時，才會評估運算式 `delete myptr`。  然後會以 `ptr` 取代儲存的指標。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/auto_ptr::operator=.md)|指派運算子，將擁有權從一個 `auto_ptr` 物件轉移至另一個物件。|  
|[operator\*](../Topic/auto_ptr::operator*.md)|`auto_ptr` 類型物件的取值運算子。|  
|[operator\-\>](../Topic/auto_ptr::operator-%3E.md)|允許成員存取的運算子。|  
|[operator auto\_ptr\<Other\>](../Topic/auto_ptr::operator%20auto_ptr%3COther%3E.md)|從一種 `auto_ptr` 轉換成另一種 `auto_ptr`。|  
|[operator auto\_ptr\_ref\<Other\>](../Topic/auto_ptr::operator%20auto_ptr_ref%3COther%3E.md)|從 `auto_ptr` 轉換成 `auto_ptr_ref`。|  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [unique\_ptr 類別](../standard-library/unique-ptr-class.md)