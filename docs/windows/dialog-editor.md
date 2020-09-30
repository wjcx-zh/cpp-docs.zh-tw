---
title: '對話方塊編輯器 (c + +) '
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
ms.openlocfilehash: 6a83640bd50d4af40be3cdb7a47b29ae5ffb3f09
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504543"
---
# <a name="dialog-editor-c"></a>對話方塊編輯器 (c + +) 

**對話方塊編輯器**可讓您建立或編輯對話方塊資源。

- 若要開啟編輯器，請在 [**資源檢視**] 視窗中，按兩下對話方塊的 .rc 檔，或移至 [功能表**視圖**] 的 [  >  **其他視窗**]  >  **資源檢視**。

建立新對話方塊或對話方塊範本的第一個步驟是加入控制項。 在 **對話方塊編輯器**中，您可以排列控制項以符合特定的大小、形狀或對齊，也可以在對話方塊中四處移動它們來工作。 刪除控制項也很容易。

您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。

您也可以在 **對話方塊編輯器**中編輯單一或多個控制項的屬性。 您可以變更定位順序，也就是當按下 **tab** 鍵時，控制項取得焦點的順序，或者，您也可以定義存取金鑰或按鍵組合，讓使用者選擇使用鍵盤的控制項。

**對話方塊編輯器**也可讓您使用自訂控制項，包括 ActiveX 控制項。 您也可以編輯 [表單檢視](../mfc/reference/cformview-class.md)、 [記錄視圖](../data/record-views-mfc-data-access.md)或 [對話方塊](../mfc/dialog-bars.md)列。

從 Visual Studio 2015 開始，您可以使用 **對話方塊編輯器** 來定義動態配置，以指定當使用者調整對話方塊大小時，控制項如何移動和調整大小。 如需詳細資訊，請參閱 [Dynamic Layout](../mfc/dynamic-layout.md)。

如需資源的詳細資訊，請參閱如何 [建立對話方塊](../windows/creating-a-new-dialog-box.md) 和 [對話方塊控制項](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 使用 **對話方塊編輯器**時，在許多情況下，您可以選取滑鼠右鍵，以顯示常用命令的快捷方式功能表。

## <a name="dialog-editor-toolbar"></a>對話方塊編輯器工具列

**對話方塊編輯器**工具列包含可在對話方塊上排列控制項版面配置的按鈕，例如大小和對齊方式。 **對話方塊編輯器** 工具列按鈕對應至 [ **格式** ] 功能表上的命令。

|圖示|意義|圖示|意義|
|----------|-------------|----------|-------------|
|![[測試對話方塊] 按鈕](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|文字方塊|![[水平均等陳列] 按鈕](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|橫向|
|![[對齊主控項的左緣] 按鈕](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|對齊主控項的左緣|![[垂直均等陳列] 按鈕](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Down|
|![[對齊主控項的右緣] 按鈕](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|對齊主控項的右緣|![[設定成相同寬度] 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|設定成相同寬度|
|![[對齊主控項的上緣] 按鈕](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|對齊主控項的上緣|![[設定成相同高度] 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|設定成相同高度|
|![[對齊主控項的下緣] 按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|靠下對齊|![[設定成相同大小] 按鈕](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|設定成相同大小|
|![[垂直置中] 按鈕](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![[切換格線] 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切換格線|
|![[水平置中] 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![[切換輔助線] 按鈕](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切換輔助線|

- 若要顯示或隱藏**對話方塊編輯器**工具列，請移至 [功能表**視圖**  >  **工具列**  >  **] 對話方塊編輯器**。

當您在 c + + 專案中開啟 **對話方塊編輯器** 時， **對話方塊編輯器** 工具列會自動出現在您的方案頂端，不過，如果您明確地關閉工具列，您將需要在下次開啟 **對話方塊編輯器**時叫用它。 您可以從可用的工具列和視窗清單中選取它，來切換其顯示畫面。

## <a name="switch-between-dialog-box-controls-and-code"></a>在對話方塊控制項和程式碼之間切換

在 MFC 應用程式中，您可以按兩下對話方塊控制項，以跳至其處理常式程式碼或快速建立存根處理常式函式。

選取控制項之後，請選取 [**事件**] 按鈕或[屬性視窗](/visualstudio/ide/reference/properties-window)中的 [**訊息**] 按鈕，以查看所選項目可用之 Windows 訊息和事件的完整清單。 從清單中選擇，以建立或編輯處理常式函數。

- 若要跳至 **對話方塊編輯器**中的程式碼，請按兩下對話方塊內的控制項，跳至其最新執行的訊息處理函式的宣告。

   針對以 ATL 為基礎的對話方塊類別，您一律會跳到函式定義。

- 若要查看控制項的事件，並選取控制項，請在 [**屬性**] 視窗中選擇 [**事件**] 按鈕。

   當單一控制項在對話方塊中具有焦點時，您可以按一下滑鼠右鍵並選取 [ **加入事件處理常式**]。 這可讓您指定要加入處理常式的類別。 如需詳細資訊，請參閱 [新增事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 當對話方塊的焦點顯示對話方塊中的所有控制項清單時，選擇 [ **事件** ] 按鈕，您可以展開該對話方塊，以編輯個別控制項的事件。

- 若要查看對話方塊的訊息，請在選取對話方塊的情況下，選擇 [**屬性**] 視窗中的 [**訊息**] 按鈕。

## <a name="accelerator-keys"></a>快速鍵

以下是 **對話方塊編輯器** 命令的預設快速鍵。  

|命令|索引鍵|描述|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl**  + **Shift**  + **向下箭**號|將所選控制項的下邊緣與主控制項對齊。|
|Format.AlignCenters|**Shift**  + **F9**|將所選控制項的垂直中央與主控制項對齊。|
|Format.AlignLefts|**Ctrl**  + **Shift**  + **向左箭**號|將所選控制項的左邊緣與主控制項對齊。|
|Format.AlignMiddles|**F9**|將所選控制項的水準中心與主控制項對齊。|
|Format.AlignRights|**Ctrl**  + **Shift**  + **向右箭**號|將所選控制項的右邊緣與主控制項對齊。|
|Format.AlignTops|**Ctrl**  + **Shift**  + **向上鍵**|將所選控制項的上邊緣與主控制項對齊。|
|Format.ButtonBottom|**Ctrl** + **B**|將選取的按鈕沿著對話方塊的底部置中。|
|Format.ButtonRight|**Ctrl**  + **R**|將選取的按鈕放在對話方塊的右上角。|
|Format.CenterHorizontal|**Ctrl**  + **Shift**  + **F9**|將控制項在對話方塊中水準置中。|
|Format.CenterVertical|**Ctrl**  + **F9**|將控制項在對話方塊中垂直置中。|
|Format.CheckMnemonics|**Ctrl**  + **M**|檢查助憶鍵的唯一性。|
|格式。 System.windows.window.sizetocontent|**Shift**  + **F7**|調整所選控制項 (s) 的大小，以符合標題文字。|
|Format.SpaceAcross|**Alt**  + **向左箭**號|以水準方式將選取的控制項間距隔開。|
|Format.SpaceDown|**Alt**  + **向下箭**號|以垂直方式將選取的控制項以空格隔開。|
|Format.TabOrder|**Ctrl**  + **D**|設定對話方塊內的控制項順序。|
|Format.TestDialog|**Ctrl**  + **T**|執行對話方塊以測試外觀和行為。|
|Format.ToggleGuides|**Ctrl**  + **G**|無格線、指導方針和方格之間的迴圈，無法進行對話方塊編輯。|

- 若要變更快速鍵，請移至 [功能表**工具**  >  **選項**]，然後選擇 [**環境**] 資料夾下的 [**鍵盤**]。

   如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 若要變更您的設定，請移至 [功能表**工具**匯  >  **入和匯出設定**]。

   對話方塊中可用的選項，以及您所看到功能表命令的名稱和位置，可能會與 [說明] 中描述 **的不同，視您** 使用的設定或版本而定。  如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[如何：建立對話方塊](../windows/creating-a-new-dialog-box.md)<br/>
[對話方塊控制項](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)-->
