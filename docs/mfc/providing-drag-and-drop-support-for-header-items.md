---
title: "為標題項目提供拖放支援 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 拖放支援"
  - "HDN_ 告知"
  - "HDS_DRAGDROP 樣式"
  - "標題控制項中的標題項目"
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 為標題項目提供拖放支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

針對標頭項目要提供拖放支援，請指定 `HDS_DRAGDROP` 樣式。  拖放支援標題項目可讓使用者重新排列標題控制項的標題項目。  如果標題項目置放，預設行為提供拖曳標題項目的半透明的拖曳影像和新位置的視覺指示器。  
  
 與共用拖放功能，您可以處理 **HDN\_BEGINDRAG** 和 **HDN\_ENDDRAG** 通知擴充預設的拖放行為。  您可以透過覆寫 [CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md) 成員函式可以自訂拖曳影像的外觀。  
  
> [!NOTE]
>  如果您在清單控制項中的內嵌標題控制項的拖放支援，請參閱 [變更的清單控制項模式](../mfc/changing-list-control-styles.md) 主題的延伸樣式部分。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)