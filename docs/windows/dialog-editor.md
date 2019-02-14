---
title: 對話方塊編輯器 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: 827a7610aa919d5349313346ac0bfa80bd0647b0
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264890"
---
# <a name="dialog-editor-c"></a>對話方塊編輯器 （c + +）

** 對話方塊**編輯器可讓您建立或編輯對話方塊資源。 您開啟對話方塊編輯器中的對話方塊的.rc 檔上按兩下**資源檢視** 視窗 (**檢視** > **資源檢視**)。 請注意，**資源檢視**不適用於 Express 版本。

建立新對話方塊 (或對話方塊範本) 的前幾個步驟之一，是在對話方塊中加入控制項。 在 [ **] 對話方塊**編輯器中，您可以安排控制項配合特定大小、 圖形或對齊方式，或您可以移動它們大約在對話方塊內順利運作。 刪除控制項也很容易。

您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。

在對話方塊編輯器中也可以編輯單一或多個控制項的屬性。 您可以變更定位順序，也就是取得控制項的順序聚焦在何時 **索引標籤**按鍵，或者您可以定義便捷鍵 （按鍵組合），可讓使用者選擇使用鍵盤的控制項。 如需預設的便捷鍵清單，請參閱 [對話方塊編輯器的快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。

** 對話方塊**編輯器也可讓您使用自訂控制項，包括 ActiveX 控制項。 此外，您可以編輯 [表單檢視](../mfc/reference/cformview-class.md)、 [資料錄檢視表](../data/record-views-mfc-data-access.md)或 [對話方塊列](../mfc/dialog-bars.md)。

從 Visual Studio 2015 開始，您可以使用對話方塊編輯器定義動態配置，其會指定控制項移動及調整大小，當使用者調整對話方塊的方式。 如需詳細資訊，請參閱 [Dynamic Layout](../mfc/dynamic-layout.md)。

- [建立新的對話方塊](../windows/creating-a-new-dialog-box.md)

- [建立使用者在執行階段無法結束的對話方塊](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)

- [加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [測試對話方塊](../windows/testing-a-dialog-box.md)

- [對話方塊編輯器的疑難排解](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > 在使用時 **對話方塊**編輯器，在許多情況下，您可以按一下滑鼠右鍵顯示常用命令的捷徑功能表。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="dialog-editor-toolbar"></a>對話方塊編輯器工具列

當您開啟** 對話方塊**在 c + + 專案中，編輯器**對話方塊編輯器**工具列會自動出現在您的解決方案的頂端。

|圖示|意義|圖示|意義|
|----------|-------------|----------|-------------|
|![測試對話方塊 按鈕](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|文字方塊|![水平均等陳列 按鈕](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|橫向|
|![將按鈕靠左對齊](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|對齊主控項的左緣|![垂直均等陳列 按鈕](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|下移|
|![將權限按鈕對齊](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|對齊主控項的右緣|![讓相同寬度 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|設定成相同寬度|
|![將頂端的按鈕對齊](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|對齊主控項的上緣|![讓相同高度 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|設定成相同高度|
|![靠下對齊按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|靠下對齊|![讓相同的大小 按鈕](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|設定成相同大小|
|![垂直置中 按鈕](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切換格線 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切換格線|
|![水平置中 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切換輔助線 按鈕](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切換輔助線|

**對話方塊編輯器**工具列包含用來排列控制項上的對話方塊中，例如大小和對齊方式的版面配置的按鈕。 **對話方塊編輯器**工具列按鈕上對應至命令**格式**功能表。

如果您正在進行** 對話方塊**編輯器中，您可以切換顯示**對話方塊編輯器**選取從清單中的可用工具列和視窗的工具列。

- 若要顯示或隱藏 [對話方塊編輯器] 工具列中，請在**檢視**功能表上，選取**工具列**，然後選擇**對話方塊編輯器**從子功能表。

   > [!NOTE]
   > **對話方塊編輯器**工具列會顯示根據預設，當您在對話方塊編輯器中開啟對話方塊資源; 不過，如果您明確地關閉工具列，您必須叫用它的下次您開啟對話方塊資源。

## <a name="switch-between-dialog-box-controls-and-code"></a>對話方塊控制項和程式碼之間切換

在 MFC 應用程式，您可以按兩下對話方塊控制項跳至其處理常式程式碼，或快速地建立處理常式函式 stub。

選取控制項，按一下 [**控制項事件**] 按鈕或**訊息**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)若要檢視 Windows 訊息和事件的完整清單適用於選取的項目。 若要建立或編輯處理常式函式清單中選擇。

- 從對話方塊編輯器，以跳到程式碼，請跳至其最近已實作的訊息處理函式的宣告 對話方塊中的控制項上按兩下。 （對於 ATL 為基礎的對話方塊類別中，您一律跳到建構函式定義。）

- 若要檢視事件的控制項，與選取的控制項選擇**控制項事件**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。

   > [!NOTE]
   > 選擇**控制項事件**按鈕時* 對話方塊*具有焦點會公開一份所有控制項，在對話方塊方塊中，您接著可以擴充編輯個別控制項的事件。

   當單一控制項具有焦點，在對話方塊中時，您可以以滑鼠右鍵按一下它，並選取**加入事件處理常式**從捷徑功能表。 這可讓您指定要加入處理常式的類別。 如需詳細資訊，請參閱 <<c0> [ 加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。

- 若要檢視訊息對話方塊中，使用 [選取] 對話方塊中選擇**訊息**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。

## <a name="accelerator-keys"></a>快速鍵

以下是預設的對話方塊編輯器命令的快速鍵。 若要變更快速鍵，請選取**選項**上**工具**功能表，然後選擇**鍵盤**下**環境**資料夾。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

|命令|按鍵|描述|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Shift** + **向下箭號**|對齊主控項的所選控制項的底部邊緣|
|Format.AlignCenters|**Shift** + **F9**|對齊主控項的所選控制項的垂直置中|
|Format.AlignLefts|**Ctrl** + **Shift** + **向左鍵**|對齊主控項的所選控制項的左的緣|
|Format.AlignMiddles|**F9**|對齊主控項的所選控制項的水平置中|
|Format.AlignRights|**Ctrl** + **Shift** + **向右箭頭**|對齊主控項的所選控制項的右邊緣|
|Format.AlignTops|**Ctrl** + **Shift** + **向上鍵**|對齊主控項的所選控制項的頂端邊緣|
|Format.ButtonBottom|**Ctrl** + **B**|將沿著正下方的對話方塊中選取的按鈕|
|Format.ButtonRight|**Ctrl** + **R**|位置對話方塊右上角選取的按鈕|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|將控制項 對話方塊中，水平置中|
|Format.CenterVertical|**Ctrl** + **F9**|將垂直內對話方塊控制項置中|
|Format.CheckMnemonics|**Ctrl** + **M**|檢查不重複的助憶鍵|
|Format.SizeToContent|**Shift** + **F7**|調整大小以符合的標題文字已選取的控制項|
|Format.SpaceAcross|**Alt** + **向左鍵**|均等所選的控制項的水平|
|Format.SpaceDown|**Alt** + **向下箭號**|均等所選的控制項的垂直|
|Format.TabOrder|**Ctrl** + **D**|設定控制項在對話方塊中的順序|
|Format.TestDialog|**Ctrl** + **T**|執行測試外觀和行為對話方塊|
|Format.ToggleGuides|**Ctrl** + **G**|沒有格線、 準則與方格之間的循環，編輯對話方塊|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：建立資源](../windows/how-to-create-a-resource.md)<br/>
[控制項](../mfc/controls-mfc.md)<br/>
[控制項類別](../mfc/control-classes.md)<br/>
[對話方塊類別](../mfc/dialog-box-classes.md)<br/>
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)