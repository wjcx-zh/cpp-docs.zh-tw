---
title: "UnorderedMap::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::First"
ms.assetid: 915e771a-cec1-4905-8ecb-76501f63c143
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::First 方法
傳回迭代器，它會指定未排序對應中的第一個 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) 項目。  
  
## 語法  
  
```cpp  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
## 傳回值  
 迭代器，指定對應中的第一個元素。  
  
## 備註  
 若要保留 First\(\) 所傳回的迭代器，為使用 [auto](~/cpp/auto-cpp.md) 型别推斷關鍵字進行宣告的變數指派傳回值，是很方便的方式。 例如，`auto x = myUnorderedMap->First();`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMap 類別](../cppcx/platform-collections-unorderedmap-class.md)   
 [集合](../cppcx/collections-c-cx.md)