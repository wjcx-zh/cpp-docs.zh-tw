---
title: "Platform::Collections::MapView 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView 類別"
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Collections::MapView 類別
表示*對應 \(Map\)* \(機碼值組的集合\) 的唯讀檢視。  
  
## 語法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>  
>  
ref class MapView sealed;  
```  
  
#### 參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 一個類型，提供函式物件，可以根據排序鍵比較兩個項目值，以判斷它們在 MapView 中的相對順序。 預設為 [::std::less\<K\>](../standard-library/less-struct.md)。  
  
## 備註  
 MapView 是在應用程式二進位介面 \(ABI\) 之間傳遞之 [Windows::Foundation::Collections::IMapView \<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262409) 介面的具象 C\+\+ 實作。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[MapView::MapView 建構函式](../cppcx/mapview-mapview-constructor.md)|初始化 MapView 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[MapView::First 方法](../cppcx/mapview-first-method.md)|傳回迭代器，初始化為對應檢視中的第一個元素。|  
|[MapView::HasKey 方法](../cppcx/mapview-haskey-method.md)|判斷目前 MapView 是否包含指定的機碼。|  
|[MapView::Lookup 方法](../cppcx/mapview-lookup-method.md)|在目前 MapView 物件中擷取位於指定機碼的元素。|  
|[MapView::Size 方法](../cppcx/mapview-size-method.md)|傳回目前 MapView 物件中的項目數。|  
|[MapView::Split 方法](../cppcx/mapview-split-method.md)|將原始 MapView 物件分割為兩個 MapView 物件。|  
  
## 繼承階層  
 `MapView`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)