---
title: "使用未裁剪的裝置內容 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 未裁剪的裝置內容"
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用未裁剪的裝置內容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您完全確定您的控制項不在其工作區矩形繪製之外，您也可以停用 `COleControl`所進行的呼叫實現小，但是可偵測的速度擷取到 `IntersectClipRect` 。  若要這樣做，請從 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)傳回的旗標集移除 **clipPaintDC** 旗標。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/CPP/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/using-an-unclipped-device-context_3.cpp)]  
  
 移除這個旗標的自動產生程式碼，也可以選擇在 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面的 **Unclipped Device Context** 選項，也就是說，當您建立的 MFC ActiveX 控制項精靈控制項時。  
  
 如果您使用無視窗啟動，這個最佳化沒有作用。  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)