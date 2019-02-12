---
title: 在對話方塊 （c + +） 上的控制項的排列方式 |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
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
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 210fbf8e062b4dd8c469f9c40a015bbc19bc2843
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152738"
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

#### <a name="to-size-a-group-of-controls-with-guides"></a>若要有輔助線大小的控制項群組

1. 貼齊輔助線 （或多個控制項） 的一端。

1. 拖曳的控制項 （或控制項） 的另一端的指南。

   視需要使用多個控制項，調整大小，每個貼齊至第二個指南。

1. 移動至控制項 （或控制項） 的大小是輔助線。

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要變更刻度的間隔

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊中，於**格線間距**欄位中，指定新的寬度和高度 Dlu 中。

### <a name="disable-guides"></a>停用輔助線

若要停用的貼齊輔助線效果，您可以搭配滑鼠使用特殊的索引鍵。 使用**Alt**金鑰會停用的貼齊選取快速入門的效果。 移動有的快速入門**Shift**金鑰可防止貼齊的控制項移動與指南。

#### <a name="to-disable-the-snapping-effect-of-the-guides"></a>若要停用的貼齊輔助線效果

將控制項拖曳時按住**Alt**索引鍵。

#### <a name="to-move-guides-without-moving-the-snapped-controls"></a>若要移動輔助線，而不移動貼齊的控制項

輔助線拖曳時按住**Shift**索引鍵。

#### <a name="to-turn-off-the-guides"></a>若要關閉指南

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊的 **版面配置輔助線**，選取**None**。

   > [!NOTE]
   > 您也可以按兩下 尺規 列，來存取**輔助線設定** 對話方塊。

\-或-

在 **格式**功能表上，選取**切換輔助線**。

### <a name="modify-the-layout-grid"></a>修改配置格線

當您放置或在對話方塊中排列控制項時，您可以使用版面配置方格的更精確的位置。 方格開啟時，控制項便會出現 「 貼齊 」 方格的虛線如同 magnetized。 您可以開啟和關閉此 「 貼齊至格線 」 功能，並變更版面配置方格資料格的大小。

#### <a name="to-turn-the-layout-grid-on-or-off"></a>若要開啟或關閉的版面配置方格

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定** 對話方塊中，選取或清除**格線** 按鈕。

   您仍可控制中個別的方格** 對話方塊**使用的編輯器視窗**切換格線**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

#### <a name="to-change-the-size-of-the-layout-grid"></a>若要變更版面配置方格的大小

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊方塊中，輸入的高度和寬度 Dlu 針對方格中的資料格。 最小高度或寬度是 4 Dlu。

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

## <a name="align-groups-of-controls"></a>對齊控制項群組

下列程序會示範如何將控制項對齊：

### <a name="to-align-groups-of-controls"></a>若要對齊控制項群組

1. [選取的控制項](../windows/selecting-multiple-controls.md)您想要對齊。 請務必選取您想要先做為主控制項的控制項或將它設為執行對齊或調整大小命令之前的主要控制項。

   控制項群組的最後一個位置是根據主控制項的位置而定。 如需有關選取主控項的詳細資訊，請參閱[指定主控項](../windows/specifying-the-dominant-control.md)。

1. 從**格式**功能表上，選擇**對齊**，然後選擇下列的對齊方式的其中一個：

   - `Lefts`： 將選取的控制項，沿著左邊對齊。

   - `Centers`： 將選取的控制項，沿著中心點的水平對齊。

   - `Rights`： 將選取的控制項，沿著右邊對齊。

   - `Tops`： 將選取的控制項，沿著上邊緣對齊。

   - `Middles`： 將選取的控制項，沿著垂直中間點對齊。

   - `Bottoms`： 將選取的控制項，沿著下邊緣對齊。

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

## <a name="change-the-tab-order-of-controls"></a>變更控制項的定位順序

定位順序是順序 **索引標籤**金鑰將輸入的焦點從一個控制項移至 對話方塊中的下一步。 通常是定位順序會繼續從左到右及從上到下一個對話方塊中。 每個控制項都**Tabstop**屬性，可決定控制項是否收到輸入的焦點。

### <a name="to-set-input-focus-for-a-control"></a>若要設定控制項的輸入的焦點

在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，選取 **，則為 True**或**False**中**Tabstop**屬性。

即使沒有的控制項**Tabstop**屬性設定為 **，則為 True**必須為定位順序的一部分。 定位順序很重要，比方說，當您[定義便捷鍵 （助憶鍵）](../windows/defining-mnemonics-access-keys.md)沒有標題的控制項。 定位順序中，包含相關的控制項的便捷鍵的靜態文字必須緊接著相關的控制項。

> [!NOTE]
> 如果您的對話方塊中包含重疊的控制項，變更索引標籤順序可能會變更控制項的顯示的方式。 定位順序中稍後出現的控制項一律會顯示任何重疊的控制項定位順序中前之上。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要檢視在對話方塊中的所有控制項目前的定位順序

在 **格式**功能表上，選取**定位順序**。

\-或-

- 按下**Ctrl** + **D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要變更在對話方塊中的所有控制項的定位順序

1. 在 **格式**功能表上，選取**定位順序**。

   在左上角的數字，每個控制項目前的定位順序中顯示它的位置。

1. 按一下您想要的順序的每個控制項設定定位順序 **索引標籤**遵循的索引鍵。

1. 按下**Enter**以結束**定位順序**模式。

   > [!TIP]
   > 一旦您輸入**定位順序**模式中，您可以按**Esc**或是**Enter**停用變更定位順序的能力。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要變更兩個或多個控制項的定位順序

1. 從**格式**功能表上，選擇**定位順序**。

1. 指定順序中的變更將會開始的位置。 第一次按住**Ctrl**索引鍵並選取控制項，然後選取您想的要變更的順序開始。

   比方說，如果您想要變更控制項的順序`7`經由`9`，按住**Ctrl**，然後選取 控制項`6`第一次。

   > [!NOTE]
   > 若要設定特定的控制項數目`1`（先在定位順序），連按兩下控制項。

1. 發行**Ctrl**鍵，然後選取您想要的順序的控制項** 索引標籤**遵循從該點的索引鍵。

1. 按下**Enter**以結束**定位順序**模式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)