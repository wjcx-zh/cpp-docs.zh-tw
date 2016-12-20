---
title: "queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> 標頭 [STL/CLR]"
  - "<queue> 標頭 [STL/CLR]"
  - "queue 類別 [STL/CLR]"
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取先進先出項目的變更長度序列。  您使用容器配接器 `queue` 處理基礎容器為佇列。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  同樣地，`GContainer` 與 `Container` ，除非後面是參考型別，在這種情況下，它是 `Container^`的情況下  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[queue::container\_type](../dotnet/queue-container-type-stl-clr.md)|基礎容器的型別。|  
|[queue::difference\_type](../dotnet/queue-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)|泛型介面的型別的容器配接器。|  
|[queue::generic\_value](../dotnet/queue-generic-value-stl-clr.md)|容器適配器的泛型介面的元素的型別。|  
|[queue::reference](../dotnet/queue-reference-stl-clr.md)|項目的參考類型。|  
|[queue::size\_type](../dotnet/queue-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[queue::value\_type](../dotnet/queue-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[queue::assign](../dotnet/queue-assign-stl-clr.md)|取代所有項目。|  
|[queue::back](../dotnet/queue-back-stl-clr.md)|存取最後一個項目。|  
|[queue::empty](../dotnet/queue-empty-stl-clr.md)|測試項目是否不存在。|  
|[queue::front](../dotnet/queue-front-stl-clr.md)|存取第一個項目。|  
|[queue::get\_container](../dotnet/queue-get-container-stl-clr.md)|存取基礎容器。|  
|[queue::pop](../dotnet/queue-pop-stl-clr.md)|移除第一個項目。|  
|[queue::push](../dotnet/queue-push-stl-clr.md)|加入新的最後一個元素。|  
|[queue::queue](../dotnet/queue-queue-stl-clr.md)|建構一個容器物件。|  
|[queue::size](../dotnet/queue-size-stl-clr.md)|計數項目的數目。|  
|[queue::to\_array](../dotnet/queue-to-array-stl-clr.md)|複製受控制序列到新陣列。|  
  
|屬性|說明|  
|--------|--------|  
|[queue::back\_item](../dotnet/queue-back-item-stl-clr.md)|存取最後一個項目。|  
|[queue::front\_item](../dotnet/queue-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|說明|  
|---------|--------|  
|[queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)|取代受控制序列。|  
|[operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)|判斷 `queue` 物件是否不等於另一個 `queue` 物件。|  
|[operator\< \(queue\)](../dotnet/operator-less-than-queue-stl-clr.md)|判斷 `queue` 物件是否小於另一個 `queue` 物件。|  
|[operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|判斷 `queue` 物件是否小於或等於另外一個 `queue` 物件。|  
|[operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)|判斷 `queue` 物件是否等於另一個 `queue` 物件。|  
|[operator\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)|判斷 `queue` 物件是否大於另一個 `queue` 物件。|  
|[operator\>\= \(queue\)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|判斷 `queue` 物件是否大於或等於另外一個 `queue` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|重複物件。|  
|IQueueValue\<，容器\>|維護泛型容器配接器。|  
  
## 備註  
 物件配置和未使用的記憶體區域透過基礎容器的序列，型別控制 `Container`，儲存 `Value` 項目並增加在要求時。  物件限制要推入至第一個項目並取出最後一個項目的存取，實作原本在初始佇列 \(也稱為 FIFO 佇列或只是佇列\)。  
  
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [堆疊](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)