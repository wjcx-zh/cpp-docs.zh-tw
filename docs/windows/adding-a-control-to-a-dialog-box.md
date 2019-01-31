---
title: 將控制項加入對話方塊 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293620"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>將控制項加入對話方塊 （c + +）

**對話方塊編輯器**索引標籤會出現在[工具箱視窗](/visualstudio/ide/reference/toolbox)當您處理**對話方塊**編輯器。 若要將控制項加入新的對話方塊中，將控制項從**工具箱**到您要建立的對話方塊。 然後移動控制項，或變更其大小和形狀。

中可用的標準控制項**工具箱**是：

- [按鈕控制項](../mfc/reference/cbutton-class.md)

- [核取方塊控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [下拉式方塊控制項](../mfc/reference/ccombobox-class.md)

- [編輯控制項](../mfc/reference/cedit-class.md)

- 群組方塊

- [清單方塊控制項](../mfc/reference/clistbox-class.md)

- [選項按鈕控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [靜態文字控制項](../mfc/reference/cstatic-class.md)

- [圖片控制項](../mfc/reference/cpictureholder-class.md)

- [Rich Edit 2.0 控制項](../mfc/using-cricheditctrl.md)

- [捲軸控制項](../mfc/reference/cscrollbar-class.md)

[Windows 通用控制項](../mfc/controls-mfc.md)中可用**工具箱**提供增強的功能，在您的應用程式。 包括：

- [滑桿控制項](../mfc/slider-control-styles.md)

- [微調控制項](../mfc/using-cspinbuttonctrl.md)

- [進度控制項](../mfc/styles-for-the-progress-control.md)

- [熱鍵控制項](../mfc/using-a-hot-key-control.md)

- [清單控制項](../mfc/list-control-and-list-view.md)

- [樹狀目錄控制項](../mfc/tree-control-styles.md)

- [索引標籤控制項](../mfc/tab-controls-and-property-sheets.md)

- [動畫控制項](../mfc/using-an-animation-control.md)

- [日期時間選擇器控制項](../mfc/creating-the-date-and-time-picker-control.md)

- [月曆控制項](../mfc/month-calendar-control-examples.md)

- [IP 位址控制項](../mfc/reference/cipaddressctrl-class.md)

- [擴充的下拉式方塊控制項](../mfc/creating-an-extended-combo-box-control.md)

- [自訂控制項](custom-controls-in-the-dialog-editor.md)

您可以將自訂控制項加入對話方塊中選取**自訂控制項**中的圖示**工具箱**將它拖曳至您的對話方塊。 若要新增**Syslink**控制項，加入自訂控制項，然後變更控制項的**類別**屬性設**Syslink**。 這會導致要重新整理和顯示的屬性**Syslink**控制屬性。 如需 MFC 包裝函式類別的資訊，請參閱[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

您也可以[ActiveX 控制項加入您的對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

您也可以自訂**工具箱**，方便使用的視窗。 如需詳細資訊，請參閱[使用工具箱](/visualstudio/ide/using-the-toolbox)。

如需有關使用**RichEdit 1.0**控制項與 MFC，請參閱[使用 RichEdit 1.0 控制項與 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-add-a-control-to-a-dialog-box"></a>在對話方塊加入控制項

1. 確定對話方塊索引標籤式視窗是編輯器框架中的目前文件。 如果對話方塊不是目前的文件，您不會看到**對話方塊編輯器索引標籤**中**工具箱**。

1. 在 **對話方塊編輯器**索引標籤[工具箱視窗](/visualstudio/ide/reference/toolbox)，選取您想要的控制項，然後：

   - 選取您想要將控制項放置位置的對話方塊。 控制項中，就會出現您所選取的位置。

       \-或-

   - 將拖放控制項**工具箱**視窗至您的對話方塊上的位置。

       \-或-

   - 按兩下中的控制項**工具箱**（出現在您的對話方塊） 視窗，然後重新定位控制項以您偏好的位置。

## <a name="to-add-multiple-controls"></a>若要將多個控制項

1. 按住**Ctrl**機碼，請選取中的控制項[工具箱視窗](/visualstudio/ide/reference/toolbox)。

1. 發行**Ctrl**鍵並選取 [] 對話方塊中，您想要新增之特定控制項的次數。

1. 按下**Esc**來停止放置控制項。

## <a name="to-size-a-control-while-you-add-it"></a>若要調整控制項的大小，而您將它加入

1. 選取的控制項[[工具箱] 視窗](/visualstudio/ide/reference/toolbox)。

1. 將游標放 （這會顯示當十字） 您想要在您的對話方塊上的新控制項的左上角的位置。

1. 選取並按住滑鼠按鈕，即可在對話方塊中，控制項的左上角的錨點，然後將游標拖曳至右和向下直到控制項是您想要的大小。

   > [!NOTE]
   > 您可以實際上錨定在任何您正在繪製之控制項的四個邊角。 此程序會使用左上角，做為範例。

1. 放開滑鼠按鈕。 控制項置於對話方塊中，您所指定的大小。

   > [!TIP]
   > 您可以調整控制項的大小之後它拖放到對話方塊中移動控制項框線的縮放控點。 如需詳細資訊，請參閱 <<c0> [ 調整個別控制項](../windows/sizing-individual-controls.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[控制項](../mfc/controls-mfc.md)<br/>
[控制項類別](../mfc/control-classes.md)<br/>
[對話方塊類別](../mfc/dialog-box-classes.md)<br/>
[捲軸樣式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Rich Edit 控制項範例](../mfc/rich-edit-control-examples.md)<br/>
