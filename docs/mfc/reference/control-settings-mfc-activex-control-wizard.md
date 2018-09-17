---
title: MFC ActiveX 控制項精靈、 控制項設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5a9f35be36de5e1c72650e83b48e8112469235
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723329"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項設定
您可以使用精靈的這個頁面來指定您要的控制項行為的方式。 比方說，您可以將基底上標準的 Windows 控制項類型的控制項、 最佳化其行為和外觀，或表示控制項可做為其他控制項的容器。  
  
 如需如何選取此頁面上將控制項的效率最大化的選項的詳細資訊，請參閱[MFC ActiveX 控制項： 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
- **建立控制項**

   在這份清單中，您可以選取控制項應該繼承的控制項的種類。 清單是可供控制項類別的子集`CreateWindowEx`和其他常見的控制項於 commctrl.h 中所指定。 您的選擇會決定在控制項的樣式`PreCreateWindow`函式中*ProjName*Ctrl.cpp 檔。 如需詳細資訊，請參閱 < [MFC ActiveX 控制項： 子類別化 Windows 控制項](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
   |控制項|描述|  
   |-------------|-----------------|  
   |**按鈕**|Windows 按鈕控制項|  
   |**下拉式方塊**|Windows 下拉式方塊控制項|  
   |**編輯**|Windows 編輯方塊控制項|  
   |**清單方塊**|Windows 清單方塊控制項|  
   |**捲軸**|Windows 捲軸控制項|  
   |**靜態**|Windows 靜態控制項|  
   |**msctls_hotkey32**|熱鍵通用控制項|  
   |**msctls_progress32**|進度列，通用控制項|  
   |**msctls_statusbar32**|狀態列通用控制項|  
   |**msctls_trackbar32**|滑動軸通用控制項|  
   |**msctls_updown32**|微調按鈕 （或上下） 通用控制項|  
   |**SysAnimate32**|動畫的通用控制項|  
   |**SysHeader32**|標頭的通用控制項|  
   |**SysListView32**|清單檢視通用控制項|  
   |**SysTabControl32**|索引標籤上的通用控制項|  
   |**SysTreeView32**|樹狀結構檢視通用控制項|  
  
- **顯示時啟用**

   指定視窗建立控制項時存取。 根據預設，**可見時啟動**選項。 如果您想要延遲啟動控制項，直到容器需要 （例如，當使用者按一下滑鼠），請清除此選項。 當此功能關閉時，控制項不會產生所需的視窗建立成本，才需要。 如需詳細資訊，請參閱 <<c0> [ 關閉可見時啟動選項](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
- **在執行階段不可見**

   指定控制項在執行期間有任何使用者介面。 計時器是控制項的一種您可能想要隱藏。  
  
- **有關於對話方塊**

   指定控制項有標準的 Windows**關於** 對話方塊中，以顯示版本號碼和著作權資訊。  
  
   > [!NOTE]
   > 使用者如何存取控制項的說明取決於您如何實作的說明，以及是否已與容器說明整合該控制項的說明。 如需有關如何在整合的說明，請[MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542)網站上搜尋 「 新增即時線上說明以 MFC ActiveX 控制項 」。  
  
   當您選取此選項時，它會插入`AboutBox`控制方法，在專案控制項類別 (C*ProjName*Ctrl.cpp) 並將 aboutbox 加入至專案分派對應。 根據預設，這個選項是選取的。  
  
- **最佳化的繪圖程式碼**

   指定容器的原始 GDI 物件自動還原在所有容器控制項中，繪製至相同的裝置內容，都已繪製。 如需這項功能的詳細資訊，請參閱[最佳化控制項繪圖](../../mfc/optimizing-control-drawing.md)。  
  
- **無視窗啟用**

   指定的控制項不會產生視窗啟用時。 無視窗啟用可讓非矩形或安全性透明的控制項，並無視窗控制項可讓您需要較少的系統負擔比具有視窗的控制項需要。 無視窗控制項不允許未裁剪的裝置內容或 flicker-free 啟用。 1996 年之前所建立的容器不支援無視窗啟用。 如需如何使用此選項的詳細資訊，請參閱[提供無視窗啟用](../../mfc/providing-windowless-activation.md)。  
  
- **裁剪的裝置內容**

   覆寫[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)控制標頭中 (*projname*ctrl.h) 若要停用來呼叫`IntersectClipRect`所做的`COleControl`。 當您選取此選項時，它會提供一項小速度的優點。 如果您選取**無視窗啟用**，則無法使用此功能。 如需詳細資訊，請參閱 <<c0> [ 使用未裁剪的裝置內容](../../mfc/using-an-unclipped-device-context.md)。  
  
- **Flicker-free 啟用**

   它會消除繪圖作業和控制項的作用與非作用中狀態之間發生的視覺重繪。 如果您選取**無視窗啟用**，則無法使用此功能。 當您設定此選項時，`noFlickerActivate`旗標是其中一個所傳回的旗標[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 如需詳細資訊，請參閱 <<c0> [ 提供 Flicker-free 啟用](../../mfc/providing-flicker-free-activation.md)。  
  
- **在 [插入物件] 對話方塊中，您可以使用**

   指定控制項是否會用於**插入物件**適用於已啟用容器 對話方塊。 當您選取此選項時，`afxRegInsertable`旗標是所傳回的旗標的其中一個`AfxOleRegisterControlClass`。 藉由使用**插入物件** 對話方塊中，使用者就可以插入新建或現有的物件組成的複合文件。  
  
- **非使用中時，滑鼠指標通知**

   控制是否使用中，或不會啟用處理滑鼠指標通知，控制。 當您選取此選項時，`pointerInactive`旗標是其中一個所傳回的旗標[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 如需如何使用此選項的詳細資訊，請參閱[提供滑鼠互動而非使用中](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
- **做為簡單框架控制項**

   指定控制項是其他控制項的容器，藉由設定控制項的位元 OLEMISC_SIMPLEFRAME。 如需詳細資訊，在[MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542)網站上搜尋 「 簡單框架網站內含項目 」。  
  
- **以非同步方式載入屬性**

   可讓任何先前的非同步資料重設，並起始新的負載，控制項的非同步屬性。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

