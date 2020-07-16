---
title: MFC ActiveX 控制項精靈、控制項設定
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 1578ca7f4134e51e0ba0d3c2b247dcafcb0fbd67
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405009"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項設定

使用嚮導的這個頁面，即可指定您希望控制項的行為方式。 例如，您可以根據標準 Windows 控制項類型來控制控制項、優化其行為和外觀，或表示控制項可作為其他控制項的容器。

如需如何選取此頁面上的選項以將控制項效率最大化的詳細資訊，請參閱[MFC ActiveX 控制項：優化](../../mfc/mfc-activex-controls-optimization.md)。

## <a name="uielement-list"></a>UIElement 清單

- **建立控制項依據**

   在這份清單中，您可以選取控制項應該繼承的控制項類型。 此清單是控制項類別的子集，可用於 `CreateWindowEx` 和 commctrl 中指定的其他通用控制項。 您的選擇會決定 ProjName 的 Ctrl .cpp 檔案中，該控制項的樣式 `PreCreateWindow` 。 *ProjName* 如需詳細資訊，請參閱[MFC ActiveX 控制項：子類別化 Windows 控制項](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

   |控制|描述|
   |-------------|-----------------|
   |**BUTTON**|Windows 按鈕控制項|
   |**COMBOBOX**|Windows 下拉式方塊控制項|
   |**編輯**|Windows 編輯方塊控制項|
   |**改**|Windows 清單方塊控制項|
   |**滾動**|Windows 捲軸控制項|
   |**靜止**|Windows 靜態控制項|
   |**msctls_hotkey32**|熱鍵通用控制項|
   |**msctls_progress32**|進度列通用控制項|
   |**msctls_statusbar32**|狀態列通用控制項|
   |**msctls_trackbar32**|追蹤列通用控制項|
   |**msctls_updown32**|微調按鈕（或上下）通用控制項|
   |**SysAnimate32**|動畫通用控制項|
   |**SysHeader32**|標頭通用控制項|
   |**SysListView32**|清單視圖通用控制項|
   |**SysTabControl32**|定位字元通用控制項|
   |**SysTreeView32**|樹狀檢視通用控制項|

- **在可見時啟動**

   指定在存取時建立控制項的視窗。 根據預設，會在選取 [**可見時**啟動] 選項。 如果您想要延遲控制項啟用，直到容器需要它為止（例如，當使用者按一下滑鼠時），請清除此選項。 當此功能關閉時，控制項在需要之前，不會產生視窗建立的費用。 如需詳細資訊，請參閱關閉在[可見時啟動選項](../../mfc/turning-off-the-activate-when-visible-option.md)。

- **執行時間不可見**

   指定控制項在執行時間沒有使用者介面。 計時器是一種您可能想要隱藏的控制項。

- **具有 [關於] box 對話方塊**

   指定控制項具有標準 Windows [**關於**] 對話方塊，其中顯示版本號碼和著作權資訊。

   > [!NOTE]
   > 使用者存取控制項的說明的方式，取決於您如何實作為協助，以及是否已將控制項說明與容器的協助整合。

   當您選取此選項時，它會將 `AboutBox` 控制方法插入專案控制項類別（C*ProjName*Ctrl .cpp）中，並將 AboutBox 新增至專案分派對應。 預設會選取這個選項。

- **優化的繪圖程式碼**

   指定容器在繪製至相同裝置內容的所有容器控制項都已繪製之後，自動還原原始的 GDI 物件。 如需這項功能的詳細資訊，請參閱[優化控制項繪製](../../mfc/optimizing-control-drawing.md)。

- **無視窗啟用**

   指定控制項在啟動時不會產生視窗。 無視窗啟用可允許非矩形或透明控制項，而無視窗控制項則需要的系統額外負荷，會比具有 window 需求的控制項少。 無視窗控制項不允許未裁剪裝置內容或無閃爍的啟用。 在1996之前建立的容器不支援無視窗啟用。 如需如何使用此選項的詳細資訊，請參閱[提供無視窗啟用](../../mfc/providing-windowless-activation.md)。

- **未裁剪裝置內容**

   覆寫控制標頭（*projname*ctrl-c）中的[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) ，以停用對 `IntersectClipRect` 所進行的呼叫 `COleControl` 。 當您選取此選項時，它會提供較小的速度優勢。 如果您選取 [**無視窗啟用**]，這項功能就無法使用。 如需詳細資訊，請參閱[使用未裁剪裝置內容](../../mfc/using-an-unclipped-device-context.md)。

- **閃爍-免費啟用**

   排除在控制項的現用和非作用中狀態之間發生的繪圖作業和伴隨的視覺效果閃爍。 如果您選取 [**無視窗啟用**]，這項功能就無法使用。 當您設定此選項時， `noFlickerActivate` 旗標是[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)傳回的其中一個旗標。 如需詳細資訊，請參閱[提供無閃爍的啟用](../../mfc/providing-flicker-free-activation.md)。

- **在 [插入物件] 對話方塊中提供**

   指定在已啟用容器的 [**插入物件**] 對話方塊中，可以使用控制項。 當您選取此選項時， `afxRegInsertable` 旗標會是所傳回的其中一個旗標 `AfxOleRegisterControlClass` 。 藉由使用 [**插入物件**] 對話方塊，使用者可以將新建立或現有的物件插入複合檔案中。

- **非作用中時的滑鼠指標通知**

   可讓控制項處理滑鼠指標通知，控制項是否為作用中。 當您選取此選項時， `pointerInactive` 旗標會是[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)傳回的其中一個旗標。 如需如何使用此選項的詳細資訊，請參閱[在非作用中時提供滑鼠互動](../../mfc/providing-mouse-interaction-while-inactive.md)。

- **作為簡單的框架控制項**

   藉由設定控制項的 OLEMISC_SIMPLEFRAME 位，指定控制項是其他控制項的容器。 如需詳細資訊，請參閱[簡單的框架網站](/windows/win32/com/simple-frame-site-containment)內含專案。

- **以非同步方式載入屬性**

   啟用任何先前非同步資料的重設，並起始控制項之非同步屬性的新負載。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[應用程式設定，MFC ActiveX 控制項精靈](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控制項精靈、控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
