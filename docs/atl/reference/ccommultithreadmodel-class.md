---
title: "CComMultiThreadModel Class | Microsoft Docs"
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
  - "CComMultiThreadModel"
  - "ATL.CComMultiThreadModel"
  - "ATL::CComMultiThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 多執行緒"
  - "CComMultiThreadModel class"
  - "執行緒 [ATL]"
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 21
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComMultiThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModel` 為遞增和遞減變數的值會提供執行緒安全的方法。  
  
## 語法  
  
```  
  
class CComMultiThreadModel  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)|參考類別 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|  
|[CComMultiThreadModel::CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)|參考類別 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|  
|[CComMultiThreadModel::ThreadModelNoCS](../Topic/CComMultiThreadModel::ThreadModelNoCS.md)|參考類別 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComMultiThreadModel::Decrement](../Topic/CComMultiThreadModel::Decrement.md)|\(靜態\) 會指定變數的值以安全執行緒方法。|  
|[CComMultiThreadModel::Increment](../Topic/CComMultiThreadModel::Increment.md)|\(靜態\) 將指定變數的值以安全執行緒方法。|  
  
## 備註  
 通常，您會將兩個 `typedef` 名稱\] 使用 `CComMultiThreadModel` ， [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  每個 `typedef` 參考的類別取決於執行緒模型使用，如下表所示:  
  
|typedef|單一執行緒|Apartment 執行緒|無限制執行緒|  
|-------------|-----------|-------------------|------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S\=`CComSingleThreadModel`;M\=`CComMultiThreadModel`  
  
 `CComMultiThreadModel` 定義三個 `typedef` 名稱。  `AutoCriticalSection` 和 `CriticalSection` 參考才能取得和釋放關鍵區段的擁有權提供方法的類別。  `ThreadModelNoCS` 參考類別 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CComSingleThreadModel Class](../../atl/reference/ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)