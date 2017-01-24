---
title: "weak_ptr 類別 | Microsoft Docs"
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
  - "std.tr1.weak_ptr"
  - "tr1.weak_ptr"
  - "weak_ptr"
  - "tr1::weak_ptr"
  - "std::tr1::weak_ptr"
  - "memory/std::tr1::weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "weak_ptr 類別"
  - "weak_ptr 類別 [TR1]"
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# weak_ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝弱式連結的指標。  
  
## 語法  
  
```  
template<class Ty> class weak_ptr {  
public:  
    typedef Ty element_type;  
  
    weak_ptr();  
    weak_ptr(const weak_ptr&);  
    template<class Other>  
        weak_ptr(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr(const shared_ptr<Other>&);  
  
    weak_ptr& operator=(const weak_ptr&);  
    template<class Other>  
        weak_ptr& operator=(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr& operator=(shared_ptr<Other>&);  
  
    void swap(weak_ptr&);  
    void reset();  
  
    long use_count() const;  
    bool expired() const;  
    shared_ptr<Ty> lock() const;  
    };  
```  
  
#### 參數  
 `Ty`  
 弱式指標所控制的類型。  
  
## 備註  
 此範本類別描述的物件，指向由一或多個 [shared\_ptr 類別](../standard-library/shared-ptr-class.md) 物件管理的資源。  指向資源的 `weak_ptr` 物件不會影響資源的參考計數。  因此，當最後一個管理該資源的 `shared_ptr` 物件終結時，將會釋放該資源，即使仍有指向該資源的 `weak_ptr` 物件。  為了避免資料結構中的循環，這是不可或缺的。  
  
 如果 `weak_ptr` 物件由擁有該資源的 `shared_ptr` 物件所建構，或是如果它由指向該資源的 `weak_ptr` 物件所建構，或如果該資源已藉由 [weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md) 指派給它，則會指向該資源。  `weak_ptr` 物件不提供對它所指向資源的直接存取。  需要使用此資源的程式碼會藉由擁有該資源的 `shared_ptr` 物件如此執行，且該物件藉由呼叫成員函式 [weak\_ptr::lock](../Topic/weak_ptr::lock.md) 所建立。  當 `weak_ptr` 物件指向的資源已釋放後，此物件就會到期，因為擁有此資源的所有 `shared_ptr` 物件已被終結。  呼叫已到期 `weak_ptr` 物件上的 `lock`會建立空的 shared\_ptr 物件。  
  
 空的 weak\_ptr 物件未指向任何資源，也沒有控制區塊。  其成員函式 `lock` 會傳回空的 shared\_ptr 物件。  
  
 當由 `shared_ptr` 物件控制的兩個或多個資源保留對 `shared_ptr` 物件的交互參考時，就會發生循環。  例如，一個具有三個項目的循環連結清單會有前端節點 `N0`；該節點保留擁有下一個節點 \(`N1`\) 的 `shared_ptr` 物件；而保留 `shared_ptr` 物件的該節點又擁有下一個節點 \(`N2`\)；該節點會依序保留擁有前端節點 \(`N0`\) 的 `shared_ptr` 物件，並關閉此循環。  在此情況下，沒有任何參考計數會變成零，也不會釋放這個循環中的節點。  若要消除循環，則最後一個節點 `N2` 應該保留指向 `N0` 的 `weak_ptr` 物件，而不是 `shared_ptr` 物件。  因為 `weak_ptr` 物件並未擁有 `N0`，所以並不會影響 `N0` 的參考計數，而且當此程式最後一個對前端節點的參考被終結時，此清單中的節點也將被終結。  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[weak\_ptr::weak\_ptr](../Topic/weak_ptr::weak_ptr.md)|建構 `weak_ptr`。|  
  
### 方法  
  
|||  
|-|-|  
|[weak\_ptr::element\_type](../Topic/weak_ptr::element_type.md)|項目的類型。|  
|[weak\_ptr::expired](../Topic/weak_ptr::expired.md)|測試擁有權是否已到期。|  
|[weak\_ptr::lock](../Topic/weak_ptr::lock.md)|取得資源的獨佔擁有權。|  
|[weak\_ptr::owner\_before](../Topic/weak_ptr::owner_before.md)|如果這個 `weak_ptr` 排序在所提供的指標之前 \(或小於\)，則傳回 `true`。|  
|[weak\_ptr::reset](../Topic/weak_ptr::reset.md)|釋放所擁有的資源。|  
|[weak\_ptr::swap](../Topic/weak_ptr::swap.md)|交換兩個 `weak_ptr` 物件。|  
|[weak\_ptr::use\_count](../Topic/weak_ptr::use_count.md)|指定之 `shared_ptr` 物件的計數數目。|  
  
### 運算子  
  
|||  
|-|-|  
|[weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md)|取代所擁有的資源。|  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [shared\_ptr 類別](../standard-library/shared-ptr-class.md)