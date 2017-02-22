---
title: "enable_shared_from_this 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1.enable_shared_from_this"
  - "enable_shared_from_this"
  - "std.tr1.enable_shared_from_this"
  - "memory/std::tr1::enable_shared_from_this"
  - "std::tr1::enable_shared_from_this"
  - "tr1::enable_shared_from_this"
  - "std.enable_shared_from_this"
  - "memory/std::enable_shared_from_this"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enable_shared_from_this 類別"
  - "enable_shared_from_this 類別 [TR1]"
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# enable_shared_from_this 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

幫助產生 `shared_ptr`。  
  
## 語法  
  
```  
template<class Ty>  
    class enable_shared_from_this {  
public:  
    shared_ptr<Ty> shared_from_this();  
    shared_ptr<const Ty> shared_from_this() const;  
  
protected:  
    enable_shared_from_this();  
    enable_shared_from_this(const enable_shared_from_this&);  
    enable_shared_from_this& operator=(const enable_shared_from_this&);  
    ~enable_shared_from_this();  
    };  
```  
  
#### 參數  
 `Ty`  
 共用指標所控制的類型。  
  
## 備註  
 物件衍生自 `enable_shared_from_this` 可以使用 `shared_from_this` 方法在成員函式來建立 [shared\_ptr](../standard-library/shared-ptr-class.md) 與現有的共用擁有權的執行個體擁有者 `shared_ptr` 擁有者。 否則，如果您建立新 `shared_ptr` 使用 `this`, ，它是不同於現有 `shared_ptr` 擁有者，可能會導致無效的參考，或造成超過一次刪除的物件。  
  
 建構函式、 解構函式和指派運算子會受到保護以防止意外誤用。 範本引數型別 `Ty` 必須是在衍生類別的型別。  
  
 如需使用方式的範例，請參閱 [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md)。  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md)   
 [shared\_ptr 類別](../standard-library/shared-ptr-class.md)