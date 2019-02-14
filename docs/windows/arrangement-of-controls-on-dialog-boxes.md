---
title: 在對話方塊 （c + +） 上的控制項的排列方式 |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 99667898428fe9532d59277bfedafd24927304dc
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264877"
---
# <a name="arrangement-of-controls-on-dialog-boxes-c"></a>在對話方塊 （c + +） 上的控制項的排列方式

** 對話方塊**編輯器提供版面配置工具，對齊，並自動調整控制項的大小。 對於大部分的工作，您可以使用[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**對話方塊編輯器**也會提供工具列命令**格式**功能表上，且大部分有[快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。

只有在已選取多個控制項時，才提供許多對話方塊的版面配置命令。 您可以選取單一控制項或多個控制項，並選取多個控制項時，您選取的第一個預設為 「 基準 」 控制項。 如需選取控制項和主控制項的資訊，請參閱[選取控制項](../windows/selecting-controls.md)。

位置、 高度和寬度目前控制項的會顯示狀態列右下角。 選取整個對話方塊時，狀態列會顯示為整體，其高度和寬度的對話方塊中的位置。

## <a name="dialog-editor-states-guides-and-grids"></a>對話方塊編輯器狀態 （輔助線和格線）

您可以使用對話方塊上的控制項排列 **對話方塊**編輯器中的三個不同的狀態：

- 使用輔助線和邊界的 （預設值）

- 上的配置格線

- 不需要任何貼齊 」 或 「 對齊 」 功能

[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制項狀態的按鈕。 若要變更狀態，請選取適當的圖示。 您也可以藉由變更狀態**輔助線設定**命令**格式**功能表。

**輔助線設定**對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**版面配置輔助線**|顯示版面配置輔助線設定。|
|**無**|隱藏配置工具。|
|**尺規和輔助線**|啟用時，加入尺規版面配置工具;指南可置於尺規。 預設指南是邊界，也可以藉由拖曳移動。 選取要放置指南尺規。 控制 「 貼齊 」 指南上方或旁邊移動控制項時。 控制項也會一起移動指南之後，它們會附加到它。 當控制項所附加至每一端的指南，並移動輔助線時，控制項會調整大小。|
|**格線**|建立版面配置方格。 新的控制項將自動貼齊格線。|
|**格線間距**|對話方塊單位 (Dlu) 中，會顯示格線間距的設定。|
|**Width:Dlu**|Dlu 中設定版面配置方格的寬度。 水平 DLU 是除以四對話方塊字型的平均寬度。|
|**Height:Dlu**|Dlu 中設定版面配置方格的高度。 垂直 DLU 是平均除以八個對話方塊字型的高度。|

### <a name="create-and-set-guides-and-margins"></a>建立並設定輔助線和邊界

無論您要移動控制項，加入控制項，或重新排列目前的版面配置輔助線可以幫助您對齊正確的對話方塊內的控制項。 指南會以藍色的虛線顯示跨對應尺規上方，並沿著左側的箭號與編輯器中顯示的對話方塊** 對話方塊**編輯器。

當您建立對話方塊中時，會提供四個邊界。 邊界是修改過的指南，顯示為藍色的虛線。

|處理序|步驟|
|----------------|----------------|
|若要建立的指南|在尺規，請選取一次建立輔助線。 (按一下建立新指南; 按兩下 launch**輔助線設定**對話方塊中，您可以在其中指定輔助線設定。)|
|若要設定指南|在對話方塊中，按一下快速入門，並將它拖曳到新位置。 （您也可以按一下尺規，即可將相關聯的指南中的箭號）。<br/><br/>本指南的座標會顯示在視窗底部的狀態列和尺規中的區段。 您可以將指標移到尺規，以顯示快速入門的確切位置中的箭號。|
|若要刪除輔助線|輔助線拖曳立即可用的對話方塊。<br/><br/>\-或-<br/><br/>拖曳對應的箭號，離開尺規。|
|若要移動邊界|拖曳到新位置的邊界。<br/><br/>若要讓邊界消失，將邊界移到零的位置。 若要回復邊界，將指標放置於邊界的零位置，將邊界移到位置。|

### <a name="align-controls-on-a-guide"></a>對齊輔助線上的控制項

當控制項不會移動，並輔助線嵌入式管理單元至控制項，如果不有任何先前貼齊輔助線的控制項，控制項的調整大小控點就貼齊格線。 當移動時的指南時，會貼齊至它的控制項就會一併移動。 當其中一個指南移動，則會調整大小貼齊至一個或多個指南的控制項。

對話方塊單位 (Dlu) 會定義中判斷的間距輔助線和控制項的尺規的刻度標記。 DLU 根據對話方塊字型，通常 8-point MS Shell Dlg 的大小。 水平 DLU 是除以四對話方塊字型的平均寬度。 垂直 DLU 是平均除以八字型的高度。

若要快取大小的一組控制項與輔助線：

1. 貼齊輔助線 （或多個控制項） 的一端。

1. 拖曳的控制項 （或控制項） 的另一端的指南。

   視需要使用多個控制項，調整大小，每個貼齊至第二個指南。

1. 移動至控制項 （或控制項） 的大小是輔助線。

若要變更刻度的間隔：

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊中，於**格線間距**欄位中，指定新的寬度和高度 Dlu 中。

### <a name="disable-guides"></a>停用輔助線

若要停用的貼齊輔助線效果，您可以搭配滑鼠使用特殊的索引鍵。 使用**Alt**金鑰會停用的貼齊選取快速入門的效果。 移動有的快速入門**Shift**金鑰可防止貼齊的控制項移動與指南。

- 若要停用的貼齊輔助線效果，請將控制項拖曳時按住**Alt**索引鍵。

- 若要移動輔助線，而不移動貼齊的控制項，將輔助線拖曳時按住**Shift**索引鍵。

- 若要關閉指南中，從**格式**功能表上，選擇**輔助線設定**。 然後在**輔助線設定**對話方塊的 **版面配置輔助線**，選取**None**。

   > [!NOTE]
   > 您也可以按兩下 尺規 列，來存取**輔助線設定** 對話方塊。

> [!TIP]
> 若要關閉指南的捷徑位於**格式**功能表上，選取**切換輔助線**。

### <a name="modify-the-layout-grid"></a>修改配置格線

當您放置或在對話方塊中排列控制項時，您可以使用版面配置方格的更精確的位置。 方格開啟時，控制項便會出現 「 貼齊 」 方格的虛線如同 magnetized。 您可以開啟和關閉此 「 貼齊至格線 」 功能，並變更版面配置方格資料格的大小。

若要開啟或關閉，請開啟 版面配置方格：

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定** 對話方塊中，選取或清除**格線** 按鈕。

   您仍可控制中個別的方格** 對話方塊**使用的編輯器視窗**切換格線**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

若要變更的版面配置方格大小：

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊方塊中，輸入的高度和寬度 Dlu 針對方格中的資料格。 最小高度或寬度是 4 Dlu。

## <a name="selecting-controls"></a>選取控制項

選取控制項來調整大小、 對齊、 移動、 複製或刪除它們，然後完成您要的作業。 在大部分情況下，您必須選取要使用的調整大小和對齊工具上的多個控制項[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

當控制項被選取時，它具有實線 (active）) 其周圍的灰色的框線或中空 （非作用中） 「 調整大小控點，「 小方塊，會出現在選取範圍框線。 選取多個控制項時，主控制項有穩固的調整大小控點，而且所有其他選取的控制項有空心的調整大小控點。

當您調整大小或對齊多個控制項， ** 對話方塊**編輯器會使用 「 主控制項 」 來判斷如何調整大小或對齊其他控制項。 根據預設，主控制項是第一個選取的控制項。

### <a name="to-select-multiple-controls"></a>若要選取多個控制項

1. 在  [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)，選取**指標**工具。

1. 使用其中一個下列的步驟，讓您的選擇：

   - 拖曳指標以繪製您想要在您的對話方塊中選取的控制項周圍的選取方塊。 當您放開滑鼠按鈕時，所有控制項內、 交集與選取方塊已選取。

   - 按住**Shift**鍵並選取您想要在選取項目中包含的控制項。

   - 按住**Ctrl**鍵並選取您想要在選取項目中包含的控制項。

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要移除的一組選取的控制項的控制項，或將控制項新增至選取的控制項的群組

使用選取的控制項群組，請按住**Shift**鍵並選取您想要移除或加入到現有的選取範圍的控制項。

   > [!NOTE]
   > 按住**Ctrl**索引鍵，然後選取 選取範圍內的控制項將此控制項主控該選取項目中。

### <a name="to-specify-the-dominant-control"></a>若要指定主控項

按住**Ctrl**鍵並選取您想要的大小或其他控制項的位置會影響的控制項*第一個*。

> [!NOTE]
> 空心下層控制項的控制代碼時，主控項的調整大小控點是純色。 所有進一步調整大小或對齊根據主控制項。

### <a name="to-change-the-dominant-control"></a>若要變更主控項

1. 所有目前選取的控制項外按一下，以清除目前的選取範圍。

1. 重複上一個程序，第一次選取不同的控制項。

## <a name="sizing-controls"></a>調整控制項的大小

您可以使用調整大小控點來調整控制項大小。 當指標位於其上的縮放控點時，它會變更形狀，以表示控制項可以在其中調整大小的指示。 作用中的縮放控點是純色;如果空心的縮放控點，則無法調整大小控制該軸。

您也可以藉由貼齊輔助線或邊界，以控制變更控制項大小或移動其中一個貼齊控制項和輔助線與另一個。

### <a name="to-size-an-individual-control"></a>若要個別控制項的大小

1. 選取的控制項。

1. 拖曳調整大小控點，若要變更控制項的大小：

   - 在頂端和側邊的調整大小控點會變更水平或垂直大小。

   - 邊角調整大小控點會變更水平和垂直大小。

   > [!TIP]
   > 一次調整控制項的一個對話方塊單位 (DLU) 大小按住**Shift**鍵並使用**向右箭號**並**向下箭號**索引鍵。

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自動調整大小以容納內文字的控制項

選擇**內容的大小**從**格式**功能表或以滑鼠右鍵按一下控制項，然後選擇**依內容調整大小**從捷徑功能表。

### <a name="to-make-controls-the-same-width-height-or-size"></a>若要讓控制項相同的寬度、 高度或大小

您可以調整大小一的組控制項以主控項的大小。

1. 選取您想要調整大小的控制項。

   第一次選取數列中的控制項是主要的控制項。 群組中控制項的最終大小取決於主控制項的大小。

1. 從**格式**功能表上，選擇**成相同大小**，然後選擇**兩者**，**高度**，或**寬度**。

### <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>若要設定大小的下拉式方塊和下拉式清單

當您將它新增至對話方塊中，您可以調整大小的下拉式方塊。 您也可以指定下拉式清單方塊的大小。 如需詳細資訊，請參閱 <<c0> [ 新增至下拉式方塊控制項的值](../windows/adding-values-to-a-combo-box-control.md)。

#### <a name="to-size-a-combo-box"></a>若要調整大小的下拉式方塊

1. 在您的對話方塊中，選取下拉式方塊控制項。

   一開始僅左邊和右邊的調整大小控點會有作用中。

1. 您可以使用調整大小控點來設定下拉式方塊的寬度。

您也可以設定下拉式方塊的下拉式部分的垂直大小。

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>若要設定大小的下拉式方塊的下拉式清單

1. 選取右邊的下拉式方塊的下拉箭號按鈕。

   ![在 MFC 專案下拉式方塊上的箭號](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控制變更，以顯示下拉式方塊的大小與擴充的下拉式清單中區域的外框。

1. 您可以使用較低的調整大小控點，變更下拉式清單 區域的初始大小。

   ![下拉式方塊&#45;MFC 專案中的方塊縮放](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 選取下拉式箭號，以關閉下拉式方塊的下拉式清單部分。

### <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>設定水平捲軸的寬度，並讓它出現

當您使用 MFC 類別的對話方塊中新增具有水平捲軸的清單方塊時，捲軸不會自動出現在您的應用程式。

藉由呼叫設定的最寬的項目最大寬度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)程式碼中。

   沒有設定這個值，捲軸不會出現，即使當清單方塊中的項目都超出 方塊中。

## <a name="group-radio-buttons-on-a-dialog-box"></a>在對話方塊中的群組選項按鈕

當您新增到對話方塊中的選項按鈕時，將它們視為一組藉由設定**群組**中的屬性**屬性**群組中的第一個按鈕的視窗。 然後，這個選項按鈕的控制項識別碼就會出現在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，讓您為選項按鈕群組加入成員變數。

對話方塊中可以有多個選項按鈕群組，但加入每個群組時請一定要使用下列程序。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>在對話方塊中加入選項按鈕群組

1. 選取選項按鈕控制項中的[[工具箱] 視窗](/visualstudio/ide/reference/toolbox)，並選擇您要放置控制項的對話方塊中的位置。

1. 重複步驟 1 加入您需要的數量無限的選項按鈕。 請確定群組中的選項按鈕是連續的定位順序。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，請將定位順序 **第一** 之選項按鈕的 [群組]  屬性設為 **True**。

   將 [群組]  屬性變更成 **True** ，可在資源指令碼之對話方塊物件的按鈕項目中加入 WS_GROUP 樣式，確保使用者在按鈕群組中一次只能選取一個選項按鈕 (當使用者按一下某個選項按鈕時，就會清除群組中的其他按鈕)。

   > [!NOTE]
   > 群組中，應該只有第一個選項按鈕的 [群組]  屬性設為 **True**。 如果有不屬於按鈕群組的其他控制項，請將 **群組之外** 第一個控制項的 [群組]  屬性也設成 **True** 。 按下，您可以快速識別群組之外的第一個控制項**Ctrl**+**D**檢視 索引標籤順序。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>加入選項按鈕群組的成員變數

1. 以滑鼠右鍵按一下定位順序第一的選項按鈕控制項 (主控項和 [群組]  屬性設為 True 的控制項)。

1. 從快顯功能表選擇 [加入變數]  。

1. 在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，選取 [控制項變數]  核取方塊，然後選取 [值]  選項按鈕。

1. 在 [變數名稱]  方塊中，輸入新成員變數的名稱。

1. 在 **變數的型別**清單方塊中，選取**int**或型別`int`。

1. 您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 比方說，`m_radioBox1 = 0;`會選取第一個選項按鈕群組中。

## <a name="to-align-groups-of-controls"></a>若要對齊控制項群組

1. 選取您想要對齊的控制項。 請務必選取您想要先做為主控制項的控制項或將它設為執行對齊或調整大小命令之前的主要控制項。

   控制項群組的最後一個位置是根據主控制項的位置而定。 如需有關選取主控項的詳細資訊，請參閱[指定主控項](../windows/specifying-the-dominant-control.md)。

1. 從**格式**功能表上，選擇**對齊**，然後選擇下列的對齊方式的其中一個：

   |值|描述|
   |-----|-----------|
   |`Lefts`|將選取的控制項沿著左邊對齊。|
   |`Centers`|將選取的控制項沿著中心點的水平對齊。|
   |`Rights`|將沿著右邊選取的控制項對齊。|
   |`Tops`|將選取的控制項以及它們的上邊緣對齊。|
   |`Middles`|將選取的控制項，沿著垂直中間點的對齊。|
   |`Bottoms`|將選取的控制項沿著下邊緣對齊。|

### <a name="to-even-the-spacing-between-controls"></a>若要均等控制項之間的間距

** 對話方塊**編輯器可讓您選取的最外層的控制項之間的平均空間控制項。

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**均等空格**，然後選擇下列間距對齊方式的其中一個：

   - `Across`： 空間平均之間最左邊和右邊的控制項選取的控制項。

   - `Down`： 空間平均之間的最上層和選取的最下層控制項的控制項。

### <a name="to-center-controls-in-a-dialog-box"></a>若要在對話方塊中的控制項置中

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**對齊對話方塊中央**，然後選擇下列的排列方式的其中一個：

   - `Vertical`： 控制項在對話方塊中，垂直置中。

   - `Horizontal`： 控制項在對話方塊中的水平置中。

### <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>若要沿著右側或對話方塊的底部排列按鈕

1. 選取一或多個按鈕。

1. 從**格式**功能表上，選擇**排列按鈕**，然後選擇下列的排列方式的其中一個：

   - `Right`： 沿著對話方塊的右邊緣對齊按鈕。

   - `Bottom`： 對齊按鈕的對話方塊中的下邊緣。

       如果您選取按鈕以外的控制項，其位置不受影響。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)