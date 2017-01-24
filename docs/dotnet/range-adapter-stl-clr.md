---
title: "range_adapter (STL/CLR) | Microsoft Docs"
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
  - "cliext::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter 類別 [STL/CLR]"
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

封裝一對迭代器 \(用來實作數個基底類別程式庫 \(BCL\) 介面\) 的樣板類別。  您可以使用 range\_adapter 操作 STL\/CLR 範圍，如同它是 BCL 集合一般。  
  
## 語法  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### 參數  
 Iter  
 與封裝的迭代器相關聯的型別。  
  
## 成員  
  
|成員函式|說明|  
|----------|--------|  
|[range\_adapter::range\_adapter](../dotnet/range-adapter-range-adapter-stl-clr.md)|建構配接器物件。|  
  
|運算子|說明|  
|---------|--------|  
|[range\_adapter::operator\=](../dotnet/range-adapter-operator-assign-stl-clr.md)|取代儲存的迭代器對。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.Collections.IEnumerable>|逐一查看集合中的項目。|  
|<xref:System.Collections.ICollection>|維護一組項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|逐一查看集合中的型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
  
## 備註  
 range\_adapter 儲存一組迭代器，其最後分隔一個項目序列。  物件實作四個 BCL 介面讓您可以順序的逐一查看項目。  您可以使用這個範本類別操作 STL\/CLR 範圍，如同操作 BCL 容器。  
  
## 需求  
 **標頭：** \<cliext\/adapter\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)