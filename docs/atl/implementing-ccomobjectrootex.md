---
title: "Implementing CComObjectRootEx | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComObjectRootEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class, 實作"
  - "CComObjectRootEx class"
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing CComObjectRootEx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 很重要；所有 ATL 物件都必須在其繼承中有一個 `CComObjectRootEx` 或 [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 執行個體。  `CComObjectRootEx` 提供以 COM 對應項目為基礎的預設 `QueryInterface` 機制。  
  
 透過其 COM 對應，當用戶端查詢介面時，物件的介面會公開給用戶端。  查詢是透過 `CComObjectRootEx::InternalQueryInterface` 執行。  `InternalQueryInterface` 只處理 COM 對應表格中的介面。  
  
 您可以用 [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md) 巨集或其中一個變化，將介面輸入到 COM 對應表格。  例如，下列程式碼會將介面 `IDispatch`、`IBeeper` 和 `ISupportErrorInfo` 輸入到 COM 對應表格：  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/CPP/implementing-ccomobjectrootex_1.h)]  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)