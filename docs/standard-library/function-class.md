---
title: "function 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "functional/std::tr1::function"
  - "std.tr1.function"
  - "std::tr1::function"
  - "function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "function 類別 [TR1]"
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# function 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可呼叫的物件的包裝函式。  
  
## 語法  
  
```cpp  
template<class Fty>  
   class function  // Fty of type Ret(T1, T2, ..., TN)  
   : public unary_function<T1, Ret>       // when Fty is Ret(T1)  
   : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)  
   {  
public:  
   typedef Ret result_type;  
  
   function();  
   function(nullptr_t);  
   function(const function& _Right);  
   template<class Fty2>  
      function(Fty2 fn);  
   template<class Fty2, class Alloc>  
       function (reference_wrapper<Fty2>, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       void assign (Fty2, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       assign (reference_wrapper<Fty2>, const Alloc& _Ax);  
```  
  
```cpp  
function& operator=(nullptr_t);  
function& operator=(const function&);  
template<class Fty2>  
   function& operator=(Fty2);  
template<class Fty2>  
   function& operator=(reference_wrapper<Fty2>);  
void swap(function&);  
  
explicit operator bool() const;  
result_type operator()(T1, T2, ....., TN) const;  
  
const std::type_info& target_type() const;  
template<class Fty2>  
   Fty2 *target();  
template<class Fty2>  
   const Fty2 *target() const;  
```  
  
```cpp  
   template<class Fty2>  
      void operator==(const Fty2&) const = delete;  
   template<class Fty2>  
      void operator!=(const Fty2&) const = delete;  
};  
```  
  
#### 參數  
 `Fty`  
 包裝函式的型別。  
  
 `_Ax`  
 配置器函式。  
  
## 備註  
 樣板類別是呼叫簽章是呼叫的 `Ret(T1, T2, ..., TN)`包裝函式。  您可以在一個一致的包裝函式使用以便各種可呼叫物件。  
  
 陣列成員函式採用命名所需目標物件的運算元。  您可以在幾個方式指定這類運算元:  
  
 `fn` \-\-可呼叫的 `fn`物件;在呼叫 `function` 物件來保存 `fn`後複製  
  
 `fnref` \-\-可對名為 `fnref.get()`;在呼叫 `function` 物件保留 `fnref.get()`後的參考  
  
 `right` \-\-可呼叫的物件，如果有的話，保留由 `function` 物件的 `right`。  
  
 `npc` \-\-Void 指標;在呼叫後 `function` 物件為 null  
  
 在所有情況下， `INVOKE(f, t1, t2, ..., tN)`， `f` 可呼叫之物件，而 `t1, t2, ..., tN` 分別為型別 `T1, T2, ..., TN` 的值，該值必須為語式正確，則為，如果 `Ret` 不是空的，轉換為 `Ret`。  
  
 空白的 `function` 物件不保留可呼叫的物件或參考可呼叫的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[function::function](../Topic/function::function.md)|建構包裝函式是 null 或儲存任意型別可呼叫的物件具有固定的簽章。|  
  
### Typedef  
  
|||  
|-|-|  
|[function::result\_type](../Topic/function::result_type.md)|儲存可呼叫物件的傳回型別。|  
  
### 成員函式  
  
|||  
|-|-|  
|[function::assign](../Topic/function::assign.md)|指派給這個函式物件的可呼叫的物件。|  
|[function::swap](../Topic/function::swap.md)|交換兩個可呼叫的物件。|  
|[function::target](../Topic/function::target.md)|測試，如果儲存的可呼叫的物件可由所指定。|  
|[function::target\_type](../Topic/function::target_type.md)|取得可呼叫之物件的型別資訊。|  
  
### 運算子  
  
|||  
|-|-|  
|[function::operator unspecified](../Topic/function::operator%20unspecified.md)|測試，如果儲存的可呼叫的物件存在。|  
|[function::operator\(\)](../Topic/function::operator\(\).md)|呼叫可呼叫的物件。|  
|[function::operator\=](../Topic/function::operator=.md)|取代儲存可呼叫的物件。|  
  
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [mem\_fn 函式](../Topic/mem_fn%20Function.md)   
 [reference\_wrapper 類別](../standard-library/reference-wrapper-class.md)