---
title: "提供避免重繪閃動 | Microsoft Docs"
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
  - "啟用 [C++], 避免重繪閃動的"
  - "重繪閃動, MFC ActiveX 控制項"
  - "MFC ActiveX 控制項 [C++], 避免重繪閃動的"
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 提供避免重繪閃動
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果控制項在非現用和現用狀態相同繪製其本身 \(而不使用無視窗啟動\)，您可以排除通常發生，在非現用和現用狀態之間轉換的繪製作業和隨附的視覺重繪。  若要這麼做，請將 **noFlickerActivate** 旗標在 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)所傳回的旗標集。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/CPP/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-flicker-free-activation_3.cpp)]  
  
 包含這個旗標的自動產生程式碼，也可以選擇在 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面的 **Flicker\-Free activation** 選項，當您建立的 MFC ActiveX 控制項精靈控制項時。  
  
 如果您使用無視窗啟動，這個最佳化沒有作用。  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)