---
title: 對話方塊控制項 (c + +) |Microsoft Docs
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
ms.openlocfilehash: 449e60e968916f7741422ca2766375ad29afd062
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505706"
---
# <a name="dialog-box-controls-c"></a>對話方塊控制項 (c + +) 

您可以使用 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)中的 [**對話方塊編輯器**] 索引標籤，將控制項新增至對話方塊，讓您選擇想要的控制項，並將它拖曳至對話方塊。 依預設，[ **工具箱** ] 視窗會設定為 [自動隱藏]。 當 **對話方塊編輯器** 開啟時，它會顯示為方案左邊界上的索引標籤。 不過，您可以選取視窗右上角的 [**自動隱藏**] 按鈕，將 [**工具箱**] 視窗釘選到 [位置]。 如需如何控制此視窗行為的詳細資訊，請參閱 [視窗管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

將控制項新增至對話方塊、重新置放現有控制項，或將控制項從一個對話方塊移至另一個對話方塊的最快速方式是使用拖放方法。 控制項的位置會以虛線框住，直到它被放入對話方塊中為止。 當您使用拖放方法將控制項加入對話方塊時，控制項會獲得適合該控制項類型的標準高度。

當您將控制項加入至對話方塊或重新放置它時，其最終位置可能取決於輔助線或邊界，或您是否已開啟版面配置方格。

一旦將控制項加入對話方塊之後，您就可以在 [ [屬性] 視窗](/visualstudio/ide/reference/properties-window)中變更屬性，例如其標題。 您也可以選取多個控制項，並同時變更其屬性。

如需 **對話方塊編輯器**的詳細資訊，請參閱如何 [加入、編輯或刪除控制項](adding-editing-or-deleting-controls.md)、 [版面配置控制項](../windows/arrangement-of-controls-on-dialog-boxes.md)，以及 [定義控制項存取和值](../windows/defining-mnemonics-access-keys.md)。

如需控制項和對話方塊的詳細資訊，請參閱 [控制項類別](../mfc/control-classes.md)、 [對話方塊類別](../mfc/dialog-box-classes.md)和 [捲軸樣式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

具有預設事件的 [ **工具箱** ] 中可用的標準控制項如下：

|控制項名稱|預設事件|
|---|---|
|[Button 控制項](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[核取方塊控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[下拉式方塊控制項](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[編輯控制項](../mfc/reference/cedit-class.md)|EN_CHANGE|
|群組方塊|(不適用)|
|[清單方塊控制項](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[選項按鈕控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[靜態文字控制項](../mfc/reference/cstatic-class.md)|(不適用)|
|[圖片控制項](../mfc/reference/cpictureholder-class.md)|(不適用)|
|[Rich Edit 2.0 控制項](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[捲軸控制項](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> 如需搭配使用 **RichEdit 1.0** 控制項與 mfc 的詳細資訊，請參閱搭配 [使用 RichEdit 1.0 控制項與 Mfc](./adding-editing-or-deleting-controls.md) 和 [Rich Edit 控制項範例](../mfc/rich-edit-control-examples.md)。

[**工具箱**] 中提供的[Windows 通用控制項](../mfc/controls-mfc.md)可提供增強的功能：

|控制項名稱|預設事件|
|---|---|
|[滑桿控制項](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[微調控制項](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[進度控制項](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[熱鍵控制項](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[清單控制項](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[樹狀控制項](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[索引標籤控制項](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[動畫控制項](../mfc/using-an-animation-control.md)|ACN_START|
|[日期時間選擇器控制項](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[月曆控制項](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP 位址控制](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[擴充的下拉式方塊控制項](../mfc/creating-an-extended-combo-box-control.md)||
|自訂控制項|TTN_GETDISPINFO|

## <a name="custom-controls"></a>自訂控制項

**對話方塊編輯器**可讓您在對話方塊範本中使用現有的自訂或使用者控制項。

> [!NOTE]
> 這種意義的自訂控制項不會與 ActiveX 控制項混淆。 ActiveX 控制項有時也稱為 OLE 自訂控制項。 此外，請勿將這些控制項與 Windows 中擁有者繪製的控制項混淆。

這項功能的目的是讓您使用 Windows 所提供以外的控制項。 在執行時間，控制項與視窗類別相關聯 (與 c + + 類別) 不同。 完成相同工作的較常見方式是在對話方塊中安裝任何控制項，例如靜態控制項。 然後，在執行時間的 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 函式中，移除該控制項，並將它取代為您自己的自訂控制項。

> [!NOTE]
> 這是舊的技巧。 在大部分的情況下，建議您在大部分的情況下撰寫 Windows 通用控制項的 ActiveX 控制項或子類別。

針對這些自訂控制項，您只能：

- 在對話方塊中設定位置。

- 輸入標題。

- 識別控制項的 Windows 類別名稱，因為您的應用程式程式碼必須使用這個名稱來註冊控制項。

- 輸入可設定控制項樣式的32位十六進位值。

- 設定延伸樣式。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](./adding-editing-or-deleting-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
