---
title: "Interfaces (ATL) | Microsoft Docs"
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
  - "COM 介面"
  - "介面, COM"
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interfaces (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介面可讓物件將其功能公開給外界的方式。  在 COM 介面指標，為資料表 \(如 vtable 的 . C \+\+\) 物件實作的函式。  資料表表示介面，因此，它所指向的函式是該介面的方法。  在選取物件，可公開介面。  
  
 每個介面根據基礎 COM 介面， [IUnknown](../atl/iunknown.md)。  **IUnknown** 方法巡覽至物件所公開的其他介面。  
  
 此外，對於每個介面唯一的介面 ID \(IID\)  這個唯一可支援版本的介面。  介面的新版本是新的介面，以新的 IID。  
  
> [!NOTE]
>  標準 COM 的 IID 和 OLE 介面預先定義。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [COM Objects and Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms690343)