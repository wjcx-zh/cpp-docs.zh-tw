---
title: 如何：版面配置控制項（C++） |Microsoft Docs
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
ms.openlocfilehash: ee732cfb414f011e95edbbb57b218d81179d44f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168573"
---
# <a name="how-to-layout-controls-c"></a>如何：版面配置控制項（C++）

**對話方塊編輯器**會提供自動對齊和調整控制項大小的版面組態工具。 對於大部分的工作，您可以使用 [[對話方塊編輯器] 工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**對話方塊編輯器**工具列命令也可以在 [**格式**] 功能表上使用，而且大部分都有[快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。

只有選取一個以上的控制項時，才可以使用對話方塊的許多版面配置命令。 您可以選取單一控制項或多個控制項，而且當選取一個以上的控制項時，您選取的第一個控制項會預設為主要控制項。

目前控制項的位置、高度和寬度會顯示在狀態列的右下角。 選取整個對話方塊時，狀態列會顯示整個對話方塊的位置，以及其高度和寬度。

## <a name="arrange-controls"></a>排列控制項

您可以使用下列三種不同狀態之一，在對話方塊**編輯器**中排列控制項：

- 在上使用輔助線和邊界，設定為預設值。

- 搭配的版面配置方格。

- 沒有任何貼齊或對齊功能。

[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含可控制狀態的按鈕。

- 若要變更狀態，請選取適當的圖示，或移至功能表**格式** > [**指南設定**]。

[**指南設定**] 對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**版面配置輔助線**|顯示版面配置輔助線的設定。|
|**None**|隱藏版面組態工具。|
|**尺規和輔助線**|啟用時，會將尺規新增至版面組態工具，並允許將輔助線放在尺規中。 預設的輔助線為邊界。|
|**格線**|建立版面配置方格。 新的控制項將會自動對齊方格。|
|**格線間距**|顯示對話方塊單位（Dlu）中格線間距的設定。|
|**寬度： Dlu**|設定以 Dlu 為單位的版面配置方格寬度。 水準 DLU 是對話方塊字型除以4的平均寬度。|
|**高度： Dlu**|設定 Dlu 中版面配置方格的高度。 垂直 DLU 是對話方塊字型除以8的平均高度。|

### <a name="guides-and-margins"></a>輔助線和邊界

不論您是移動控制項、加入控制項，或是重新排列目前的版面配置、輔助線和邊界，都可以協助您在對話方塊中精確對齊控制項。

當您建立對話方塊時，會提供四個修改過的輔助線，並顯示為藍色虛線。

- 若要移動邊界，請將邊界拖曳至新位置。

- 若要讓邊界消失，請將邊界移至零位置。

- 若要取回邊界，請將指標放在邊界的零位置上，並將邊界移至 [位置]。

輔助線會在編輯器中顯示的對話方塊中，以藍色虛線顯示，並在 [**對話方塊編輯器]** 的頂端和左邊尺規中對應箭號。 控制項的調整大小控點會在控制項移動時貼齊至輔助線，如果沒有任何控制項先前已加入至指南，則輔助線貼齊至控制項。 移動輔助線時，會一併移動其上的控制項。 當移動其中一個輔助線時，會調整貼齊至多個指南的控制項大小。

- 若要在尺規內建立輔助線，請選取 [一次] 來建立節目表，或按兩下以啟動 [**節目表設定**] 對話方塊，您可以在其中指定 [節目表設定]。

- 若要在對話方塊上設定輔助線，請選取 [指南]，並將它拖曳至新位置，或選取尺規中的箭號以拖曳相關聯的節目表。

   本指南的座標會顯示在視窗底部和尺規的狀態列中，或將指標移到尺規的箭號上，以顯示輔助線的確切位置。

- 若要刪除節目表，請將節目表拖曳到對話方塊外，或從尺規拖曳對應的箭號。

尺規中的刻度標記，可決定輔助線和控制項的間距，由對話方塊單位（Dlu）定義。 DLU 是以對話方塊字型的大小為基礎，通常是8點 MS Shell Dlg。 水準 DLU 是對話方塊字型除以四的平均寬度。 垂直 DLU 是字型除以8的平均高度。

- 若要變更刻度的間隔，請移至 [功能表**格式**] > [**指南設定**]，然後在 [**方格間距**] 欄位中，指定新的寬度和以 dlu 為單位的高度。

### <a name="layout-grid"></a>版面配置方格

當您在對話方塊中放置或排列控制項時，請使用版面配置方格來進行更精確的定位。 當格線開啟時，控制項會貼齊格線的虛線，如同 magnetized。

- 若要開啟或關閉版面配置方格，請移至 [功能表**格式**] > [**節目表設定**]，然後選取或清除 [**方格**] 按鈕。

   您仍然可以使用 [[對話方塊編輯器] 工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)上的 [**切換格線**] 按鈕，在個別的 [**對話方塊編輯器]** 視窗中控制方格。

- 若要變更版面配置方格的大小，請移至 [功能表**格式**] > [**指南設定**]，然後在方格中的儲存格上輸入 dlu 的高度和寬度。 最小高度或寬度為4。

### <a name="disable-guides"></a>停用輔助線

您可以使用特殊按鍵搭配滑鼠來停用輔助線的貼齊效果。 使用**Alt**鍵會停用所選指南的貼齊效果。 使用**Shift**鍵移動指南，可防止貼齊的控制項與本指南一起移動。

- 若要停用輔助線的貼齊效果，請在按住**Alt**鍵的同時拖曳控制項。

- 若要移動輔助線而不移動已對齊的控制項，請在按住**Shift**鍵的同時拖曳該輔助線。

- 若要關閉指南，請移至功能表**格式** > **指南設定**。 然後，在 [**版面配置指南**] 底下，選取 [**無**]。

   > [!TIP]
   > 您也可以使用功能表**格式** > **切換輔助線**中的快捷方式。

## <a name="select-controls"></a>選取控制項

選取控制項以進行大小、對齊、移動、複製或刪除，然後完成您想要的操作。 在大部分的情況下，您需要選取一個以上的控制項，以使用[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)上的調整大小和對齊工具。

選取控制項時，它周圍會有一個具有實心（作用中）或空心（非使用中）調整大小控點的陰影框線，出現在選取範圍框線中的小方塊。 選取多個控制項時，主要控制項具有實心大小控點，而且所有其他選取的控制項都有空白的調整大小控點。

- 若要選取控制項，請在 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)中選取 [**指標**] 工具，並使用下列其中一個步驟來進行選取：

  - 將指標拖曳至您想要在對話方塊中選取之控制項的周圍繪製選取方塊。 當您放開滑鼠按鍵時，會選取選取方塊內和相交的所有控制項。

  - 按住**Shift**鍵，然後選取您想要包含在選取專案中的控制項。

  - 按住**Ctrl**鍵，然後選取您想要包含在選取專案中的控制項。

- 若要從選取的控制項群組中新增或移除控制項，請按住**Shift**鍵，然後選取您要加入或移除的控制項。

### <a name="dominant-controls"></a>主要控制項

當您調整大小或對齊多個控制項時，**對話方塊編輯器**會使用主要控制項來判斷其他控制項的大小或對齊方式。 根據預設，主要控制項是第一個選取的控制項。

- 若要指定主要控制項，請按住**Ctrl**鍵，然後選取您想要用來影響其他控制項之大小或位置的*控制項。* 按住**Ctrl**鍵並選取選取範圍內的控制項，也會控制該選取專案中的主要控制項。

- 若要變更主控制項，請清除目前選取的所有控制項以外的專案，然後重複上述程式，*先*選取不同的控制項。

> [!NOTE]
> 主要控制項的調整大小控點為實心，而從屬控制項的控制碼為空心。 所有進一步的調整大小或對齊都是以主要控制項為基礎。

## <a name="size-controls"></a>大小控制項

使用調整大小控點來調整控制項的大小。 當指標放在調整大小控點上時，它會變更圖形，以指示控制項可以調整大小的方向。 現用的調整大小控點為實心，如果調整大小控點為空心，則無法沿著該軸調整控制項的大小。

- 若要調整控制項的大小，請選取控制項，然後拖曳調整大小控點來變更大小。

  - 頂端和側邊的大小控點會變更水準或垂直大小。

  - 角落的大小控點會同時變更水準和垂直大小。

   > [!TIP]
   > 您可以按住**Shift**鍵並使用**向右鍵**和**向下**鍵，一次調整控制項的一個對話方塊單位（DLU）。

- 若要自動調整控制項的大小以符合其內的文字，請移至功能表**格式**，或以滑鼠右鍵按一下控制項，然後選擇 [大小] [**內容**]。

- 若要讓控制項具有相同的大小，請選取您想要調整大小的控制項，並移至功能表**格式** > **讓相同的大小**，然後選擇 [**兩者**]、[**高度**] 或 [**寬度**]。

   您可以根據主要控制項的大小調整控制項群組，這是在數列中第一個選取的控制項。 群組中控制項的最終大小取決於主控制項的大小。

- 若要使用輔助線調整控制項群組的大小，請將控制項（或控制項）的一邊貼齊至輔助線，然後將參考拖曳至控制項的另一端（或控制項）。 現在您可以移動任一指南來調整控制項（或控制項）的大小。

   如有需要，請使用多個控制項來調整每個，以貼齊第二個輔助。

### <a name="other-controls"></a>其他控制項

當您將下拉式方塊新增至對話方塊時，可以調整其大小。 您也可以指定下拉式清單方塊的大小。 如需詳細資訊，請參閱[將值加入至下拉式方塊控制項](../windows/adding-values-to-a-combo-box-control.md)。

1. 選取下拉式方塊右側的下拉箭號按鈕。

   ![MFC 專案中下拉式方塊的箭號](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控制項的外框會變更，以顯示下拉式清單區域已擴充的下拉式方塊大小。

1. 使用較低的調整大小控點來變更下拉式清單區域的初始大小。

   ![MFC&#45;專案中的下拉式方塊大小調整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 再次選取下拉箭號，以關閉下拉式方塊的下拉清單部分。

> [!NOTE]
> 當您使用 MFC 將具有水準捲軸的清單方塊加入至對話方塊時，捲軸不會自動出現在您的應用程式中。
>
> 藉由在程式碼中呼叫[CListBox：： SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ，設定最寬元素的寬度。 若未設定此值，即使清單方塊中的專案寬于方塊，也不會顯示捲軸。

## <a name="align-controls"></a>對齊控制項

- 若要對齊控制項，請選取您要對齊的控制項。 移至功能表**格式** > **對齊**並選擇下列其中一個對齊方式：

   |Alignment|描述|
   |-----|-----------|
   |**左**|將選取的控制項沿著其左邊對齊。|
   |**培訓中心**|將選取的控制項沿著其中心點水準對齊。|
   |**權限**|將選取的控制項靠右對齊。|
   |**上端**|將選取的控制項沿著其上邊緣對齊。|
   |**中部**|將選取的控制項垂直沿著其中間點對齊。|
   |**對齊**|將選取的控制項沿著其下邊緣對齊。|

   請務必先選取您想要做為主要的控制項，或將它設為主要控制項，然後再執行 [對齊] 或 [調整大小] 命令，因為控制項群組的最後位置取決於主控制項的位置。

- 若要平均分配空間控制項，請選取您想要重新排列的控制項。 移至 [功能表**格式**] > [**空間**]，然後選擇下列其中一個間距對齊：

   |Spacing|描述|
   |---|---|
   |**利用率**|在選取的最左邊和最右邊的控制項之間平均空間控制項。|
   |**向下**|最上層的空間控制項，以及所選取的最底層控制項之間。|

- 若要將控制項置中，請選取您要重新排列的控制項或控制項。 移至  **Format**功能表格式 ** > 置中 對話方塊**，然後選擇下列其中一個相片順序：

   |安排|描述|
   |---|---|
   |**垂直**|在對話方塊中垂直置中控制項。|
   |**水平**|在對話方塊中水準置中控制項。|

- 若要對齊 [推播] 按鈕，請選取一或多個 [推送] 按鈕。 移至 功能表 **格式** > **排列按鈕**，然後選擇下列其中一個相片順序：

   |安排|描述|
   |---|---|
   |**Right**|沿著對話方塊右邊緣對齊 [推播] 按鈕。|
   |**下方**|將 [推播] 按鈕沿著對話方塊的下邊緣對齊。|

   如果您選取 [按下] 按鈕以外的控制項，其位置不會受到影響。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[管理對話方塊控制項](controls-in-dialog-boxes.md)<br/>
[如何：加入、編輯或刪除控制項](adding-editing-or-deleting-controls.md)<br/>
[如何：定義控制項存取和值](defining-mnemonics-access-keys.md)<br/>
