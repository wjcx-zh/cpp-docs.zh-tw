---
title: 控制項 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617185"
---
# <a name="controls-mfc"></a>控制項 (MFC)

控制項是使用者可以與之互動，以輸入或操作資料的物件。 它們通常會出現在對話方塊或工具列中。 本主題系列涵蓋三種主要的控制項︰

- Windows 通用控制項，包括主控描繪控制項

- ActiveX 控制項

- MFC 程式庫所提供的其他控制項類別

## <a name="windows-common-controls"></a>Windows 通用控制項

Windows 作業系統長久以來一直提供許多 Windows 通用控制項。 這些控制項物件可程式化，而且 Visual C++ 對話方塊編輯器支援將這些控制項加入您的對話方塊。 MFC 程式庫提供類別來封裝上述每個控制項，如 [Windows 通用控制項和 MFC 類別](#_core_windows_common_controls_and_mfc_classes)表格所示。 (表格中的某些項目具有進一步說明的相關主題。 至於缺乏主題的控制項，請參閱 MFC 類別的文件。)

[CWnd](reference/cwnd-class.md) 類別是所有視窗類別 (包括所有控制項類別) 的基底類別。

## <a name="activex-controls"></a>ActiveX 控制項

ActiveX 控制項 (先前稱為 OLE 控制項) 可用於 Windows 應用程式的對話方塊中，或全球資訊網的 HTML 網頁中。 如需詳細資訊，請參閱[MFC ActiveX 控制項](mfc-activex-controls.md)。

## <a name="other-mfc-control-classes"></a>其他 MFC 控制項類別

除了封裝所有 Windows 通用控制項的類別，以及支援編寫您自己的 ActiveX 控制項 (或使用其他人所提供的 ActiveX 控制項) 的類別之外，MFC 還提供自己的控制項類別︰

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a> 尋找 Windows 通用控制項的相關資訊

下表簡短描述每個 Windows 通用控制項，包括控制項的 MFC 包裝函式類別。

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Windows 通用控制項和 MFC 類別

|控制|MFC 類別|描述|Windows 95 中的新功能|
|-------------|---------------|-----------------|------------------------|
|[動畫](using-canimatectrl.md)|[CAnimateCtrl](reference/canimatectrl-class.md)|顯示 AVI 視訊剪輯的連續畫面格|是|
|按鈕|[CButton](reference/cbutton-class.md)|造成動作的按鈕；也用於核取方塊、選項按鈕和群組方塊|否|
|下拉式方塊|[CComboBox](reference/ccombobox-class.md)|編輯方塊和清單方塊的組合|否|
|[日期和時間選擇器](using-cdatetimectrl.md)|[CDateTimeCtrl](reference/cdatetimectrl-class.md)|可讓使用者選擇特定日期或時間值|是|
|編輯方塊|[CEdit](reference/cedit-class.md)|用於輸入文字的方塊|否|
|[擴充的下拉式方塊](using-ccomboboxex.md)|[CComboBoxEx](reference/ccomboboxex-class.md)|可顯示影像的下拉式方塊控制項|是|
|[標頭](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|出現在文字資料行上方的按鈕；顯示的文字控制項寬度|是|
|[箭頭](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|視窗，可讓使用者建立「熱鍵」以快速執行動作|是|
|[影像清單](using-cimagelist.md)|[CImageList](reference/cimagelist-class.md)|用來管理大量圖示或點陣圖的影像集合 (影像清單並非真正的控制項；它支援其他控制項所使用的清單)|是|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|顯示具有圖示之文字清單的視窗|是|
|清單方塊|[CListBox](reference/clistbox-class.md)|包含字串清單的方塊|否|
|[月曆](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|顯示日期資訊的控制項|是|
|[進度](using-cprogressctrl.md)|[CProgressCtrl](reference/cprogressctrl-class.md)|表示長時間作業進度的視窗|是|
|[Rebar](using-crebarctrl.md)|[CRebarCtrl](reference/crebarctrl-class.md)|可包含其他控制項形式之子視窗的工具列|是|
|[Rich Edit](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|使用者可在其中編輯字元和段落格式的視窗 (請參閱 [與 Rich Edit 控制項相關的類別](classes-related-to-rich-edit-controls.md))|是|
|捲軸|[CScrollBar](reference/cscrollbar-class.md)|捲軸，用作為對話方塊內 (而非視窗上) 控制項|否|
|[一直](using-csliderctrl.md)|[CSliderCtrl](reference/csliderctrl-class.md)|含有選擇性使用刻度之滑桿控制項的視窗|是|
|[微調按鈕](using-cspinbuttonctrl.md)|[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|一對箭號按鈕，使用者可在上方按一下以遞增或遞減值|是|
|靜態文字|[CStatic](reference/cstatic-class.md)|用於標示其他控制項的文字|否|
|[狀態列](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|用於顯示狀態資訊的視窗，類似於 MFC 類別 `CStatusBar`|是|
|[標識](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|類似於筆記本的插頁；用於「索引標籤對話方塊」或屬性工作表|是|
|[toolbar](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|具有產生命令之按鈕的視窗，類似於 MFC 類別 `CToolBar`|是|
|[工具提示](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|小型快顯視窗，描述工具列按鈕或其他工具的用途|是|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|顯示階層式項目清單的視窗|是|

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- 個別控制項︰請參閱本主題的 [Windows 通用控制項和 MFC 類別](#_core_windows_common_controls_and_mfc_classes) 表格，以取得所有控制項的連結

- [建立和使用控制項](making-and-using-controls.md)

- [使用對話方塊編輯器加入控制項](using-the-dialog-editor-to-add-controls.md)

- [以手動方式將控制項加入對話方塊](adding-controls-by-hand.md)

- [從 MFC 控制項類別衍生控制項類別](deriving-controls-from-a-standard-control.md)

- [將通用控制項作為子視窗使用](using-a-common-control-as-a-child-window.md)

- [來自通用控制項的通知](receiving-notification-from-common-controls.md)

- [將通用控制項加入對話方塊](using-common-controls-in-a-dialog-box.md)。

- [從標準 Windows 控制項衍生控制項](deriving-controls-from-a-standard-control.md)

- [以型別安全存取對話方塊控制項](type-safe-access-to-controls-in-a-dialog-box.md)

- [從通用控制項接收通知訊息](receiving-notification-from-common-controls.md)

- [範例](common-control-sample-list.md)

如需 Windows SDK 中 Windows 通用控制項的相關資訊，請參閱[通用控制項](/windows/win32/Controls/common-controls-intro)。

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)
