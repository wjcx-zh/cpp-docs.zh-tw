---
title: "Map::MapChanged 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::MapChanged"
ms.assetid: d14b5b93-36ff-47a5-b588-dd1dc6ea4364
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::MapChanged 事件
在對應中插入或移除項目時引發。  
  
## 語法  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
## 屬性值\/傳回值  
 [MapChangedEventHandler\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br206644.aspx)，包含引發事件之物件以及發生之變更類型的資訊。 另請參閱 [IMapChangedEventArgs\<K\>](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) 和 [CollectionChange 列舉](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx)。  
  
## .NET Framework 對等用法  
 使用 C\# 或 Visual Basic 專案 IMap\<K,V\> 做為 IDictionary\<K,V\> 的 Windows 市集應用程式。  
  
## 需求  
 Windows 8.0 \(含\) 以上版本  
  
## 請參閱  
 [集合](../cppcx/collections-c-cx.md)