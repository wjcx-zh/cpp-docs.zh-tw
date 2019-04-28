---
title: 對話方塊控制項 (C++) |Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 563cf73299c00413889ada2520b1bf4fcd86f2be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223580"
---
# <a name="dialog-box-controls-c"></a>對話方塊控制項 (C++)

您可以將控制項加入對話方塊方塊中，使用**對話方塊編輯器**索引標籤中[工具箱視窗](/visualstudio/ide/reference/toolbox)，可讓您選擇您想要並將它拖曳至對話方塊中的控制項。 根據預設，**工具箱**範圍設定為 自動隱藏。 它會顯示為您的解決方案的左邊界上的索引標籤時**對話方塊編輯器**已開啟。 不過，您可以釘選**工具箱**視窗中選取的位置**自動隱藏**視窗右上角的按鈕。 如需有關如何控制這個視窗的行為的詳細資訊，請參閱 <<c0> [ 視窗管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

將控制項加入對話方塊中，重新定位現有控制項，或將控制項從一個對話方塊中移至另一個，最快的方法是使用拖放方法。 控制項的位置述一條虛線，直到它放入對話方塊。 當您將控制項加入對話方塊中使用拖放方法時，控制項提供適用於該類型的控制項的標準高度。

當您將控制項加入對話方塊中，或重新調整位置時，其最終位置可能會取決於指南或邊界，或者您是否已開啟的版面配置方格。

一旦您已將控制項加入對話方塊中，您可以變更屬性，例如其標題[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您也可以選取多個控制項，並同時變更其屬性。

如需詳細資訊**對話方塊編輯器**，請參閱如何[新增、 編輯或刪除控制項](adding-editing-or-deleting-controls.md)，[版面配置控制項](../windows/arrangement-of-controls-on-dialog-boxes.md)，和[定義控制存取和值](../windows/defining-mnemonics-access-keys.md).

如需有關控制項和對話方塊的詳細資訊，請參閱[控制項類別](../mfc/control-classes.md)，[對話方塊類別](../mfc/dialog-box-classes.md)，並[捲軸樣式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

中可用的標準控制項**工具箱**事件是預設值：

|控制項名稱|預設事件|
|---|---|
|[按鈕控制項](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[核取方塊控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[下拉式方塊控制項](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[編輯控制項](../mfc/reference/cedit-class.md)|EN_CHANGE|
|群組方塊|（不適用）|
|[清單方塊控制項](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[選項按鈕控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[靜態文字控制項](../mfc/reference/cstatic-class.md)|（不適用）|
|[圖片控制項](../mfc/reference/cpictureholder-class.md)|（不適用）|
|[Rich Edit 2.0 控制項](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[捲軸控制項](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> 如需有關使用**RichEdit 1.0**控制項與 MFC，請參閱[使用 RichEdit 1.0 控制項與 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)並[豐富編輯控制項範例](../mfc/rich-edit-control-examples.md)。

[Windows 通用控制項](../mfc/controls-mfc.md)中可用**工具箱**提供增強的功能是：

|控制項名稱|預設事件|
|---|---|
|[滑桿控制項](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[微調控制項](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[進度控制項](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[熱鍵控制項](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[清單控制項](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[樹狀目錄控制項](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[索引標籤控制項](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[動畫控制項](../mfc/using-an-animation-control.md)|ACN_START|
|[日期時間選擇器控制項](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[月曆控制項](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP 位址控制項](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[擴充的下拉式方塊控制項](../mfc/creating-an-extended-combo-box-control.md)||
|自訂控制項|TTN_GETDISPINFO|

## <a name="custom-controls"></a>自訂控制項

**對話方塊編輯器**可讓您使用現有的自訂或對話方塊範本中的使用者控制項。

> [!NOTE]
> 在這種情況下的自訂控制項是不會混淆的 ActiveX 控制項。 ActiveX 控制項已有時也稱為 OLE 自訂控制項。 此外，請勿混淆主控描繪控制項在 Windows 中使用這些控制項。

這項功能被為了讓您使用所提供的 Windows 以外的控制項。 在執行階段，該控制項是相關聯的視窗類別 (不完全相同C++類別)。 安裝在您的對話方塊中的任何控制項，例如靜態控制項，是較常見的方式，來完成相同的工作。 然後會在執行階段，在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式，移除該控制項，並取代您自己的自訂控制項。

> [!NOTE]
> 這是舊的技巧。 目前建議您在大部分情況下撰寫 ActiveX 控制項或子類別化 Windows 通用控制項。

這些自訂的控制項，您僅限於：

- 在對話方塊中設定的位置。

- 輸入標題。

- 因為應用程式程式碼必須註冊此名稱的控制項，用來識別控制項的 Windows 類別的名稱。

- 輸入 32 位元的十六進位值，設定控制項的樣式。

- 設定延伸的樣式。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器](../windows/dialog-editor.md)<br/>

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->