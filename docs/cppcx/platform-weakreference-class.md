---
title: "Platform::WeakReference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform::WeakReference"
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::WeakReference 類別
表示 ref 類別之執行個體的弱式參考。  
  
## 語法  
  
```vb  
class WeakReference  
```  
  
#### 參數  
  
## Members  
  
### 建構函式  
  
|成員|描述|  
|--------|--------|  
|[WeakReference::WeakReference 建構函式](../cppcx/weakreference-weakreference-constructor-c-cx.md)|初始化 WeakReference 類別的新執行個體。|  
  
### 方法  
  
|成員|描述|  
|--------|--------|  
|[WeakReference::Resolve 方法](../cppcx/weakreference-resolve-method-platform-namespace.md)|傳回基底 ref 類別的控制代碼。如果物件已不存在則傳回 nullptr。|  
  
### 運算子  
  
|成員|描述|  
|--------|--------|  
|[WeakReference::operator\=](../cppcx/weakreference-operator-assign.md)|指派新值給 WeakReference 物件。|  
  
## 備註  
 WeakReference 類別本身不是 ref 類別，因此不會繼承 Platform::Object^，而且也不能在公用方法的簽章中使用。  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)