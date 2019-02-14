---
title: 控制項在對話方塊中 （c + +） |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f231a376b335d7fb711ef2039c13f49624e6bfb
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264838"
---
# <a name="controls-in-dialog-boxes-c"></a>控制項在對話方塊中 （c + +）

您可以將控制項加入對話方塊方塊中，使用[對話方塊編輯器索引標籤](../windows/dialog-editor-tab-toolbox.md)中[工具箱視窗](/visualstudio/ide/reference/toolbox)，這可讓您選擇您想要並將它拖曳至對話方塊中的控制項。 根據預設，工具箱 視窗設為 自動隱藏。 對話方塊編輯器開啟時，它會為您的解決方案的左邊界上的索引標籤出現。 不過，您可以釘選**工具箱**視窗中的按一下位置**自動隱藏**視窗右上角的按鈕。 如需有關如何控制這個視窗的行為的詳細資訊，請參閱 <<c0> [ 視窗管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

將控制項加入對話方塊中，重新定位現有控制項，或將控制項從一個對話方塊中移至另一個，最快的方法是使用拖放方法。 控制項的位置述一條虛線，直到它放入對話方塊。 當您將控制項加入對話方塊中使用拖放方法時，控制項提供適用於該類型的控制項的標準高度。

當您將控制項加入對話方塊中，或重新調整位置時，其最終位置可能會取決於指南或邊界，或者您是否已開啟的版面配置方格。

一旦您已將控制項加入對話方塊中，您可以變更屬性，例如其標題[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以選取多個控制項，並變更其屬性，全部一次。

- [新增、編輯或刪除控制項](adding-editing-or-deleting-controls.md)

- [選取控制項](../windows/selecting-controls.md)

- [調整個別控制項的大小](../windows/sizing-individual-controls.md)

- [讓控制項同寬、同高或相同大小](../windows/making-controls-the-same-width-height-or-size.md)

- [設定下拉式方塊和下拉式清單的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [將值新增至下拉式方塊控制項](../windows/adding-values-to-a-combo-box-control.md)

- [設定水平捲軸的寬度](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [對話方塊上的控制項排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [定義助憶鍵 (便捷鍵)](../windows/defining-mnemonics-access-keys.md)

- [指定對話方塊的位置和大小](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

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

如需有關使用**RichEdit 1.0**控制項與 MFC，請參閱[使用 RichEdit 1.0 控制項與 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)並[豐富編輯控制項範例](../mfc/rich-edit-control-examples.md)。

[Windows 通用控制項](../mfc/controls-mfc.md)中可用**工具箱**提供增強的功能，在您的應用程式。 包括：

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

如需詳細資訊，請參閱 <<c0> [ 控制項類別](../mfc/control-classes.md)，[對話方塊類別](../mfc/dialog-box-classes.md)，並[捲軸樣式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

## <a name="custom-controls"></a>自訂控制項

對話方塊編輯器可讓您使用現有 「 自訂 」 或對話方塊範本中的 「 使用者 」 控制項。

> [!NOTE]
> 在這種情況下的自訂控制項是不會混淆的 ActiveX 控制項。 ActiveX 控制項已有時也稱為 OLE 自訂控制項。 此外，請勿混淆主控描繪控制項在 Windows 中使用這些控制項。

這項功能被為了讓您使用所提供的 Windows 以外的控制項。 在執行階段，則控制項為相關聯的視窗類別 （不同於 c + + 類別）。 安裝在您的對話方塊中的任何控制項，例如靜態控制項，是較常見的方式，來完成相同的工作。 然後會在執行階段，在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式，移除該控制項，並取代您自己的自訂控制項。

這是舊的技巧。 目前建議您在大部分情況下撰寫 ActiveX 控制項或子類別化 Windows 通用控制項。

這些自訂的控制項，您僅限於：

- 在對話方塊中設定的位置。

- 輸入標題。

- 用來識別控制項的 Windows 類別 （應用程式程式碼必須註冊該控制項使用這個名稱） 的名稱。

- 輸入 32 位元的十六進位值，設定控制項的樣式。

- 設定延伸的樣式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[控制項](../mfc/controls-mfc.md)<br/>