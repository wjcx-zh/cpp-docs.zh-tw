---
title: "Platform::Collections::VectorView 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView 類別"
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Platform::Collections::VectorView 類別
代表物件之循序集合的唯讀檢視，這些物件可透過索引加以個別存取。 集合中每個物件的類型，由樣板參數指定。  
  
## 語法  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### 參數  
 `T`  
 `VectorView` 物件中包含的元素類型。  
  
 `E`  
 指定二元述詞，以測試是否與 `T` 型別的值相等。 預設值是 `std::equal_to<T>`。  
  
## 備註  
 `VectorView` 類別實作 [Windows::Foundation::Collections::IVectorView\<T\>](http://go.microsoft.com/fwlink/p/?LinkId=262411) 介面，也支援標準樣板程式庫迭代器。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[VectorView::VectorView 建構函式](../cppcx/vectorview-vectorview-constructor.md)|初始化 VectorView 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[VectorView::First 方法](../cppcx/vectorview-first-method.md)|傳回迭代器，指定 VectorView 中的第一個項目。|  
|[VectorView::GetAt 方法](../cppcx/vectorview-getat-method.md)|擷取由指定之索引所表示的目前 VectorView 項目。|  
|[VectorView::GetMany 方法](../cppcx/vectorview-getmany-method.md)|由指定的索引處開始，從目前 VectorView 擷取一連串項目。|  
|[VectorView::IndexOf 方法](../cppcx/vectorview-indexof-method.md)|在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。|  
|[VectorView::Size 方法](../cppcx/vectorview-size-method.md)|傳回目前 VectorView 物件中的項目數。|  
  
## 繼承階層  
 `VectorView`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [在 C\+\+ 中建立 Windows 執行階段元件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)