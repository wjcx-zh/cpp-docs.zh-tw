---
title: 如何：配置控制項 (c + +) |Microsoft Docs
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
ms.openlocfilehash: ac21096f18b1331759f9bf7dfe613100298b7296
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509666"
---
# <a name="how-to-layout-controls-c"></a>如何：配置控制項 (c + +) 

**對話方塊編輯器**會提供自動對齊及調整控制項大小的版面組態工具。 針對大部分的工作，您可以使用 [對話方塊編輯器工具列](./dialog-editor.md)。 所有 **對話方塊編輯器** 工具列命令也可在 [ **格式** ] 功能表上取得，而且大部分都有 [快速鍵](./dialog-editor.md)。

只有當選取了一個以上的控制項時，對話方塊的許多版面配置命令才能使用。 您可以選取單一控制項或多個控制項，如果選取了一個以上的控制項，則您選取的第一個控制項預設會是主控制項。

目前控制項的位置、高度和寬度會顯示在狀態列的右下角。 選取整個對話方塊時，狀態列會顯示整個對話方塊的位置，以及其高度和寬度。

## <a name="arrange-controls"></a>排列控制項

您可以使用 **對話方塊編輯器** ，以三種不同的狀態來排列對話方塊的控制項：

- 在上使用輔助線和邊界，設定為預設值。

- 使用版面配置方格。

- 沒有任何貼齊或對齊功能。

[對話方塊編輯器工具列](./dialog-editor.md)包含控制狀態的按鈕。

- 若要變更狀態，請選取適當的圖示，或移至 [功能表**格式**  >  **指南設定**]。

[ **指南設定** ] 對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**版面配置輔助線**|顯示版面配置輔助線的設定。|
|**None**|隱藏版面組態工具。|
|**尺規和輔助線**|啟用時，會將尺規加入至版面組態工具，並允許在尺規中放置輔助線。 預設的輔助線是邊界。|
|**方格**|建立版面配置方格。 新的控制項會自動對齊格線。|
|**格線間距**|顯示對話方塊單位中， (Dlu) 之方格間距的設定。|
|**寬度： Dlu**|設定以 Dlu 為單位之版面配置方格的寬度。 水準 DLU 是對話方塊字型的平均寬度除以4。|
|**Height： Dlu**|設定以 Dlu 為單位的版面配置方格高度。 垂直 DLU 是對話方塊字型除以8的平均高度。|

### <a name="guides-and-margins"></a>輔助線和邊界

無論您是要移動控制項、加入控制項，還是重新排列目前的版面配置、輔助線和邊界，都能協助您在對話方塊內精確地對齊控制項。

當您建立對話方塊時，會提供四個修改過的輔助線，並顯示為藍色虛線。

- 若要移動邊界，請將邊界拖曳至新的位置。

- 若要讓邊界消失，請將邊界移至零的位置。

- 若要恢復邊界，請將指標放在邊界的零位置，然後將邊界移至位置。

輔助線會顯示為編輯器中顯示的藍色虛線，以及頂端和 **對話方塊編輯器**左邊尺規中的對應箭號。 當移動控制項時，控制項的調整大小控點會對齊輔助線，而如果沒有任何控制項先前已貼齊至本指南，則為控制項對齊線。 移動輔助線時，貼齊的控制項也會移動。 移至多個指南的控制項，會在其中一個輔助線移動時調整大小。

- 若要在尺規內建立節目表，請選取 [一次] 建立節目表，或按兩下以啟動 [ **節目表設定** ] 對話方塊，您可以在其中指定節目表設定。

- 若要在對話方塊上設定節目表，請選取 [節目表] 並將它拖曳至新的位置，或選取尺規中的箭號，以拖曳相關聯的指南。

   本指南的座標會顯示在視窗底部的狀態列中與尺規中，或將指標移至尺規的箭號上方，以顯示指南的確切位置。

- 若要刪除節目表，請從對話方塊拖曳輔助線，或將對應的箭號拖曳至尺規之外。

尺規中用來決定輔助線和控制項間距的刻度標記，是由對話單位（ (Dlu) ）所定義。 DLU 是以對話方塊字型的大小為基礎，通常是8點的 MS Shell Dlg。 水準 DLU 是依四個對話方塊字型的平均寬度。 垂直 DLU 是將字型除以8的平均高度。

- 若要變更刻度的間隔，請移至 [功能表**格式**  >  **指南設定**]，然後在 [**格線間距**] 欄位中，指定以 dlu 為單位的新寬度和高度。

### <a name="layout-grid"></a>版面配置方格

當您在對話方塊中放置或排列控制項時，請使用版面配置方格來進行更精確的定位。 當格線開啟時，控制項就會貼齊方格的虛線，如同 magnetized。

- 若要開啟或關閉版面配置方格，請移至 [功能表**格式**  >  **指南設定**]，然後選取或清除**格線**按鈕。

   您仍然可以在 [[對話方塊編輯器] 工具列](./dialog-editor.md)上，使用 [**切換格線**] 按鈕來控制個別**對話方塊編輯器**視窗中的方格。

- 若要變更版面配置方格的大小，請移至 [功能表**格式**  >  **指南設定**]，然後針對方格中的儲存格輸入以 dlu 為單位的高度和寬度。 最小高度或寬度為4。

### <a name="disable-guides"></a>停用輔助線

您可以搭配使用特殊按鍵與滑鼠，以停用這些指南的貼齊效果。 使用 **Alt** 鍵會停用所選指南的貼齊效果。 使用 **Shift** 鍵移動節目表，可防止貼齊的控制項與本指南一起移動。

- 若要停用輔助線的貼齊效果，請在按住 **Alt** 鍵時拖曳控制項。

- 若要移動輔助線而不移動已貼齊的控制項，請在按住 **Shift** 鍵時拖曳輔助線。

- 若要關閉指南，請移至 [功能表**格式**  >  **指南設定**]。 然後，在 [ **版面配置指南**] 下，選取 [ **無**]。

   > [!TIP]
   > 您也可以使用功能表**格式**  >  **切換指南**中的快捷方式。

## <a name="select-controls"></a>選取控制項

選取要調整大小、對齊、移動、複製或刪除的控制項，然後完成您想要的操作。 在大多數情況下，您需要選取一個以上的控制項，以使用 [對話方塊編輯器工具列](./dialog-editor.md)上的 [調整大小] 和 [對齊] 工具。

選取控制項時，它周圍會有以實線 (作用中的) 或空心 (非使用中的) 調整大小控點，也就是出現在選取框線中的小方塊。 選取多個控制項時，主控制項會有實心的調整大小控點，而所有其他選取的控制項都有空心調整大小控點。

- 若要選取控制項，請在 [ [工具箱] 視窗](/visualstudio/ide/reference/toolbox)中選取 [ **指標** ] 工具，然後使用下列其中一個步驟來進行選取：

  - 將指標拖曳至您想要在對話方塊中選取的控制項周圍的選取方塊。 當您放開滑鼠按鍵時，會選取選取方塊內和相交的所有控制項。

  - 按住 **Shift** 鍵，然後選取您想要包含在選取範圍內的控制項。

  - 按住 **Ctrl** 鍵，然後選取您想要包含在選取範圍內的控制項。

- 若要在選取的控制項群組中新增或移除控制項，請按住 **Shift** 鍵，然後選取您要新增或移除的控制項。

### <a name="dominant-controls"></a>主控制項

當您將多個控制項調整大小或對齊時， **對話方塊編輯器** 會使用主控制項來判斷其他控制項如何調整大小或對齊。 依預設，主控制項是選取的第一個控制項。

- 若要指定主控制項，請按住 **Ctrl** 鍵，然後選取您想要使用的控制項，以 *先*影響其他控制項的大小或位置。 按住 **Ctrl** 鍵並選取選取範圍內的控制項，也會讓控制項成為該選取範圍中的主控制項。

- 若要變更主控制項，請在所有目前選取的控制項之外選取，以清除目前的選取範圍，然後重複上述程式， *先*選取不同的控制項。

> [!NOTE]
> 主控制項的調整大小控點是純量，而次級控制項的控制碼是空心的。 所有進一步的調整大小或對齊都是以主控制項為基礎。

## <a name="size-controls"></a>大小控制項

使用調整大小控點來調整控制項的大小。 當指標定位在調整大小控點上時，它會變更圖形來指出控制項可以調整大小的方向。 作用中的調整大小控點是實線，如果調整大小控點是空心的，則無法沿著該軸調整控制項的大小。

- 若要調整控制項的大小，請選取控制項，然後拖曳調整大小控點來變更大小。

  - 頂端和側邊的大小控點會變更水準或垂直大小。

  - 角落的大小控點會變更水準和垂直大小。

   > [!TIP]
   > 您可以按住 **Shift** 鍵並使用 **向右鍵** 和 **向下** 鍵，將控制項一次調整為一個對話單位 (DLU) 。

- 若要自動調整控制項的大小以符合其內的文字，請移至功能表 **格式** 或以滑鼠右鍵按一下控制項，然後選擇 [ **內容大小**]。

- 若要讓控制項的大小相同，請選取您想要調整大小的控制項，並移至 [功能表**格式**] 的  >  **相同大小**，然後選擇 [**兩者**]、[**高度**] 或 [**寬度**]。

   您可以根據主控制項的大小調整控制項群組的大小，也就是在數列中第一個選取的控制項。 群組中控制項的最終大小取決於主控制項的大小。

- 若要使用輔助線來調整控制項群組的大小，請將控制項的一端貼齊 (或控制項) 至輔助線，然後將 [節目表] 拖曳至控制項的另一端 (或控制項) 。 現在您可以移動任一個指南，將控制項的大小 (或控制項) 。

   如果有多個控制項需要，每個控制項的大小都要貼齊第二個指南。

### <a name="other-controls"></a>其他控制項

當您將下拉式方塊新增至對話方塊時，可以調整其大小。 您也可以指定下拉式清單方塊的大小。 如需詳細資訊，請參閱 [將值加入至下拉式方塊控制項](./defining-mnemonics-access-keys.md)。

1. 選取下拉式方塊右邊的下拉箭號按鈕。

   ![MFC 專案中下拉式方塊上的箭頭](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控制項的外框會變更，以顯示下拉式清單區域已擴充的下拉式方塊大小。

1. 使用較低的調整大小控點來變更下拉式清單區域的初始大小。

   ![在 MFC 專案中調整大小的組合&#45;框](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 再次選取下拉式箭號，以關閉下拉式方塊的下拉式清單部分。

> [!NOTE]
> 當您使用 MFC 將具有水準捲軸的清單方塊加入至對話方塊時，捲軸不會自動出現在您的應用程式中。
>
> 在您的程式碼中呼叫 [CListBox：： SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ，以設定最寬元素的最大寬度。 如果未設定此值，即使清單方塊中的專案超出方塊，也不會顯示捲軸。

## <a name="align-controls"></a>對齊控制項

- 若要對齊控制項，請選取您要對齊的控制項。 移至 [功能表**格式**  >  **對齊**]，然後選擇下列其中一個對齊方式：

   |對齊|描述|
   |-----|-----------|
   |**左轉**|將選取的控制項與其左邊對齊。|
   |**中心**|將選取的控制項以水準方向沿著中心點對齊。|
   |**權限**|將選取的控制項靠右對齊。|
   |**上衣**|將選取的控制項與其上邊緣對齊。|
   |**中心**|將選取的控制項沿著其中間點垂直對齊。|
   |**底部**|將選取的控制項與其下邊緣對齊。|

   請務必先選取您想要作為主要控制項的控制項，或將它設定為主控制項，再執行對齊或調整大小命令，因為控制項群組的最後位置取決於主控制項的位置。

- 若要平均空間控制項，請選取您想要重新排列的控制項。 平均移至 [功能表**格式**  >  **空間**]，然後選擇下列其中一個間距對齊方式：

   |間距|描述|
   |---|---|
   |**橫向**|在最左邊和最右邊的控制項之間平均空間控制。|
   |**向下**|在選取的最上層與最底部的控制項之間平均空間控制項。|

- 若要置中控制項，請選取您要重新排列的控制項或控制項。 移至對話方塊中的 [功能表**格式**  >  **中心]** ，然後選擇下列其中一種相片順序：

   |安排|描述|
   |---|---|
   |**Vertical**|在對話方塊中垂直置中控制項。|
   |**水平**|在對話方塊中水準置中控制項。|

- 若要對齊推播按鈕，請選取一或多個推播按鈕。 移至 [功能表**格式**  >  **排列] 按鈕**，然後選擇下列其中一種相片順序：

   |安排|描述|
   |---|---|
   |**對**|沿著對話方塊的右邊緣對齊推播按鈕。|
   |**底部**|沿著對話方塊的下邊緣對齊推播按鈕。|

   如果您選取 [按下] 按鈕以外的控制項，其位置不會受到影響。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[管理對話方塊控制項](controls-in-dialog-boxes.md)<br/>
[如何：加入、編輯或刪除控制項](adding-editing-or-deleting-controls.md)<br/>
[如何：定義控制項存取和值](defining-mnemonics-access-keys.md)<br/>
