---
title: "CComSingleThreadModel Class | Microsoft Docs"
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
  - "ATL.CComSingleThreadModel"
  - "CComSingleThreadModel"
  - "ATL::CComSingleThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSingleThreadModel class"
  - "single-threaded applications"
  - "single-threaded applications, ATL"
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSingleThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供遞增和遞減變數值的方法。  
  
## 語法  
  
```  
  
class CComSingleThreadModel  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CComSingleThreadModel::AutoCriticalSection](../Topic/CComSingleThreadModel::AutoCriticalSection.md)|參考類別 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComSingleThreadModel::CriticalSection](../Topic/CComSingleThreadModel::CriticalSection.md)|參考類別 `CComFakeCriticalSection`。|  
|[CComSingleThreadModel::ThreadModelNoCS](../Topic/CComSingleThreadModel::ThreadModelNoCS.md)|參考 `CComSingleThreadModel`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComSingleThreadModel::Decrement](../Topic/CComSingleThreadModel::Decrement.md)|遞減特定變數的值。  這個實作不具備執行緒安全。|  
|[CComSingleThreadModel::Increment](../Topic/CComSingleThreadModel::Increment.md)|將指定的變數值。  這個實作不具備執行緒安全。|  
  
## 備註  
 `CComSingleThreadModel` 為遞增和遞減變數值的方法。  不同於 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 和 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這些方法不具備執行緒安全。  
  
 通常，您會將兩個 `typedef` 名稱\] 使用 `CComSingleThreadModel` ， [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  每個 `typedef` 參考的類別取決於執行緒模型使用，如下表所示:  
  
|typedef|單一執行緒模型|Apartment 執行緒模型|無限制執行緒模型|  
|-------------|-------------|---------------------|--------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S\=`CComSingleThreadModel`;M\=`CComMultiThreadModel`  
  
 `CComSingleThreadModel` 定義三個 `typedef` 名稱。  `ThreadModelNoCS` 參考 `CComSingleThreadModel`。  `AutoCriticalSection` 和 `CriticalSection` 參考將 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供空的方法與取得和釋放關鍵區段的擁有權。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)