---
title: "追蹤器 | Microsoft Docs"
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
  - "應用程式 [OLE], 追蹤器"
  - "CDC 類別, 追蹤器"
  - "CRectTracker 類別, 實作追蹤器"
  - "OLE 應用程式 [C++], 追蹤器"
  - "OLE 容器, 追蹤器"
  - "OLE 伺服器應用程式, 追蹤器"
  - "追蹤器"
  - "追蹤 OLE 項目"
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 追蹤器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CRectTracker](../mfc/reference/crecttracker-class.md) 類別提供矩形項目在應用程式和使用者之間的使用者介面可提供各種不同的顯示模式。  這些樣式包含純色，已規劃的或虛線的框線;包含項目的一般配置模式;並請調整大小可以設定外部或內部框線的控制代碼。  追蹤與 OLE 項目，也就是說，衍生自 `COleClientItem`的物件一起通常用於。  TRACKER 矩形重新命名項目的目前狀態的視覺提示。  
  
 MFC OLE [OCLIENT](../top/visual-cpp-samples.md) 範例示範通用介面使用追蹤和 OLE 用戶端項目從容器應用程式的檢視。  如需追蹤程式的不同樣式和能力的示範物件，請參閱 MFC 一般 [追蹤程式](../top/visual-cpp-samples.md)範例。  
  
 如需實作自己的 OLE 應用程式的追蹤程式的詳細資訊，請參閱 [追蹤程式:實作您的 OLE 應用程式的追蹤](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)