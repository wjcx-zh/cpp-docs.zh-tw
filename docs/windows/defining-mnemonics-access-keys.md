---
title: 定義控制存取和值
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 20319cd08d6d1e77faef1275e63bf3ffd354356b
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336484"
---
# <a name="defining-control-access-and-values"></a>定義控制存取和值

## <a name="change-the-tab-order-of-controls"></a>變更控制項的定位順序

定位順序是順序**索引標籤**金鑰將輸入的焦點從一個控制項移至 對話方塊中的下一步。 通常是定位順序會繼續從左到右及從上到下一個對話方塊中。 每個控制項都**Tabstop**屬性，可決定控制項是否收到輸入的焦點。

### <a name="to-set-input-focus-for-a-control"></a>若要設定控制項的輸入的焦點

在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，選取 **，則為 True**或**False**中**Tabstop**屬性。

即使沒有的控制項**Tabstop**屬性設定為 **，則為 True**必須為定位順序的一部分。 定位順序很重要，比方說，當您[定義便捷鍵 （助憶鍵）](../windows/defining-mnemonics-access-keys.md)沒有標題的控制項。 定位順序中，包含相關的控制項的便捷鍵的靜態文字必須緊接著相關的控制項。

> [!NOTE]
> 如果您的對話方塊中包含重疊的控制項，變更索引標籤順序可能會變更控制項的顯示的方式。 定位順序中稍後出現的控制項一律會顯示任何重疊的控制項定位順序中前之上。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要檢視在對話方塊中的所有控制項目前的定位順序

移至**格式**功能表，然後選取**定位順序**，或按下**Ctrl** + **D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要變更在對話方塊中的所有控制項的定位順序

1. 在 **格式**功能表上，選取**定位順序**。

   在左上角的數字，每個控制項目前的定位順序中顯示它的位置。

1. 選取您想要的順序的每個控制項設定定位順序**索引標籤**遵循的索引鍵。

1. 按下**Enter**以結束**定位順序**模式。

   > [!TIP]
   > 一旦您輸入**定位順序**模式中，您可以按**Esc**或是**Enter**停用變更定位順序的能力。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要變更兩個或多個控制項的定位順序

1. 從**格式**功能表上，選擇**定位順序**。

1. 指定順序中的變更將會開始的位置。 第一次按住**Ctrl**索引鍵並選取控制項，然後選取您想的要變更的順序開始。

   比方說，如果您想要變更控制項的順序`7`經由`9`，按住**Ctrl**，然後選取 控制項`6`第一次。

   > [!NOTE]
   > 若要設定特定的控制項數目`1`（先在定位順序），連按兩下控制項。

1. 發行**Ctrl**鍵，然後選取您想要的順序的控制項**索引標籤**遵循從該點的索引鍵。

1. 按下**Enter**以結束**定位順序**模式。

## <a name="define-mnemonics-access-keys"></a>定義助憶鍵 （便捷鍵）

一般來說，鍵盤使用者輸入的焦點從一個控制項移到另一個對話方塊中**索引標籤**並**箭號**索引鍵。 不過，您可以定義便捷鍵 （助憶鍵，或按一下 以易記名稱），可讓使用者藉由按下單一索引鍵選擇的控制項。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定義具有可見標題 （按鈕、 核取方塊和選項按鈕） 的控制項的便捷鍵

1. 選取對話方塊上的控制項。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，請在**標題**屬性，輸入控制項中，輸入 & 符號的新名稱 (`&`) 您想要為該控制項的便捷鍵的字母前面。 例如， `&Radio1` 。

1. 按 **Enter** 鍵。

   在顯示的標題中表示的存取金鑰，比方說，就會出現底線**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定義沒有可見標題控制項的便捷鍵

1. 使用時，進行控制項的標題**靜態文字**控制中[工具箱](/visualstudio/ide/reference/toolbox)。

1. 在靜態文字的標題中，輸入連字號 (`&`) 您想要作為便捷鍵的字母前面。

1. 請確定靜態文字控制項前面的控制項之前的定位順序。

> [!NOTE]
> 對話方塊中的所有便捷鍵應該都是唯一的。 若要檢查重複的便捷鍵，請前往**格式**功能表，然後選取**檢查助憶鍵**。

## <a name="combo-box-values"></a>下拉式方塊的值

您可以將值加入下拉式方塊控制項，只要您有 **對話方塊**編輯器中開啟。

> [!TIP]
> 它是個不錯的主意，將所有的值加入至下拉式方塊*之前*大小的方塊中**對話方塊**編輯器中，或者您可能會截斷應該會出現在下拉式方塊控制項的文字。

### <a name="to-enter-values-into-a-combo-box-control"></a>若要在下拉式方塊控制項中輸入值

1. 選擇下拉式方塊控制項選取它。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，向下捲動至**資料**屬性。

   > [!NOTE]
   > 如果您要顯示依類型分組的屬性**資料**會出現在**其他**屬性。

1. 選取 [值] 區域，如**資料**屬性並輸入您的資料值，以分號隔開。

   > [!NOTE]
   > 不要將放值之間的空間，因為空間干擾下拉式清單中的字母排序。

1. 按下**Enter**當您完成加入值。

放大下拉式方塊的下拉式部分的資訊，請參閱[設定的下拉式方塊和下拉式清單中其大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 您無法將使用此程序的 Win32 專案中的值 (**資料**屬性灰色 Win32 專案)。 因為 Win32 專案不會新增這項功能的程式庫，您必須使用 Win32 專案下拉式方塊以程式設計方式加入值。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在下拉式方塊中測試值的外觀

輸入中的值之後**資料**屬性中，選取**測試**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

   請嘗試整個值清單中向下捲動。 值會出現在輸入中，如同**資料**中的屬性**屬性**視窗。 沒有任何拼字檢查或大小寫。

   按下**Esc**以返回 **對話方塊**編輯器。

   您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 比方說，`m_radioBox1 = 0;`會選取第一個選項按鈕群組中。
您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 比方說，`m_radioBox1 = 0;`會選取第一個選項按鈕群組中。

## <a name="radio-button-values"></a>選項按鈕的值

當您新增到對話方塊中的選項按鈕時，將它們視為一組藉由設定**群組**中的屬性**屬性**群組中的第一個按鈕的視窗。 然後，這個選項按鈕的控制項識別碼就會出現在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，讓您為選項按鈕群組加入成員變數。

您可以在對話方塊中有多個選項按鈕群組。 加入每個群組，使用下列程序。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>在對話方塊中加入選項按鈕群組

1. 選取選項按鈕控制項中的[[工具箱] 視窗](/visualstudio/ide/reference/toolbox)和選擇的位置，在對話方塊中控制項的位置。

1. 重複上述步驟來加入多個選項按鈕，視需要。 請確定群組中的選項按鈕是連續的定位順序。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，請將定位順序 **第一** 之選項按鈕的 [群組]  屬性設為 **True**。

   變更**群組**屬性設 **，則為 True**對話方塊物件的資源指令碼中的按鈕的項目中加入 WS_GROUP 樣式，並防止該使用者可以一次選取多個選項按鈕（如果使用者選取一個選項按鈕，群組中其他已取消） 按鈕群組。

   > [!NOTE]
   > 群組中，應該只有第一個選項按鈕的 [群組]  屬性設為 **True**。 如果有不屬於按鈕群組的其他控制項，請將 **群組之外** 第一個控制項的 [群組]  屬性也設成 **True** 。 您可以使用，以快速識別群組之外的第一個控制項**Ctrl**+**D**檢視 索引標籤順序。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>加入選項按鈕群組的成員變數

1. 以滑鼠右鍵按一下定位順序中的第一個選項按鈕控制項 (主控項再加上**群組**屬性設定為 **，則為 True**)，然後選擇 **加入變數**從快顯功能表。

1. 在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，選取 [控制項變數]  核取方塊，然後選取 [值]  選項按鈕。

1. 在 [變數名稱]  方塊中，輸入新成員變數的名稱。

1. 在 [變數類型]  清單方塊中選取 [int]  或輸入 *int*。

   您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 比方說，`m_radioBox1 = 0;`會選取第一個選項按鈕群組中。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)