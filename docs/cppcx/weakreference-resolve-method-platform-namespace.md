---
title: "WeakReference::Resolve 方法 (Platform 命名空間) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::Resolve"
ms.assetid: 78bbcadd-89d0-4863-a4e8-1d84040eed7d
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::Resolve 方法 (Platform 命名空間)
傳回原始 ref 類別的控制代碼。如果物件已不存在則傳回 `nullptr`。  
  
## 語法  
  
```vb  
  
template<typename T>  
T^ Resolve() const  
```  
  
#### 參數  
  
## 屬性值\/傳回值  
 之前與 WeakReference 物件相關聯之 ref 類別的控制代碼，或者是 nullptr。  
  
## 備註  
  
## 範例  
 這是程式碼範例說明。  
  
```  
  
Bar^ bar = ref new Bar(); //use bar... if (bar != nullptr) { WeakReference wr(bar); Bar^ newReference = wr.Resolve<Bar>(); }  
```  
  
 請注意，類型參數是 T 而非 T^。  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)