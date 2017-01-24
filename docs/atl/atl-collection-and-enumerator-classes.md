---
title: "ATL Collection and Enumerator Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合類別, ATL"
  - "列舉程式, ATL 類別"
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Collection and Enumerator Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 提供下列類別提供協助您實作的集合和列舉值。  
  
|類別|描述|  
|--------|--------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合的介面實作。|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|列舉值介面實作 \(假設在 STL 相容的容器中的資料\)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|列舉值介面實作 \(假設在陣列中的資料\)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|列舉值物件會實作 \(使用 `IEnumOnSTLImpl`\)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|列舉值物件會實作 \(使用 `CComEnumImpl`\)|  
|[\_Copy](../atl/atl-copy-policy-classes.md)|複製原則類別|  
|[\_CopyInterface](../atl/atl-copy-policy-classes.md)|複製原則類別|  
|[CAdapt](../atl/reference/cadapt-class.md)|配接器類別 \(隱藏 **operator \_&** 允許 `CComPtr`、在 STL 容器中儲存的 `CComQIPtr`和 `CComBSTR` \)|  
  
## 請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)