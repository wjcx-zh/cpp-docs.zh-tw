---
title: 對話方塊編輯器 （c + +）
ms.date: 02/15/2019
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
ms.openlocfilehash: dc5a823951e07af96efceec52d2aa23552c2d002
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029482"
---
# <a name="dialog-editor-c"></a>對話方塊編輯器 （c + +）

**對話方塊編輯器**可讓您建立或編輯對話方塊資源。

- 若要開啟編輯器，請按兩下對話方塊的.rc 檔中**資源檢視**視窗中或移至功能表**檢視** > **資源檢視**。

其中一個進行新的對話方塊或對話方塊範本，第一個步驟加入控制項。 在 **對話方塊編輯器**，您可以安排控制項配合特定大小、 圖形或對齊方式，或您可以移動它們大約在對話方塊內順利運作。 刪除控制項也很容易。

您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。

您也可編輯的單一屬性或多個控制項**對話方塊編輯器**。 您可以變更定位順序，也就是取得控制項的順序聚焦在何時** 索引標籤**按鍵，或者，您可以定義的存取金鑰或金鑰的結合，讓使用者選擇使用鍵盤的控制項。

**對話方塊編輯器**也可讓您使用自訂控制項，包括 ActiveX 控制項。 您也可以編輯[表單檢視](../mfc/reference/cformview-class.md)，[記錄檢視](../data/record-views-mfc-data-access.md)，或[對話方塊列](../mfc/dialog-bars.md)。

從 Visual Studio 2015 開始，您可以使用**對話方塊編輯器**來定義當使用者調整對話方塊的動態配置，其會指定如何將控制項移動和調整大小。 如需詳細資訊，請參閱 [Dynamic Layout](../mfc/dynamic-layout.md)。

如需有關資源的詳細資訊，請參閱如何[建立對話方塊](../windows/creating-a-new-dialog-box.md)並[對話方塊控制項](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 在使用時**對話方塊編輯器**，在許多情況下，您可以選擇使用滑鼠右鍵顯示常用命令的捷徑功能表。

## <a name="dialog-editor-toolbar"></a>對話方塊編輯器工具列

**對話方塊編輯器**工具列包含用來排列控制項上的對話方塊中，例如大小和對齊方式的版面配置的按鈕。 **對話方塊編輯器**工具列按鈕上對應至命令**格式**功能表。

|圖示|意義|圖示|意義|
|----------|-------------|----------|-------------|
|![測試對話方塊 按鈕](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|文字方塊|![水平均等陳列 按鈕](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|橫向|
|![將按鈕靠左對齊](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|對齊主控項的左緣|![垂直均等陳列 按鈕](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|下移|
|![將權限按鈕對齊](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|對齊主控項的右緣|![讓相同寬度 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|設定成相同寬度|
|![將頂端的按鈕對齊](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|對齊主控項的上緣|![讓相同高度 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|設定成相同高度|
|![靠下對齊按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|靠下對齊|![讓相同的大小 按鈕](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|設定成相同大小|
|![垂直置中 按鈕](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切換格線 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切換格線|
|![水平置中 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切換輔助線 按鈕](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切換輔助線|

- 若要顯示或隱藏**對話方塊編輯器**工具列上，移至功能表**檢視** > **工具列** > **對話方塊編輯器**。

當您開啟**對話方塊編輯器**在 c + + 專案中，**對話方塊編輯器**工具列會自動出現在您的解決方案的頂端，不過，如果您明確地關閉工具列，您必須叫用它下次您開啟**對話方塊編輯器**。 您可以切換顯示選取從清單中的可用工具列和視窗。

## <a name="switch-between-dialog-box-controls-and-code"></a>對話方塊控制項和程式碼之間切換

在 MFC 應用程式，您可以按兩下對話方塊控制項跳至其處理常式程式碼，或快速地建立處理常式函式 stub。

選取控制項，然後選取 [**控制項事件** 按鈕或**訊息**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)若要檢視 Windows 訊息和事件的完整清單適用於選取的項目。 若要建立或編輯處理常式函式清單中選擇。

- 若要跳到程式碼，從**對話方塊編輯器**，跳至其最近已實作的訊息處理函式的宣告 對話方塊中的控制項上按兩下。

   對於 ATL 為基礎的對話方塊類別中，您一律跳到建構函式定義。

- 若要檢視事件的控制項，與選取的控制項選擇**控制項事件**按鈕**屬性**視窗。

   當單一控制項具有焦點，在對話方塊中時，您可以以滑鼠右鍵按一下並選取**加入事件處理常式**。 這可讓您指定要加入處理常式的類別。 如需詳細資訊，請參閱 <<c0> [ 加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 選擇**控制項事件**對話方塊具有焦點時的按鈕會公開一份對話方塊方塊中，您接著可以擴充編輯個別控制項的事件中的所有控制項。

- 若要檢視訊息對話方塊中，使用 [選取] 對話方塊中選擇**訊息**按鈕**屬性**視窗。

## <a name="accelerator-keys"></a>快速鍵

以下是預設值為快速鍵**對話方塊編輯器**命令。  

|命令|按鍵|描述|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Shift** + **向下箭號**|對齊主控項的所選控制項下邊緣。|
|Format.AlignCenters|**Shift** + **F9**|對齊主控項的所選控制項的垂直置。|
|Format.AlignLefts|**Ctrl** + **Shift** + **向左鍵**|對齊主控項的所選控制項的左邊的緣。|
|Format.AlignMiddles|**F9**|對齊主控項的所選控制項的水平置。|
|Format.AlignRights|**Ctrl** + **Shift** + **向右箭頭**|對齊主控項的所選控制項的右邊緣。|
|Format.AlignTops|**Ctrl** + **Shift** + **向上鍵**|對齊主控項的所選控制項的上邊緣。|
|Format.ButtonBottom|**Ctrl** + **B**|將沿著正下方的對話方塊中選取的按鈕。|
|Format.ButtonRight|**Ctrl** + **R**|位置對話方塊右上角選取的按鈕。|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|將控制項對話方塊內的水平置中。|
|Format.CenterVertical|**Ctrl** + **F9**|置中以垂直方式中對話方塊的控制項。|
|Format.CheckMnemonics|**Ctrl** + **M**|檢查助憶鍵的唯一性。|
|Format.SizeToContent|**Shift** + **F7**|調整大小以符合的標題文字已選取的控制項。|
|Format.SpaceAcross|**Alt** + **向左鍵**|平均的水平空間選取的控制項。|
|Format.SpaceDown|**Alt** + **向下箭號**|垂直均等選取的控制項。|
|Format.TabOrder|**Ctrl** + **D**|設定控制項在對話方塊中的順序。|
|Format.TestDialog|**Ctrl** + **T**|執行測試外觀和行為的對話方塊。|
|Format.ToggleGuides|**Ctrl** + **G**|沒有格線、 準則與方格之間循環編輯對話方塊。|

- 若要變更快速鍵，請移至功能表**工具** > **選項**，然後選擇**鍵盤**下**環境**資料夾。

   如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 若要變更您的設定，請移至功能表**工具** > **匯入和匯出設定**。

   在對話方塊的名稱和您看到，功能表命令的位置中可用的選項可能會與不同的功能中所述**協助**根據您目前使用的設定或版本。  如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[HOW TO：建立對話方塊](../windows/creating-a-new-dialog-box.md)<br/>
[對話方塊控制項](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->