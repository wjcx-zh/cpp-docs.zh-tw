---
title: 如何：排列控制項 （c + +） |Microsoft Docs
ms.date: 02/15/2019
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
ms.openlocfilehash: d9bd73c9cc81b113f222bbc090c62200c93554b2
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336627"
---
# <a name="how-to-arrange-controls-c"></a>如何：排列控制項 （c + +）

**對話方塊**編輯器提供版面配置工具，對齊，並自動調整控制項的大小。 對於大部分的工作，您可以使用[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**對話方塊編輯器**也會提供工具列命令**格式**功能表上，且大部分有[快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。

只有在已選取多個控制項時，才提供許多對話方塊的版面配置命令。 您可以選取單一控制項或多個控制項，並選取多個控制項時，您選取的第一個預設為 「 基準 」 控制項。 如需選取控制項和主控制項的資訊，請參閱[選取控制項](../windows/selecting-controls.md)。

位置、 高度和寬度目前控制項的會顯示狀態列右下角。 選取整個對話方塊時，狀態列會顯示為整體，其高度和寬度的對話方塊中的位置。

## <a name="guides-and-grids"></a>輔助線和格線

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

### <a name="to-create-edit-and-delete-guides-and-margins"></a>若要建立、 編輯和刪除輔助線和邊界

無論您要移動控制項，加入控制項，或重新排列目前的版面配置輔助線可以幫助您對齊正確的對話方塊內的控制項。 指南會以藍色的虛線顯示跨對應尺規上方，並沿著左側的箭號與編輯器中顯示的對話方塊**對話方塊**編輯器。

當您建立對話方塊中時，會提供四個邊界。 邊界是修改過的指南，顯示為藍色的虛線。 請參閱下列動作：

- 若要建立的指南，內尺規，請選取一次建立輔助線。 (按一下建立新指南; 按兩下 launch**輔助線設定**對話方塊中，您可以在其中指定輔助線設定。)

- 若要設定指南中，在對話方塊中，選取快速入門，並將它拖曳到新位置。 （您也可以選取箭號尺規，即可將相關聯的指南中。）本指南的座標會顯示在視窗底部的狀態列和尺規中的區段。 您可以將指標移到尺規，以顯示快速入門的確切位置中的箭號。

- 若要移動邊界，拖曳到新位置的邊界。 若要讓邊界消失，將邊界移到零的位置。 若要回復邊界，將指標放置於邊界的零位置，將邊界移到位置。

- 若要刪除輔助線，輔助線拖曳出對話方塊中，或拖曳離開尺規對應的箭號。

### <a name="to-align-controls-on-a-guide"></a>對齊輔助線上的控制項

當控制項不會移動，並輔助線嵌入式管理單元至控制項，如果不有任何先前貼齊輔助線的控制項，控制項的調整大小控點就貼齊格線。 當移動時的指南時，會貼齊至它的控制項就會一併移動。 當其中一個指南移動，則會調整大小貼齊至一個或多個指南的控制項。

對話方塊單位 (Dlu) 會定義中判斷的間距輔助線和控制項的尺規的刻度標記。 DLU 根據對話方塊字型，通常 8-point MS Shell Dlg 的大小。 水平 DLU 是除以四對話方塊字型的平均寬度。 垂直 DLU 是平均除以八字型的高度。

#### <a name="to-size-a-group-of-controls-with-guides"></a>若要有輔助線大小的控制項群組

1. 貼齊輔助線 （或多個控制項） 的一端。

1. 拖曳的控制項 （或控制項） 的另一端的指南。

   視需要使用多個控制項，調整大小，每個貼齊至第二個指南。

1. 移動至控制項 （或控制項） 的大小是輔助線。

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要變更刻度的間隔

從**格式**功能表上，選擇**輔助線設定**，然後在**格線間距**欄位中，指定在 Dlu 中的新寬度和高度。

### <a name="to-disable-guides"></a>若要停用輔助線

若要停用的貼齊輔助線效果，您可以搭配滑鼠使用特殊的索引鍵。 使用**Alt**金鑰會停用的貼齊選取快速入門的效果。 移動有的快速入門**Shift**金鑰可防止貼齊的控制項移動與指南。

- 若要停用的貼齊輔助線效果，請將控制項拖曳時按住**Alt**索引鍵。

- 若要移動輔助線，而不移動貼齊的控制項，將輔助線拖曳時按住**Shift**索引鍵。

- 若要關閉指南中，從**格式**功能表上，選擇**輔助線設定**。 然後在**輔助線設定**對話方塊的 **版面配置輔助線**，選取**None**。

   > [!NOTE]
   > 您也可以按兩下 尺規 列，來存取**輔助線設定** 對話方塊。

> [!TIP]
> 若要關閉指南的捷徑位於**格式**功能表上，選取**切換輔助線**。

### <a name="to-modify-the-layout-grid"></a>若要修改配置格線

當您放置或在對話方塊中排列控制項時，您可以使用版面配置方格的更精確的位置。 方格開啟時，控制項便會出現 「 貼齊 」 方格的虛線如同 magnetized。 您可以開啟和關閉此 「 貼齊至格線 」 功能，並變更版面配置方格資料格的大小。

- 若要開啟或關閉，版面配置方格從**格式**功能表上，選擇**輔助線設定**，然後選取或清除**方格** 按鈕。

   您仍可控制中個別的方格**對話方塊**使用的編輯器視窗**切換格線**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

- 若要變更大小的版面配置方格中，從**格式**功能表上，選擇**輔助線設定**，然後輸入的高度和寬度 Dlu 方格中的資料格。 最小高度或寬度是 4 Dlu。

## <a name="select-controls"></a>選取控制項

選取控制項來調整大小、 對齊、 移動、 複製或刪除它們，然後完成您要的作業。 在大部分情況下，您必須選取要使用的調整大小和對齊工具上的多個控制項[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

當控制項被選取時，它具有實線 (active）) 其周圍的灰色的框線或中空 （非作用中） 「 調整大小控點，「 小方塊，會出現在選取範圍框線。 選取多個控制項時，主控制項有穩固的調整大小控點，而且所有其他選取的控制項有空心的調整大小控點。

當您調整大小或對齊多個控制項， **對話方塊**編輯器會使用 「 主控制項 」 來判斷如何調整大小或對齊其他控制項。 根據預設，主控制項是第一個選取的控制項。

### <a name="to-select-controls"></a>若要選取控制項

1. 在  [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)，選取**指標**工具。

1. 使用其中一個下列的步驟，讓您的選擇：

   - 拖曳指標以繪製您想要在您的對話方塊中選取的控制項周圍的選取方塊。 當您放開滑鼠按鈕時，所有控制項內、 交集與選取方塊已選取。

   - 按住**Shift**鍵並選取您想要在選取項目中包含的控制項。

   - 按住**Ctrl**鍵並選取您想要在選取項目中包含的控制項。

1. 若要新增或移除控制項，從選取的控制項群組，請按住**Shift**鍵並選取您想要新增或移除的控制項。

> [!NOTE]
> 按住**Ctrl**索引鍵，然後選取 選取範圍內的控制項將此控制項主控該選取項目中。

### <a name="to-select-a-dominant-control"></a>若要選取的主控制項

- 若要指定主控項的控制項，請按住**Ctrl**鍵並選取您想要的大小或其他控制項的位置會影響的控制項*第一個*。

- 若要變更主控，清除目前的選取範圍以外的所有目前選取的控制項選取並重複先前的程序，第一次選取不同的控制項。

> [!NOTE]
> 空心下層控制項的控制代碼時，主控項的調整大小控點是純色。 所有進一步調整大小或對齊根據主控制項。

## <a name="size-controls"></a>控制項的大小

您可以使用調整大小控點來調整控制項大小。 當指標位於其上的縮放控點時，它會變更形狀，以表示控制項可以在其中調整大小的指示。 作用中的縮放控點是純色和控制項如果空心的縮放控點，無法調整大小的軸。

> [!TIP]
> 您也可以藉由貼齊輔助線或邊界，以控制變更控制項大小或移動其中一個貼齊控制項和輔助線與另一個。

### <a name="to-size-a-control"></a>若要調整控制項的大小

1. 選取的控制項。

1. 拖曳調整大小控點，若要變更控制項的大小：

   - 在頂端和側邊的大小控點會變更水平或垂直大小。

   - 邊角大小控點會變更水平和垂直大小。

   > [!TIP]
   > 一次調整控制項的一個對話方塊單位 (DLU) 大小按住**Shift**鍵並使用**右**並**向下**方向鍵。

> [!TIP]
> 若要自動調整大小以容納內文字的控制項，開啟**格式** 功能表或以滑鼠右鍵按一下控制項，然後選擇**依內容調整大小**。

### <a name="to-make-controls-the-same-size"></a>若要將控制項設為相同的大小

您可以調整大小一的組控制項以主控項的大小。

1. 選取您想要調整大小的控制項。

   第一次選取數列中的控制項是主要的控制項。 群組中控制項的最終大小取決於主控制項的大小。

1. 從**格式**功能表上，選擇**成相同大小**，然後選擇 **兩者**，**高度**，或**寬度**.

### <a name="combo-box"></a>下拉式方塊

當您將它新增至對話方塊中，您可以調整大小的下拉式方塊。 您也可以指定下拉式清單方塊的大小。 如需詳細資訊，請參閱 <<c0> [ 新增至下拉式方塊控制項的值](../windows/adding-values-to-a-combo-box-control.md)。

1. 選取右邊的下拉式方塊的下拉箭號按鈕。

   ![在 MFC 專案下拉式方塊上的箭號](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控制變更，以顯示下拉式方塊的大小與擴充的下拉式清單中區域的外框。

1. 您可以使用較低的調整大小控點，變更下拉式清單 區域的初始大小。

   ![下拉式方塊&#45;MFC 專案中的方塊縮放](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 選取下拉式箭號，以關閉下拉式方塊的下拉式清單部分。

### <a name="horizontal-scroll-bar"></a>水平捲軸

當您使用 MFC 類別的對話方塊中新增具有水平捲軸的清單方塊時，捲軸不會自動出現在您的應用程式。

藉由呼叫設定的最寬的項目最大寬度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)程式碼中。 沒有設定這個值，捲軸不會出現，即使當清單方塊中的項目都超出 方塊中。

## <a name="align-controls"></a>對齊控制項

1. 選取您想要對齊的控制項。 請務必選取您想要先主控項的控制項或將它設為執行對齊或調整大小命令之前的主要控制項。

   控制項群組的最後一個位置是根據主控制項的位置而定。

1. 從**格式**功能表上，選擇**對齊**，然後選擇下列的對齊方式的其中一個：

   |對齊|描述|
   |-----|-----------|
   |`Lefts`|將選取的控制項沿著左邊對齊。|
   |`Centers`|將選取的控制項沿著中心點的水平對齊。|
   |`Rights`|將沿著右邊選取的控制項對齊。|
   |`Tops`|將選取的控制項以及它們的上邊緣對齊。|
   |`Middles`|將選取的控制項，沿著垂直中間點的對齊。|
   |`Bottoms`|將選取的控制項沿著下邊緣對齊。|

### <a name="to-even-spacing-between-controls"></a>甚至控制項之間的間距

**對話方塊**編輯器可讓您選取的最外層的控制項之間的平均空間控制項。

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**均等空格**，然後選擇下列間距對齊方式的其中一個：

   |間距|描述|
   |---|---|
   |`Across`|最左邊和右邊選取的控制項之間的平均空間控制項。|
   |`Down`|最頂端和底部選取的控制項之間的平均空間控制項。|

### <a name="to-center-controls"></a>若要控制項置中

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**對齊對話方塊中央**，然後選擇下列的排列方式的其中一個：

   |排列方式|描述|
   |---|---|
   |`Vertical`|控制項在對話方塊中，垂直置中。|
   |`Horizontal`|控制項在對話方塊中的水平置中。|

### <a name="to-arrange-push-buttons"></a>若要排列按鈕

1. 選取一或多個按鈕。

1. 從**格式**功能表上，選擇**排列按鈕**，然後選擇下列的排列方式的其中一個：

   |排列方式|描述|
   |---|---|
   |`Right`|對齊按鈕的對話方塊中的右邊緣。|
   |`Bottom`|對齊對話方塊中的下邊緣的按鈕。|

   如果您選取按鈕以外的控制項，其位置不受影響。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)