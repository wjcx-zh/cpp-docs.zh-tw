---
title: '快速鍵編輯器 (c + +) '
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: c98ff1fd44b73b3f204e9b952836c387f7f21146
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353086"
---
# <a name="accelerator-editor-c"></a>快速鍵編輯器 (c + +) 

快速鍵對應表是 c + + Windows 資源，其中包含快速鍵清單（稱為快速鍵）和與其相關聯的命令識別碼。 程式可有多個快速鍵對應表。

一般而言，快速鍵是用作程式命令的鍵盤快速鍵，功能表或工具列也使用這些命令。 不過，您可以使用快速鍵對應表定義和使用者介面物件沒有關聯性的命令鍵組合。

> [!TIP]
> 使用 **快速鍵編輯器**時，以滑鼠右鍵按一下以顯示常用命令的快捷方式功能表。 可用的命令取決於指標所指項目。

您可以使用 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 連結快速鍵命令和程式碼。 如需預先定義的快速鍵清單，請參閱 [快速鍵](predefined-accelerator-keys.md)。

> [!NOTE]
> Windows 不允許您建立空的快速鍵對應表。 如果建立了沒有任何項目的快速鍵對應表，當您儲存資料表時它會自動刪除。

## <a name="accelerator-properties"></a>快速鍵屬性

您可以隨時在 [屬性視窗](/visualstudio/ide/reference/properties-window) 中設定快速鍵屬性。 您也可以使用 **快速鍵編輯器** 來修改快速鍵對應表中的快速鍵屬性。 使用 [ **屬性** ] 視窗或 **快速鍵編輯器** 所做的變更會產生相同的結果，而編輯會立即反映在快速鍵對應表中。

**ID**屬性會參考程式碼中的每個快速鍵對應表專案。 當使用者按下快速鍵或按鍵組合時，此專案是程式所收到的命令值。 若要讓快速鍵與功能表項目相同，請將 **識別碼** 設為相同，只要快速鍵對應表的 **識別碼** 與功能表資源的 **識別碼** 相同即可。

每個加速器 **識別碼** 都有三個屬性： **修飾**詞、索引 **鍵**和 **類型**

**修飾**詞屬性會設定快速鍵的控制項按鍵組合。

> [!NOTE]
> 在 [ **屬性** ] 視窗中，[ **修飾** 詞] 屬性會顯示為三個不同的 **布林值** 屬性，這些屬性全都可以獨立控制： **Alt**、 **Ctrl**和 **Shift**。

以下是快速鍵對應表中的 **修飾** 詞屬性的合法專案：

   |值|描述|
   |-----------|-----------------|
   |**None**|使用者只按下索引 **鍵值** 。<br/><br/>此值最有效率地搭配 ASCII/ANSI 值001至026使用，此值會以 ^ A 到 ^ Z (**ctrl + A** 至 **ctrl + z**) 來解讀。|
   |**Alt 鍵**|使用者必須在**金鑰**值之前按下**Alt** 。|
   |**Ctrl**|使用者必須在**金鑰**值之前按**Ctrl**鍵，而不能使用 ASCII 類型。|
   |**Shift 鍵**|使用者必須按下 **Shift** **鍵** 值。|
   |**Ctrl + Alt**|使用者必須在**金鑰**值之前按**Ctrl**和**Alt** ，而不能使用 ASCII 類型。|
   |**Ctrl + Shift**|使用者必須在**金鑰**值之前按下**Ctrl**和**Shift** ，而不能使用 ASCII 類型。|
   |**Alt + Shift**|使用者必須在**金鑰**值之前按下**Alt**和**Shift** ，而不是與 ASCII 類型有效。|
   |**Ctrl + Alt + Shift**|使用者必須按下 **Ctrl**、 **Alt**和 **Shift** 才能使用索引 **鍵值** ，而不能使用 ASCII 類型。|

索引 **鍵** 屬性會設定要做為加速器使用的實際金鑰。

以下是快速鍵對應表中的索引 **鍵** 屬性的合法專案：

   |值|說明|
   |-----------|-----------------|
   |十進位格式0和255之間的整數。|此值會決定值是否視為 ASCII 或 ANSI，如下所示：<br/><br/>   -單一位數的數位一律會轉譯為對應的索引鍵，而不是 ASCII 或 ANSI 值。<br/>   -從1到26的值（如果前面加上零）會被解釋為 ^ A 到 ^ Z，表示在按下 **Ctrl** 鍵時，字母的 ASCII 值。<br/>   -27-32 的值一律會轉譯為027至032的三位數十進位值。<br/>   -從033到255的值（不論前面是否加上0）都會轉譯為 ANSI 值。|
   |單一鍵盤字元。|大寫 A-z 或數位 0-9 可以是 ASCII 或虛擬機器碼值。 任何其他字元只是 ASCII。|
   |範圍 A-Z (大寫的單一鍵盤字元僅) ，前面加上插入號 (^) ，例如 ^ C。|當按下 **Ctrl** 鍵時，此選項會輸入索引鍵的 ASCII 值。|
   |任何有效的虛擬機器碼識別碼。|快速鍵對應表中的下拉式清單方塊包含標準虛擬 **機碼識別碼** 的清單。|

> [!NOTE]
> 輸入 ASCII 值時，會限制 **修飾** 詞屬性選項。 唯一可供使用的控制項索引鍵是 **Alt** 鍵。

> [!TIP]
> 定義快速鍵的快捷方式是在快速鍵對應表中的專案或多個專案上按一下滑鼠右鍵，然後選擇 [ **下一個按鍵類型]** ，然後按鍵盤上的任何按鍵或按鍵組合。
>
> 您也可以從 [**編輯**] 功能表取得**下一個索引鍵類型**命令。

**Type**屬性會決定與快速鍵**識別碼**相關聯的快速鍵組合是否會轉譯為 ASCII/ANSI 索引鍵值或虛擬機器碼 (VIRTKEY) 組合。

- 如果 [ **類型** ] 屬性是 [ **ASCII**]，則 [ **修飾** 詞] 屬性只可以是 `None` 或 `Alt` ，或者可以有使用 **Ctrl** 鍵的快速鍵，如前面的索引鍵所指定 `^` 。

- 如果 **Type** 屬性是 **VIRTKEY**，則 **修飾** 詞和索引 **鍵值** 的任何組合都是有效的。

> [!NOTE]
> 如果您想要在快速鍵對應表中輸入值，並將值視為 ASCII/ANSI，請選取資料表中專案的 **類型** ，然後從下拉式清單中選取 [ **ASCII** ]。 但是，如果您使用 [**編輯**] 功能表中的 [**下一個金鑰**型別] 命令來指定機**碼**，您必須在輸入**金鑰**代碼*之前，先*將**Type**屬性從**VIRTKEY**變更為**ASCII** 。

## <a name="accelerator-tables"></a>快速鍵對應表

在 c + + 專案中，您可以直接使用 **快速鍵編輯器**中的就地編輯來編輯快速鍵對應表。

下列程式是指使用標準屬性頁，但就地編輯和屬性頁方法都有相同的結果。 使用屬性頁或就地編輯所做的變更會立即反映在快速鍵對應表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 按兩下 [ [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的圖示，以開啟快速鍵對應表。

1. 選取資料表中的專案，然後選擇啟用就地編輯。

1. 從下拉式方塊中選取，或輸入就地以進行變更：

   - 針對 [ **識別碼**]，從清單中選取或輸入以編輯。

   - 在 [ **修飾**詞] 中，從清單中選取。

   - 在 [索引 **鍵**] 中，選取要編輯的清單或類型。

   - 在 [ **類型**] 中，從清單中選取 [ **ASCII** ] 或 [ **VIRTKEY** ]。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在開啟的快速鍵對應表中尋找項目

1. 按兩下 [ [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的圖示，以開啟快速鍵對應表。

1. 選取資料行標題，依字母順序排序資料行的內容。 例如，選取 [ **識別碼** ] 以依字母順序顯示快速鍵對應表中的所有識別碼。

   然後就可以掃描清單並找到項目。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 按兩下 [ [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的圖示，以開啟快速鍵對應表。

1. 在快速鍵對應表中按一下滑鼠右鍵，然後選擇 [ **新增加速器**]，或選取資料表底部的空白資料列專案。

1. 從 [**識別碼**] 方塊的下拉式清單中選取**識別碼**，或在 [**識別碼**] 方塊中輸入新的*識別碼*。

1. 輸入您想要用來做為快速鍵的機*碼*，或以滑鼠右鍵按一下並選擇 **[下一個輸入的按鍵]** 來設定按鍵組合，或 [移至] 功能表**編輯**  >  **下一個輸入的按鍵**。

1. 視需要變更 **修飾** 詞和 **類型**，然後按 **enter**。

> [!NOTE]
> 確定定義的所有快速鍵都是唯一的。 您可以將數個按鍵組合指派給相同的識別碼，而不會有任何不良影響，例如，您可以將**Ctrl** + **P**和**F8**指派給 ID_PRINT。 不過，將按鍵組合指派給一個以上的識別碼無法正常運作，例如，將**Ctrl** + **Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 按兩下 [ [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的圖示，以開啟快速鍵對應表。

1. 選取您要刪除的專案，或按住 **Ctrl** 鍵或 **Shift** 鍵，同時選擇多個專案。

1. 按一下滑鼠右鍵並選擇 [**刪除**]，或移至 [功能表**編輯**  >  **刪除**]。

> [!TIP]
> 您也可以按 **delete** 鍵來刪除。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 開啟兩個資源指令檔中的快速鍵對應表，然後選取您要移動的專案。

1. 從 [ **編輯** ] 功能表中，選擇 [ **複製** ] 或 [ **剪**下]。

1. 選取目標資源腳本檔中的專案，然後從 [ **編輯** ] 功能表選擇 [ **貼**上]。

> [!NOTE]
> 您也可以使用快速鍵進行複製及貼上。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>變更多個快速鍵的屬性

1. 按兩下 [ [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的圖示，以開啟快速鍵對應表。

1. 選取您要變更的快速鍵，方法是按住 **Ctrl** 鍵，然後選取每個按鍵。

1. 移至 [屬性視窗](/visualstudio/ide/reference/properties-window) ，然後輸入您想要所有選取的加速器共用的值。

> [!NOTE]
> 每個修飾詞值在 [ **屬性** ] 視窗中會顯示為布林值屬性。 如果您在 [ **屬性** ] 視窗中變更修飾詞值，快速鍵對應表會將新的修飾詞視為之前的任何修飾詞的補充。 基於這個原因，如果您設定了任何修飾詞值，就必須設定所有的修飾詞，以確保每個加速器都會共用相同的 **修飾** 詞設定。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](resource-editors.md)<br/>
[快速鍵](predefined-accelerator-keys.md)<br/>
