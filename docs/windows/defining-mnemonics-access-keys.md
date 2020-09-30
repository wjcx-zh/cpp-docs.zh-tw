---
title: 如何： (c + +) 定義控制項存取和值
ms.date: 02/15/2019
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
ms.openlocfilehash: 59d81c0b835171132ebf29739a4e130191a87769
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504450"
---
# <a name="how-to-define-control-access-and-values-c"></a>如何： (c + +) 定義控制項存取和值

## <a name="tab-order"></a>定位順序

定位順序是 **tab** 鍵在對話方塊中，將輸入焦點從一個控制項移到下一個控制項的順序。 索引標籤順序通常會在對話方塊中從左至右，從上到下繼續。 每個控制項都有一個 **Tabstop** 屬性，可決定控制項是否接收輸入焦點。

- 若要設定控制項的輸入焦點，請在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [ **Tabstop** ] 屬性中選取 [ **True** ] 或 [ **False** ]。

即使控制項沒有設為**True**的**Tabstop**屬性，也必須是定位順序的一部分，特別是針對沒有標題的控制項。 包含相關控制項之便捷鍵的靜態文字，必須緊接在定位順序中的相關控制項之前。

> [!NOTE]
> 如果對話方塊包含重迭的控制項，變更定位順序可能會變更控制項的顯示方式。 稍後在定位順序中的控制項，一律會顯示在定位順序中之前的任何重迭控制項上方。

- 若要查看所有控制項的目前定位順序，請移至 [功能表**格式**定位  >  **順序]**，或按**Ctrl**  +  **D**。

   每個控制項左上角的數位會顯示其在目前定位順序中的位置。

- 若要變更所有控制項的定位順序，請移至 [功能表**格式**定位  >  **順序]** ，並依您想要按下**tab**鍵的順序來選取每個控制項，以設定定位順序。

- 若要變更兩個或多個控制項的定位順序，請移至 [功能表**格式**定位  >  **順序]**。 按住 **ctrl** 鍵，並選取將開始順序變更的控制項，然後放開 **ctrl** 鍵，然後依您想要 **Tab** 鍵在該時間點之後遵循的順序來選取控制項。

   例如，如果您想要變更控制項的順序 `7` `9` ，請按住 **Ctrl**，然後選取 [first control] `6` 。

- 若要將特定控制項設定為數字 `1` ，或在定位順序中的第一個控制項上按兩下控制項。

> [!TIP]
> 輸入定位 **順序** 模式之後，請按下 **Esc** 鍵或 **enter** 鍵結束定位 **順序** 模式，並停用變更定位順序的能力。

## <a name="mnemonics-access-keys"></a> (存取金鑰) 的助憶鍵

一般情況下，鍵盤使用者會在對話方塊中，使用 **Tab** 鍵和 **箭頭** 鍵將輸入焦點移到另一個控制項。 不過，您可以 (助憶鍵或容易記住的名稱) 來定義存取金鑰，讓使用者可以按單一按鍵來選擇控制項。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要使用可見標題 (按鈕、核取方塊和選項按鈕，來定義控制項的存取金鑰) 

1. 選取對話方塊上的控制項。

1. 在 [ [屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [ **標題** ] 屬性中，輸入控制項的新名稱，然後在 `&` 您想要作為該控制項存取金鑰的字母前面輸入連字號 () 。 例如： `&Radio1` 。

1. 按 **Enter**。

   顯示的標題中會出現底線來指出存取金鑰，例如 **R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定義沒有可見標題之控制項的便捷鍵

1. 使用 [[工具箱](/visualstudio/ide/reference/toolbox)] 中的**靜態文字**控制項來建立控制項的標題。

1. 在 [靜態文字標題] 中，輸入 `&` 您要作為存取金鑰的字母前面的連字號 () 。

1. 請確定靜態文字控制項緊接在定位順序中所標記的控制項之前。

> [!NOTE]
> 對話方塊內的所有存取金鑰都應該是唯一的。 若要檢查是否有重複的存取金鑰，請移至功能表**格式**  >  **檢查助記**鍵。

## <a name="combo-box-values"></a>下拉式列示方塊值

只要開啟 **對話方塊編輯器** ，您就可以將值加入至下拉式方塊控制項。

> [!TIP]
> 建議您在調整**對話方塊編輯器**中的方塊大小時，將所有值都加入下拉式方塊中，*否則您可能*會截斷應該出現在群組控制項中的文字。

### <a name="to-enter-values-into-a-combo-box-control"></a>在下拉式方塊控制項中輸入值

1. 選取下拉式方塊控制項來選擇它。

1. 在 [ [屬性] 視窗](/visualstudio/ide/reference/properties-window)中，向下滾動至 **資料** 屬性。

   > [!NOTE]
   > 如果您要顯示依類型分組的屬性， **資料** 會出現在 [ **其他** 屬性] 中。

1. 選取 [ **資料** ] 屬性的 [值] 區域，然後輸入您的資料值（以分號分隔）。

   > [!NOTE]
   > 請勿在值之間加上空格，因為空格會干擾下拉式清單中的 Alphabetizing。

1. 當您完成新增值時，請按 **enter** 鍵。

如需放大下拉式方塊的下拉式部分的詳細資訊，請參閱設定下拉式方塊的 [大小及其下拉式清單](./arrangement-of-controls-on-dialog-boxes.md)。

> [!NOTE]
> 您無法使用此程式將值加入至 Win32 專案 (**資料** 屬性在 win32 專案) 中呈現灰色。 由於 Win32 專案沒有可加入這項功能的程式庫，因此您必須以程式設計的方式，將值新增至具有 Win32 專案的下拉式方塊。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>測試下拉式方塊中的值外觀

1. 在 [**資料**] 屬性中輸入值之後，請選取[對話方塊編輯器工具列](./dialog-editor.md)上的 [**測試**] 按鈕。

1. 請嘗試向下滾動整個值清單。 在 [**屬性**] 視窗的 [**資料**] 屬性中輸入值時，其值會完全相同。 沒有拼寫或大小寫檢查。

1. 按下 **Esc** 鍵以返回 **對話方塊** 編輯器。

## <a name="radio-button-values"></a>選項按鈕值

當您將選項按鈕加入至對話方塊時，請在群組中第一個按鈕的 [**屬性**] 視窗中設定**群組**屬性，將其視為群組。 然後，這個選項按鈕的控制項識別碼就會出現在 [[加入成員變數精靈]](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard)中，讓您為選項按鈕群組加入成員變數。

您可以在對話方塊上有一個以上的選項按鈕群組。 使用下列程式來新增每個群組。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>在對話方塊中加入選項按鈕群組

1. 在 [ [工具箱] 視窗](/visualstudio/ide/reference/toolbox) 中選取選項按鈕控制項，然後在對話方塊中選擇要放置控制項的位置。

1. 重複上述步驟，以新增您所需的多個選項按鈕。 請確定群組中的選項按鈕在定位順序中是連續的。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，請將定位順序 **第一** 之選項按鈕的 [群組] ** 屬性設為 **True**。

   將 [ **群組** ] 屬性變更為 [ **True** ]，會將 WS_GROUP 樣式加入至資源腳本之對話方塊物件的按鈕專案中，並防止使用者在按鈕群組中一次選取一個以上的選項按鈕 (如果使用者選取一個選項按鈕，則會) 清除群組中的其他專案。

   > [!NOTE]
   > 群組中，應該只有第一個選項按鈕的 [群組] **** 屬性設為 **True**。 如果您有不屬於按鈕群組的其他控制項，請將*群組外*第一個控制項的 [**群組**] 屬性設定為 [ **True** ]。 您可以使用**Ctrl** + **D**來查看定位順序，以快速識別群組外的第一個控制項。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>加入選項按鈕群組的成員變數

1. 以滑鼠右鍵按一下定位順序中的第一個選項按鈕控制項， (主控制項，然後將 [ **群組** ] 屬性設定為 [ **True** ]) 然後選擇 [ **加入變數**]。

1. 在 [[加入成員變數精靈]](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard)中，選取 [控制項變數] **** 核取方塊，然後選取 [值] **** 選項按鈕。

   - 在 [變數名稱] **** 方塊中，輸入新成員變數的名稱。

   - 在 [ **變數類型** ] 清單方塊中，選取 **`int`** 或輸入 *int*。

   您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 例如， `m_radioBox1 = 0;` 選取群組中的第一個選項按鈕。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[管理對話方塊控制項](controls-in-dialog-boxes.md)<br/>
[如何：加入、編輯或刪除控制項](adding-editing-or-deleting-controls.md)<br/>
[How To： Layout 控制項](arrangement-of-controls-on-dialog-boxes.md)<br/>
