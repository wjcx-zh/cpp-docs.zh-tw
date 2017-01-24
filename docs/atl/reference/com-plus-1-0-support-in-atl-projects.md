---
title: "ATL 專案中的 COM+ 1.0 支援 | Microsoft Docs"
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
  - "vc.appwiz.ATL.MTS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, COM+ 1.0 支援"
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 專案中的 COM+ 1.0 支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用 [ATL 專案精靈](../../atl/reference/creating-an-atl-project.md)來建立具有 COM\+ 1.0 元件基本支援的專案。  
  
 COM\+ 1.0 是設計來開發分散式元件架構應用程式。  它也提供執行階段基礎結構來部署和管理這些應用程式。  
  
 如果選取 \[支援 COM\+ 1.0\] 核取方塊，精靈會在連結步驟修改建置 \(Build\) 指令碼。  要注意的是，COM\+ 1.0 專案會連結至下列程式庫：  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果選取 \[支援 COM\+ 1.0\] 核取方塊，則您也可選取 \[支援元件登錄器\]。  元件登錄器允許您的 COM\+ 1.0 物件取得元件、登錄元件或未登錄元件的清單 \(一次一個或全部\)。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)