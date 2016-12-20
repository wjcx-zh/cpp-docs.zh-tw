---
title: "reference_wrapper 類別 | Microsoft Docs"
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
  - "std.tr1.reference_wrapper"
  - "tr1.reference_wrapper"
  - "reference_wrapper"
  - "tr1::reference_wrapper"
  - "xrefwrap/std::tr1::reference_wrapper"
  - "std::tr1::reference_wrapper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference_wrapper 類別"
  - "reference_wrapper 類別 [TR1]"
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# reference_wrapper 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝一個參考。  
  
## 語法  
  
```  
template<class Ty>  
    class reference_wrapper  
    : public unary_function<T1, Ret>        // see below  
    : public binary_function<T1, T2, Ret>   // see below  
    {  
public:  
    typedef Ty type;  
    typedef T0 result_type;                 // see below  
  
    reference_wrapper(Ty&);  
  
    Ty& get() const;  
    operator Ty&() const;  
    template<class T1, class T2, ..., class TN>  
        typename result_of<T(T1, T2, ..., TN)>::type  
        operator()(T1&, T2&, ..., TN&);  
  
private:  
    Ty *ptr; // exposition only  
    };  
```  
  
## 備註  
 `reference_wrapper<Ty>` 可複製建構和指派，並保留指向 `Ty` 類型物件的指標。  
  
 只有 `Ty` 類型為下列其中一項，特製化 `reference_wrapper<Ty>` 才能衍生自 `std::unary_function<T1, Ret>` \(進而定義巢狀類型 `result_type` 與 `Ret` 同義，而巢狀類型 `argument_type` 與 `T1` 同義\)：  
  
 接受一個 `T1` 類型引數並傳回 `Ret` 的函式類型或函式類型指標；或  
  
 成員函式 `Ret T::f() cv` 的指標，其中 `cv` 代表成員函式的 cv 限定詞，`T1` 類型為 `cv` `T*`；或  
  
 衍生自 `unary_function<T1, Ret>` 的類別類型。  
  
 只有 `Ty` 類型為下列其中一項，特製化 `reference_wrapper<Ty>` 才能衍生自 `std::binary_function<T1, T2, Ret>` \(進而定義巢狀類型 `result_type` 與 `Ret` 同義、巢狀類型 `first_argument_type` 與 `T1` 同義，而巢狀類型 `second_argument_type` 與 `T2` 同義\)：  
  
 接受 `T1` 和 `T2` 類型的兩個引數並傳回 `Ret` 的函式類型或函式類型指標；或  
  
 成員函式 `Ret T::f(T2) cv` 的指標，其中 `cv` 代表成員函式的 cv 限定詞，`T1` 類型為 `cv` `T*`；或  
  
 衍生自 `binary_function<T1, T2, Ret>` 的類別類型。  
  
### 建構函式  
  
|||  
|-|-|  
|[reference\_wrapper::reference\_wrapper](../Topic/reference_wrapper::reference_wrapper.md)|建構 `reference_wrapper`。|  
  
### Typedefs  
  
|||  
|-|-|  
|[reference\_wrapper::result\_type](../Topic/reference_wrapper::result_type.md)|包裝之參考的弱式結果類型。|  
|[reference\_wrapper::type](../Topic/reference_wrapper::type.md)|包裝的參考類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[reference\_wrapper::get](../Topic/reference_wrapper::get.md)|取得包裝的參考。|  
  
### 運算子  
  
|||  
|-|-|  
|[reference\_wrapper::operator Ty&](../Topic/reference_wrapper::operator%20Ty&.md)|取得包裝的參考指標。|  
|[reference\_wrapper::operator\(\)](../Topic/reference_wrapper::operator\(\).md)|呼叫包裝的參考。|  
  
## 需求  
 **標頭：**\<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [cref 函式](../Topic/cref%20Function.md)   
 [ref 函式](../Topic/ref%20Function.md)