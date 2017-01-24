---
title: "捲軸樣式 | Microsoft Docs"
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
  - "SBS_VERT"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN"
  - "SBS_LEFTALIGN"
  - "SBS_RIGHTALIGN"
  - "SBS_TOPALIGN"
  - "SBS_SIZEBOXTOPLEFTALIGN"
  - "SBS_BOTTOMALIGN"
  - "SBS_SIZEBOX"
  - "SBS_HORZ"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SBS_BOTTOMALIGN 常數"
  - "SBS_HORZ 常數"
  - "SBS_LEFTALIGN 常數"
  - "SBS_RIGHTALIGN 常數"
  - "SBS_SIZEBOX 常數"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN 常數"
  - "SBS_SIZEBOXTOPLEFTALIGN 常數"
  - "SBS_TOPALIGN 常數"
  - "SBS_VERT 常數"
  - "捲軸, 樣式"
ms.assetid: 8bcde35b-387d-49ae-bdd6-7cda9f5dae26
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 捲軸樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SBS\_BOTTOMALIGN** 配合 **SBS\_HORZ** 樣式。  捲軸的下邊緣對齊 **Create** 成員函式指定矩形的下邊緣。  捲軸有系統捲軸的預設高度。  
  
-   **SBS\_HORZ** 委派水平捲軸。  如果 **SBS\_BOTTOMALIGN** 和 **SBS\_TOPALIGN** 模式未指定，捲軸不會測量的高度、寬度和位置在 **Create** 成員函式。  
  
-   **SBS\_LEFTALIGN** 與 **SBS\_VERT** 樣式一起使用。  捲軸的左邊緣對齊 **Create** 成員函式指定矩形的左邊緣。  捲軸有系統捲軸的預設寬度。  
  
-   **SBS\_RIGHTALIGN** 與 **SBS\_VERT** 樣式一起使用。  捲軸的右邊緣對齊 **Create** 成員函式指定矩形的右邊緣。  捲軸有系統捲軸的預設寬度。  
  
-   **SBS\_SIZEBOX** 將大小控制區塊。  如果 **SBS\_SIZEBOXBOTTOMRIGHTALIGN** 和 **SBS\_SIZEBOXTOPLEFTALIGN** 模式未指定大小，控制項中有指定的高度、寬度和位置在 **Create** 成員函式。  
  
-   **SBS\_SIZEBOXBOTTOMRIGHTALIGN** 配合 **SBS\_SIZEBOX** 樣式。  大小控制項的右下角對齊 **Create** 成員函式指定矩形的右下角。  大小控制區塊有系統調整方塊中的預設大小。  
  
-   **SBS\_SIZEBOXTOPLEFTALIGN** 配合 **SBS\_SIZEBOX** 樣式。  大小控制項的左上角對齊 **Create** 成員函式指定矩形的左上角。  大小控制區塊有系統調整方塊中的預設大小。  
  
-   **SBS\_SIZEGRIP** 和 **SBS\_SIZEBOX**，不過，與凸起的框線。  
  
-   **SBS\_TOPALIGN** 配合 **SBS\_HORZ** 樣式。  捲軸的上邊緣對齊 **Create** 成員函式指定矩形的上邊緣。  捲軸有系統捲軸的預設高度。  
  
-   **SBS\_VERT** 委派垂直捲軸。  如果 **SBS\_RIGHTALIGN** 和 **SBS\_LEFTALIGN** 模式未指定，捲軸不會測量的高度、寬度和位置在 **Create** 成員函式。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CScrollBar::Create](../Topic/CScrollBar::Create.md)   
 [Scroll Bar Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb787533)