---
title: "MFC ActiveX 控制項精靈、控制項設定 | Microsoft Docs"
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
  - "vc.appwiz.mfc.ctl.settings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項精靈, 控制項設定"
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項精靈、控制項設定
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用這個精靈頁面來指定您希望控制項表現的行為。  例如，您可以將現有的標準 Windows 控制項型別當做控制項的基礎、最佳化其行為和外觀，或是指示控制項可當做其他控制項的容器。  
  
 如需關於如何選取這個頁面上的選項，以最佳化控制項效率的詳細資訊，請參閱[MFC ActiveX 控制項：最佳化](../../mfc/mfc-activex-controls-optimization.md).  
  
## UIElement 清單  
 **建立控制項基於**  
 您可以在這個清單上選取控制項應繼承的控制項類型。  此清單是控制項類別的子集，這些類別可供 `CreateWindowEx` 及 commctrl.h 所指定的其他通用控制項使用。  您的選擇會決定 *ProjName*Ctrl.cpp 檔中 `PreCreateWindow` 函式內控制項的樣式。  如需詳細資訊，請參閱[MFC ActiveX 控制項：子類別化 Windows 控制項](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
|控制項|說明|  
|---------|--------|  
|**BUTTON**|Windows 按鈕控制項|  
|**COMBOBOX**|Windows 下拉式方塊控制項|  
|**EDIT**|Windows 編輯方塊控制項|  
|**LISTBOX**|Windows 清單方塊控制項|  
|**SCROLLBAR**|Windows 捲軸控制項|  
|**STATIC**|Windows 靜態控制項|  
|**msctls\_hotkey32**|熱鍵通用控制項|  
|**msctls\_progress32**|進度列通用控制項|  
|**msctls\_statusbar32**|狀態列通用控制項|  
|**msctls\_trackbar32**|追蹤列通用控制項|  
|**msctls\_updown32**|旋轉按鈕 （或上下） 通用控制項|  
|**SysAnimate32**|動畫通用控制項|  
|**SysHeader32**|標題通用控制項|  
|**SysListView32**|清單檢視通用控制項|  
|**SysTabControl32**|索引標籤通用控制項|  
|**SysTreeView32**|樹狀檢視通用控制項|  
  
 **當可見時啟動**  
 指定在存取控制項時建立該控制項的視窗。  預設情況下，\[**當可見時啟動**\] 選項已選取。  如果您想將控制項啟用延後到容器要求時 \(例如當使用者按一下滑鼠時\)，請清除此選項。  當這個功能關閉時，控制項只有在需要時才會承擔建立視窗的負載。  如需詳細資訊，請參閱[關閉可見時啟動選項](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 **執行階段不可見**  
 指定控制項在執行階段不具使用者介面。  計時器是一種您可能想隱藏的控制項。  
  
 **產生關於對話方塊**  
 指定控制項具有標準 Windows \[**關於**\] 對話方塊，其中會顯示版本號碼和著作權資訊。  
  
> [!NOTE]
>  使用者存取控制項說明的方式，要視您如何實作說明，以及是否將控制項說明與容器說明整合而定。  如需如何整合說明的詳細資訊，請在這個 [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) 網站上，搜尋「加入即時線上說明加入至 MFC ActiveX 控制項」。  
  
 當您選取這個選項時，它會插入專案控制項類別 \(C*ProjName*Ctrl.cpp\) 中的 `AboutBox` 控制方法並將 AboutBox 加入至專案分派對應。  根據預設，這個選項是選取的。  
  
 **最佳化的繪圖程式碼**  
 指定容器在所有容器的控制項 \(繪製至相同的裝置內容\) 都已繪製之後，自動還原原始 GDI 物件。  如需這個功能的詳細資訊，請參閱[最佳化控制項繪圖](../../mfc/optimizing-control-drawing.md)。  
  
 **無視窗啟動**  
 指定控制項在啟動時不會產生視窗。  無視窗 \(Windowless\) 控制項啟動允許非矩形或透明控制項，而且無視窗控制項會比具有視窗的控制項消耗較少的系統資源。  無視窗控制項不允許未經裁剪的裝置內容或避免重繪閃動。  1996 年以前建立的容器不支援無視窗啟動。  如需如何使用這個選項的詳細資訊，請參閱[提供無視窗啟用](../../mfc/providing-windowless-activation.md)。  
  
 **未裁剪的裝置內容**  
 覆寫控制項標題 \(*projname*ctrl.h\) 中的 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)，停用 `COleControl`對 `IntersectClipRect` 的呼叫。  當您選取這個選項時，它會提供少許速度優勢。  如果您選取 \[**無視窗啟動**\]，則無法使用這個功能。  如需詳細資訊，請參閱[使用未裁剪的裝置內容](../../mfc/using-an-unclipped-device-context.md)。  
  
 **避免重繪閃動**  
 排除繪製作業以及在控制項的非使用中與使用中狀態之間伴隨發生的視覺重繪閃動。  如果您選取 \[**無視窗啟動**\]，則無法使用這個功能。  當您設定這個選項時，`noFlickerActivate` 旗標會是 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) 傳回的其中一個旗標。  如需詳細資訊，請參閱[提供避免重繪閃動](../../mfc/providing-flicker-free-activation.md)。  
  
 **在插入物件對話方塊中可用**  
 指定啟用狀態的容器在其 \[**插入物件**\] 對話方塊中將可使用控制項。  當您選取這個選項時，`afxRegInsertable` 旗標會是 `AfxOleRegisterControlClass` 傳回的其中一個旗標。  使用者可以使用 \[**插入物件**\] 對話方塊，將新建立或現有物件插入至複合文件中。  
  
 **當非現用時之滑鼠指標告知**  
 無論控制項是否在使用中，都會啟用控制項來處理滑鼠指標通知。  當您選取這個選項時，`pointerInactive` 旗標會是 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) 傳回的其中一個旗標。  如需如何使用這個選項的詳細資訊，請參閱[非現用時提供滑鼠互動](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
 **動作和簡單框架控制項相同**  
 透過設定控制項的 `OLEMISC_SIMPLEFRAME` 位元，指定控制項為其他控制項的容器。  如需詳細資訊，在 [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) 網站，搜尋「簡單框架網站內含項目」。  
  
 **非同步載入屬性**  
 啟用任何先前非同步 \(Asynchronous\) 資料的重設和初始化新載入控制項的非同步屬性。  
  
## 請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [應用程式設定，MFC ActiveX 控制項精靈](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)