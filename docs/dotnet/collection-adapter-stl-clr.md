---
title: "collection_adapter (STL/CLR) | Microsoft Docs"
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
  - "cliext::collection_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collection_adapter 類別 [STL/CLR]"
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# collection_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝 .NET 集合做為 STL\/CLR 容器。  `collection_adapter` 是一簡單的 STL\/CLR 容器物件的樣板類別。  它包裝基底類別程式庫 \(BCL\) 介面，並傳回用來操作受控制序列的一個迭代器 。  
  
## 語法  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### 參數  
 Coll  
 集合的包裝型別。  
  
## 特製化  
  
|特製化|說明|  
|---------|--------|  
|IEnumerable|序列傳遞項目。|  
|ICollection|維護一組項目。|  
|IList|維護項目的有序群組。|  
|IDictionary|維護一組 {索引碼, 值}。|  
|IEnumerable\<Value\>|序列傳遞型別項目。|  
|ICollection\<Value\>|維護型別項目的群組。|  
|IList\<Value\>|維護類型項目的有序群組。|  
|IDictionary\<Value\>|維護一組型別{索引碼, 值}。|  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[collection\_adapter::difference\_type](../dotnet/collection-adapter-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[collection\_adapter::iterator](../dotnet/collection-adapter-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[collection\_adapter::key\_type](../dotnet/collection-adapter-key-type-stl-clr.md)|字典索引鍵的型別。|  
|[collection\_adapter::mapped\_type](../dotnet/collection-adapter-mapped-type-stl-clr.md)|字典值的型別。|  
|[collection\_adapter::reference](../dotnet/collection-adapter-reference-stl-clr.md)|項目的參考類型。|  
|[collection\_adapter::size\_type](../dotnet/collection-adapter-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[collection\_adapter::value\_type](../dotnet/collection-adapter-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[collection\_adapter::base](../dotnet/collection-adapter-base-stl-clr.md)|指定要包裝的 BCL 介面。|  
|[collection\_adapter::begin](../dotnet/collection-adapter-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[collection\_adapter::collection\_adapter](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|建構配接器物件。|  
|[collection\_adapter::end](../dotnet/collection-adapter-end-stl-clr.md)|指定受控制序列的結尾。|  
|[collection\_adapter::size](../dotnet/collection-adapter-size-stl-clr.md)|計數項目的數目。|  
|[collection\_adapter::swap](../dotnet/collection-adapter-swap-stl-clr.md)|交換兩個容器的內容。|  
  
|運算子|說明|  
|---------|--------|  
|[collection\_adapter::operator\=](../dotnet/collection-adapter-operator-assign-stl-clr.md)|取代儲存的 BCL 控制代碼。|  
  
## 備註  
 您可以使用這個範本類別操作 BCL 容器做為 STL\/CLR 容器。  儲存 `collection_adapter` 控制代碼 BCL 介面，進而控制項目序列。  `collection_adapter` 物件的 `X` 傳回一組輸入 Iterator 您使用瀏覽項目的 `X.begin()` 和 `X.end()` 順序。  部分特製化也可讓您寫入 `X.size()` 判斷受控制序列的長度。  
  
## 需求  
 **標頭：** \<cliext\/adapter\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)