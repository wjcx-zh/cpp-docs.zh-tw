---
title: "Platform::Collections::UnorderedMapView 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView"
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::Collections::UnorderedMapView 類別
表示*對應 \(Map\)* \(機碼值組的集合\) 的唯讀檢視。  
  
## 語法  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>  
>  
ref class UnorderedMapView sealed;  
```  
  
#### 參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 可提供函式物件用來比較兩個機碼值是否相等的類型。 預設是 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
## 備註  
 UnorderedMapView 是在應用程式二進位介面 \(ABI\) 之間傳遞之 [Windows::Foundation::Collections::IMapView\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262409) 介面的具象 C\+\+ 實作。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[UnorderedMapView::UnorderedMapView 建構函式](../cppcx/unorderedmapview-unorderedmapview-constructor.md)|初始化 UnorderedMapView 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[UnorderedMapView::First 方法](../cppcx/unorderedmapview-first-method.md)|傳回迭代器，初始化為對應檢視中的第一個元素。|  
|[UnorderedMapView::HasKey 方法](../cppcx/unorderedmapview-haskey-method.md)|判斷目前 UnorderedMapView 是否包含指定的機碼。|  
|[UnorderedMapView::Lookup 方法](../cppcx/unorderedmapview-lookup-method.md)|取得目前 UnorderedMapView 物件中，所指定機碼處的項目。|  
|[UnorderedMapView::Size 方法](../cppcx/unorderedmapview-size-method.md)|傳回目前 UnorderedMapView 物件中的元素數目。|  
|[UnorderedMapView::Split 方法](../cppcx/unorderedmapview-split-method.md)|將原始 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。|  
  
## 繼承階層  
 `UnorderedMapView`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](http://go.microsoft.com/fwlink/p/?LinkId=262409)