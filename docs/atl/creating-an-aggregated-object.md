---
title: "Creating an Aggregated Object | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 建立"
  - "aggregation [C++], creating aggregated objects"
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating an Aggregated Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

彙總委派 **IUnknown** 呼叫，提供指標的外部物件的 **IUnknown** 給內部物件。  
  
### 建立彙總物件  
  
1.  將 **IUnknown** 指標至您的類別物件並將它初始化為在建構函式中 **NULL** 。  
  
2.  覆寫會建立彙總的 [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md) 。  
  
3.  使用 **IUnknown** 指標，會定義在步驟 1 中，做為第二個參數為 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md) 巨集。  
  
4.  覆寫釋放 **IUnknown** 指標的 [FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md) 。  
  
> [!NOTE]
>  在 `FinalConstruct`，如果您從彙總物件使用和發行一個介面，則您應該將 [DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md) 巨集加入至您的類別物件的定義。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)