---
title: 對話框編輯器 (C++)
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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370284"
---
# <a name="dialog-editor-c"></a>對話框編輯器 (C++)

**對話框編輯器**允許您創建或編輯對話方塊資源。

- 要打開編輯器,請在 **「資源檢視」** 視窗中按兩下對話方塊的 .rc 檔案,或轉到選單 **「查看** > **其他 Windows** > **資源檢視**」 。

創建新對話框或對話方塊範本的第一個步驟是添加控制項。 在**對話框編輯器**中,可以排列控制項以適合特定大小、形狀或對齊方式,也可以將它們移動到對話框中工作。 刪除控制項也很容易。

您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。

也可以編輯**對話框編輯器**中單個或多個控制項的屬性。 您可以更改選項卡順序,即按下**Tab**鍵時控制件獲得焦點的順序,也可以定義允許使用者使用鍵盤選擇控制項的存取鍵或鍵組合。

**對話框編輯器**還允許您使用自定義控制項,包括 ActiveX 控制件。 您可以編輯[面板檢視](../mfc/reference/cformview-class.md),[紀錄檢視](../data/record-views-mfc-data-access.md)或[對話框列](../mfc/dialog-bars.md)。

從 Visual Studio 2015 開始,可以使用**對話方塊編輯器**定義動態佈局,其中指定控制件在使用者調整對話框大小時如何移動和調整大小。 如需詳細資訊，請參閱 [Dynamic Layout](../mfc/dynamic-layout.md)。

有關資源的詳細資訊,請參閱如何[建立對話框](../windows/creating-a-new-dialog-box.md)與[對話方塊控制元件](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 在在許多情況下,使用**對話框編輯器**時,可以使用滑鼠右鍵選擇顯示常用命令的快捷菜單。

## <a name="dialog-editor-toolbar"></a>對話方塊編輯器工具列

**「對話框編輯器**」工具列包含用於排列對話框上控制件佈局的按鈕,例如大小和對齊方式。 **對話框編輯器**工具列按鈕對應於 **「格式」** 選單上的命令。

|圖示|意義|圖示|意義|
|----------|-------------|----------|-------------|
|![[測試對話方塊] 按鈕](../mfc/media/vcdialogeditortestdialog.png "vc 對話編輯器測試對話")|文字方塊|![[水平均等陳列] 按鈕](../mfc/media/vcdialogeditoracross.png "vc 對話編輯器")|橫向|
|![[對齊主控項的左緣] 按鈕](../mfc/media/vcdialogeditoralignlefts.png "vc 對話編輯器對齊左")|對齊主控項的左緣|![[垂直均等陳列] 按鈕](../mfc/media/vcdialogeditordown.png "vc 對話編輯器向下")|向下|
|![[對齊主控項的右緣] 按鈕](../mfc/media/vcdialogeditoralignrights.png "vc 對話編輯器對齊權利")|對齊主控項的右緣|![[設定成相同寬度] 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vc 對話編輯器相同寬度")|設定成相同寬度|
|![[對齊主控項的上緣] 按鈕](../mfc/media/vcdialogeditoraligntops.png "vc 對話編輯器對齊頂部")|對齊主控項的上緣|![[設定成相同高度] 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vc 對話編輯器使同一高度")|設定成相同高度|
|![[對齊主控項的下緣] 按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vc 對話編輯器對齊")|靠下對齊|![[設定成相同大小] 按鈕](../mfc/media/vcdialogeditorsamesize.png "vc 對話編輯器相同大小")|設定成相同大小|
|![[垂直置中] 按鈕](../mfc/media/vcdialogeditorvertical.png "vc 對話編輯器垂直")|Vertical|![[切換格線] 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vc 對話編輯器切換格線")|切換格線|
|![[水平置中] 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vc 對話編輯器水準")|水平|![[切換輔助線] 按鈕](../mfc/media/vcdialogeditortoggleguides.png "vc 對話編輯器切換指南")|切換輔助線|

- 要顯示或隱藏**對話框編輯器**工具列,請造訪選單 **「檢視** > **工具列** > **對話框編輯器**」。

在C++專案中打開**對話框編輯器**時,**對話框編輯器**工具列會自動顯示在解決方案的頂部,但是,如果顯式關閉工具列,則需要在下次打開**對話框編輯器**時調用它。 您可以通過從可用工具列和視窗清單中選擇它來切換其顯示。

## <a name="switch-between-dialog-box-controls-and-code"></a>在對話框控制器與代碼之間切換

在 MFC 應用程式中,可以按兩下對話方塊以跳轉到其處理程式碼或快速創建存根處理程式函數。

選擇控制項後,選擇「[屬性」視窗中](/visualstudio/ide/reference/properties-window)的 **「控制事件**」按鈕或 **「消息」** 按鈕,以查看可用於所選專案的 Windows 訊息和事件的完整清單。 從清單中選擇以建立或編輯處理程式函數。

- 要從**對話框編輯器**跳轉到代碼,請按兩下對話方塊中的控制項,以跳轉到聲明,使其最近實現的消息處理函數。

   對於基於 ATL 的對話方塊類,您始終跳轉到建構函數定義。

- 要檢視控制的事件,選擇控制項後,請選擇「**屬性**」視窗中的 **「控制事件**」按鈕。

   當單個控制器在對話框中具有焦點時,您可以右鍵單擊並選擇 **「添加事件處理程式**」 。。 這使您能夠指定向其添加處理程式的類。 有關詳細資訊,請參閱[新增事件處理程式](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 選擇 **「控制事件」** 按鈕,當對話方塊具有焦點時,將公開對話方塊中所有控制項的清單,然後可以展開該清單以編輯各個控制項的事件。

- 要檢視對話框的消息,選擇該對話框,請選擇「**屬性**」視窗中**的「消息」** 按鈕。

## <a name="accelerator-keys"></a>快速鍵

下面是**對話框編輯器**命令的預設快速鍵。  

|Command|索引鍵|描述|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **向下移** + **位元**|將所選控件的底部邊緣與主導控制項對齊。|
|Format.AlignCenters|**換檔** + **F9**|將所選控件的垂直中心與主導控制項對齊。|
|Format.AlignLefts|**Ctrl** + **向左** + **箭頭**移動|將所選控件的左邊緣與主導控制項對齊。|
|Format.AlignMiddles|**F9**|將所選控件的水準中心與主導控件對齊。|
|Format.AlignRights|**Ctrl** + 向右**箭頭****移位** + |將所選控件的右邊緣與主導控制項對齊。|
|Format.AlignTops|**Ctrl** + **向上移位** + **箭頭**|將所選控件的上邊緣與主導控制項對齊。|
|Format.ButtonBottom|**Ctrl** + **B**|沿對話框的底部中心放置所選按鈕。|
|Format.ButtonRight|**Ctrl** + **R**|將所選按鈕放在對話框的右上角。|
|Format.CenterHorizontal|**Ctrl** + **換檔** + **F9**|在對話框中水準居中控制件。|
|Format.CenterVertical|**Ctrl** + **F9**|控制元件垂直居中對話框中。|
|Format.CheckMnemonics|**Ctrl** + **M**|檢查助記符的獨特性。|
|格式.大小到內容|**換檔** + **F7**|調整所選控制的大小以適合標題文本。|
|Format.SpaceAcross|**Alt** + **左箭號**|水準均勻地放置所選控件。|
|Format.SpaceDown|**Alt** + **向下箭號**|垂直均勻地空間所選控件。|
|Format.TabOrder|**Ctrl** + **D**|設置對話框中控制件的順序。|
|Format.TestDialog|**Ctrl** + **T**|運行對話框以測試外觀和行為。|
|Format.ToggleGuides|**Ctrl** + **G**|在無網格、準則和網格之間迴圈以進行對話框編輯。|

- 要更改快捷鍵,請轉到菜單 **「工具** > **選項**」,然後選擇 **「環境」** 資料夾下的 **「鍵盤**」。

   如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 要更改設定,請轉到菜單 **「工具** > **匯入和匯出設置**」。

   對話框中可用的選項以及您看到的功能表命令的名稱和位置可能與 **「説明」** 中描述的選項不同,具體取決於您的活動設定或版本。  有關詳細資訊,請參閱[個人化可視化工作室 IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[如何:建立對話框](../windows/creating-a-new-dialog-box.md)<br/>
[對話框控制項](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
