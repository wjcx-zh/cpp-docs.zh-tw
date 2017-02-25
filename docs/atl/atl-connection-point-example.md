---
title: "ATL Connection Point Example | Microsoft Docs"
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
  - "連接點 [C++], 範例"
  - "examples [ATL]"
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ATL Connection Point Example
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個範例顯示所支援 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 為輸出介面的物件:  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/CPP/atl-connection-point-example_1.h)]  
  
 當指定 `IPropertyNotifySink` 為輸出介面時，您可以使用類別 [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 而不是 `IConnectionPointImpl`。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/CPP/atl-connection-point-example_2.h)]  
  
## 請參閱  
 [連接點](../atl/atl-connection-points.md)