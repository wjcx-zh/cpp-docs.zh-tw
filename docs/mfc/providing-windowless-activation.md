---
title: "提供無視窗啟用 | Microsoft Docs"
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
  - "啟用 [C++], MFC ActiveX 控制項"
  - "啟用 [C++], 無視窗"
  - "MFC ActiveX 控制項 [C++], 啟用選項"
  - "MFC ActiveX 控制項的無視窗啟用"
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供無視窗啟用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

視窗中發生的建立程式碼 \(亦即，當您呼叫 **CreateWindow**\) 是高度耗費資源的執行。  維護一個螢幕上的視窗的控制項必須處理 Windows 訊息。  因此無視窗控制項與視窗控制項快速地為。  
  
 無視窗控制項的進一步的好處是，不同於視窗型控制項，無視窗控制項支援透明繪製和非矩形螢幕區域。  表示控制項的一個常見的範例是具有透明背景的文字控制項。  控制項的文字，但不是背景，因此，哪些傳入的文字展示下。  較新的表單通常是矩形利用控制項，例如箭號和圓形按鈕。  
  
 通常，在這種情況下，容器撰寫支援無視窗物件的情況下，控制項不需要它的視窗，因此，反之，無法使用其容器的 Windows 服務。  無視窗控制項與舊的容器回溯相容。  在沒有寫入的較舊的容器支援無視窗控制項，無視窗控制項建立視窗，當現用。  
  
 由於無視窗控制項沒有自己的視窗，具有視窗\) 的容器 \(如提供控制項的視窗則會提供的服務執行。  例如，如果控制項需要查詢鍵盤焦點，捕捉滑鼠或取得裝置內容，這些作業由容器處理。  容器傳送使用者輸入訊息傳送至其視窗為適當的無視窗控制項，請使用 `IOleInPlaceObjectWindowless` 介面。\(這個介面的說明請參閱 *ActiveX SDK* \)。 `COleControl` 成員函式叫用從容器的這些服務。  
  
 若要讓控制項使用無視窗啟動，包括 **windowlessActivate** 旗標在 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)所傳回的旗標集。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/CPP/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-windowless-activation_3.cpp)]  
  
 如果在 MFC ActiveX 控制項精靈的 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面中， **Windowless activation** 選項包括這個旗標的自動產生程式碼。  
  
 在無視窗啟動時，容器會委派輸入訊息至控制項的 `IOleInPlaceObjectWindowless` 介面。  此介面的`COleControl` 實作會將您的控制項的訊息對應分派訊息在適當調整滑鼠座標之後。  將對應的項目加入至訊息對應讓您可以像一般的 Windows 訊息般處理訊息。  在這些訊息的處理常式，請避免使用 `m_hWnd` 成員變數 \(或使用它的任何成員函式\)，而不需先檢查其值不是 **NULL**。  
  
 `COleControl` 提供叫用滑鼠捕捉、鍵盤焦點、捲動和其他 Windows 服務從容器適當的成員函式，包括：  
  
-   [GetFocus](../Topic/COleControl::GetFocus.md)， [SetFocus](../Topic/COleControl::SetFocus.md)  
  
-   [GetCapture](../Topic/COleControl::GetCapture.md)， [SetCapture](../Topic/COleControl::SetCapture.md)， [ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)  
  
-   [GetDC](../Topic/COleControl::GetDC.md)， [ReleaseDC](../Topic/COleControl::ReleaseDC.md)  
  
-   [InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)  
  
-   [ScrollWindow](../Topic/COleControl::ScrollWindow.md)  
  
-   [GetClientRect](../Topic/COleControl::GetClientRect.md)  
  
 在無視窗控制項，您必須使用 `COleControl` 成員函式來取代對應的 `CWnd` 成員函式或及其相關的 Win32 API 函式。  
  
 您可以無視窗控制項是 OLE 拖放作業的目標。  通常，這需要控制 Windows 登錄為置放目標。  因為控制項沒有自己的視窗，容器使用其視窗做為置放目標。  控制項提供容器可以在適當時間呼叫委派 `IDropTarget` 介面的實作。  若要公開這個介面的控制項，請覆寫 [COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md)。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/CPP/providing-windowless-activation_4.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)