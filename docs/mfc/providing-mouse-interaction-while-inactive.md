---
title: "非現用時提供滑鼠互動 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 滑鼠互動"
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 非現用時提供滑鼠互動
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果控制項沒有立即啟動，您仍會想處理 `WM_SETCURSOR` 和 `WM_MOUSEMOVE` 訊息，即使控制項沒有自己的視窗。  這可以藉由打開 `IPointerInactive` 介面的 `COleControl` 實作完成，預設為停用。\(這個介面的說明請參閱 *ActiveX SDK* \)。若要啟用此功能，在 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)傳回的一組旗標中包含 `pointerInactive` 旗標:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 在建立具有 **MFC ActiveX Control Wizard**中的控制項時，如果您選擇 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面的 **Mouse Pointer Notifications When Inactive** 選項，包含這個旗標的程式碼會自動產生。  
  
 當 `IPointerInactive` 介面啟用時，容器委派 `WM_SETCURSOR` 和 `WM_MOUSEMOVE` 訊息給它。  `IPointerInactive` 的`COleControl` 實作會將您的控制項的訊息對應分派訊息在適當調整滑鼠座標之後。  將對應的項目加入至訊息對應讓您可以像一般的 Windows 訊息般處理訊息。  在這些訊息的處理常式，請避免使用 `m_hWnd` 成員變數 \(或使用它的任何成員函式\)，而不需先檢查其值不是 **NULL**。  
  
 您也可能需要將非現用控制項作為 OLE 拖放作業的目標。  這需要在使用者將物件拖曳過它時啟動控制項，因此控制項視窗可以註冊為置放目標。  在拖曳期間，若要讓啟動發生，請覆寫 [COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md)，並傳回 **POINTERINACTIVE\_ACTIVATEONDRAG** 旗標:  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 啟用 `IPointerInactive` 介面通常表示您要控制項可以隨時處理滑鼠訊息。  若要讓不支援 `IPointerInactive` 介面之容器產生這種行為，您必須讓您的控制項當當可見時一直啟動，表示控制項應包含 **OLEMISC\_ACTIVATEWHENVISIBLE** 旗標在它的其他旗標中。  不過，為了防止這個旗標於支援 `IPointerInactive` 之容器生效，您也可以指定 **OLEMISC\_IGNOREACTIVATEWHENVISIBLE** 旗標:  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)