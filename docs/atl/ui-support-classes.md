---
title: "UI Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.ui"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "使用者介面, ATL 類別"
  - "使用者介面, support classes"
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# UI Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會提供一般 UI 支援:  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) 解析和呈現引擎的 Microsoft HTML 的介面。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) 提供容器與控制項溝通的主要方法。  處理控制項的就地啟動和停用。  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) 處理控制項的就地重新啟動。  讓無視窗 \(Windowless\) 控制項接收訊息，以及參與拖放作業。  
  
-   [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) 協助就地控制項與其容器之間的通訊。  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) 讓控制項直接顯示和告知容器在其顯示的變更。  為避免重繪閃動 \(Flicker\-Free 繪圖的支援、非矩形和透明控制項和點擊測試。  
  
## 相關文件  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)