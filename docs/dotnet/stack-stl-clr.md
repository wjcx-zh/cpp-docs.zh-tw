---
title: "stack (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/stack> 標頭 [STL/CLR]"
  - "<stack> 標頭 [STL/CLR]"
  - "stack 類別 [STL/CLR]"
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取後進先出項目的變更長度序列。  您使用容器配接器 `stack` 處理基礎容器做為下壓縮堆疊上。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  同樣地，`GContainer` 與 `Container` ，除非後面是參考型別，在這種情況下，它是 `Container^`的情況下  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
    { ..... };  
```  
  
#### 參數  
 值  
 受控制序列中項目的型別。  
  
 容器  
 基礎容器的型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[stack::const\_reference](../dotnet/stack-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[stack::container\_type](../dotnet/stack-container-type-stl-clr.md)|基礎容器的型別。|  
|[stack::difference\_type](../dotnet/stack-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)|泛型介面的型別的容器配接器。|  
|[stack::generic\_value](../dotnet/stack-generic-value-stl-clr.md)|容器適配器的泛型介面的元素的型別。|  
|[stack::reference](../dotnet/stack-reference-stl-clr.md)|項目的參考類型。|  
|[stack::size\_type](../dotnet/stack-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[stack::value\_type](../dotnet/stack-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[stack::assign](../dotnet/stack-assign-stl-clr.md)|取代所有項目。|  
|[stack::empty](../dotnet/stack-empty-stl-clr.md)|測試是否不存在項目。|  
|[stack::get\_container](../dotnet/stack-get-container-stl-clr.md)|存取基礎容器。|  
|[stack::pop](../dotnet/stack-pop-stl-clr.md)|移除最後一個項目。|  
|[stack::push](../dotnet/stack-push-stl-clr.md)|加入新的最後一個元素。|  
|[stack::size](../dotnet/stack-size-stl-clr.md)|計數項目的數目。|  
|[stack::stack](../dotnet/stack-stack-stl-clr.md)|建構一個容器物件。|  
|[stack::top](../dotnet/stack-top-stl-clr.md)|存取最後一個項目。|  
|[stack::to\_array](../dotnet/stack-to-array-stl-clr.md)|複製受控制序列至新陣列。|  
  
|屬性|說明|  
|--------|--------|  
|[stack::top\_item](../dotnet/stack-top-item-stl-clr.md)|存取最後一個項目。|  
  
|運算子|說明|  
|---------|--------|  
|[stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)|取代受控制序列。|  
|[operator\!\= \(stack\)](../dotnet/operator-inequality-stack-stl-clr.md)|判斷 `stack` 物件是否不等於另一個 `stack` 物件。|  
|[operator\< \(stack\)](../dotnet/operator-less-than-stack-stl-clr.md)|判斷 `stack` 物件是否小於另一個 `stack` 物件。|  
|[operator\<\= \(stack\)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|判斷 `stack` 物件是否小於或等於另外一個 `stack` 物件。|  
|[operator\=\= \(stack\)](../dotnet/operator-equality-stack-stl-clr.md)|判斷 `stack` 物件是否等於另一個 `stack` 物件。|  
|[operator\> \(stack\)](../dotnet/operator-greater-than-stack-stl-clr.md)|判斷 `stack` 物件是否大於另一個 `stack` 物件。|  
|[operator\>\= \(stack\)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|判斷 `stack` 物件是否大於或等於另外一個 `stack` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|複製物件。|  
|IStack\<Value, Container\>|維護泛型容器配接器。|  
  
## 備註  
 物件配置和未使用的記憶體區域透過基礎容器的序列，型別控制 `Container`，儲存 `Value` 項目並增加在要求時。  物件會限制對推入和移除最後一個項目的存取，實作後進先出的佇列 \(也稱為 LIFO 佇列或堆疊\)。  
  
## 需求  
 **標頭：** \<cliext\/stack\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)