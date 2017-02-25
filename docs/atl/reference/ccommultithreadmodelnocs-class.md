---
title: "CComMultiThreadModelNoCS Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComMultiThreadModelNoCS"
  - "CComMultiThreadModelNoCS"
  - "ATL.CComMultiThreadModelNoCS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 多執行緒"
  - "CComMultiThreadModelNoCS class"
  - "執行緒 [ATL]"
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CComMultiThreadModelNoCS Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModelNoCS` 為遞增和遞減變數的值會提供執行緒安全，方法，而不使用鎖定或解除鎖定功能的關鍵區段。  
  
## 語法  
  
```  
  
class CComMultiThreadModelNoCS  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](../Topic/CComMultiThreadModelNoCS::AutoCriticalSection.md)|參考類別 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](../Topic/CComMultiThreadModelNoCS::CriticalSection.md)|參考類別 `CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](../Topic/CComMultiThreadModelNoCS::ThreadModelNoCS.md)|參考類別 `CComMultiThreadModelNoCS`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComMultiThreadModelNoCS::Decrement](../Topic/CComMultiThreadModelNoCS::Decrement.md)|\(靜態\) 會指定變數的值以安全執行緒方法。|  
|[CComMultiThreadModelNoCS::Increment](../Topic/CComMultiThreadModelNoCS::Increment.md)|\(靜態\) 將指定變數的值以安全執行緒方法。|  
  
## 備註  
 `CComMultiThreadModelNoCS` 類似 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 因為遞增和遞減變數提供執行緒安全的方法。  不過，在中，當您將 `CComMultiThreadModelNoCS`參考關鍵區段類別，方法就像 `Lock` 和 `Unlock` 不會執行任何動作。  
  
 一般而言，您會 `ThreadModelNoCS``typedef` 名稱使用 `CComMultiThreadModelNoCS` 。  這 `typedef` 在 `CComMultiThreadModelNoCS`、 `CComMultiThreadModel`和 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)中定義。  
  
> [!NOTE]
>  全域 `typedef` 名稱 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 和 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) 不參考 `CComMultiThreadModelNoCS`。  
  
 除了 `ThreadModelNoCS`之外， `CComMultiThreadModelNoCS` 定義 `AutoCriticalSection` 和 `CriticalSection`。  後者這兩個 `typedef` 名稱參考 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供空的方法與取得及釋放關鍵區段。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)