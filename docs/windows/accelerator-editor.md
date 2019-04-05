---
title: 快速鍵編輯器 （c + +）
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
ms.openlocfilehash: f5ae9880719a3a8b799ea8deb751b6f0a85542bd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041120"
---
# <a name="accelerator-editor-c"></a>快速鍵編輯器 （c + +）

快速鍵對應表是 c + + Windows 資源，其中包含一份稱為快速鍵，以及與它們相關聯的命令識別碼的快速鍵。 程式可有多個快速鍵對應表。

一般而言，快速鍵是用作程式命令的鍵盤快速鍵，功能表或工具列也使用這些命令。 不過，您可以使用快速鍵對應表定義和使用者介面物件沒有關聯性的命令鍵組合。

> [!TIP]
> 使用時**快速鍵編輯器**，以滑鼠右鍵按一下以顯示經常命令的捷徑功能表。 可用的命令取決於指標所指項目。

您可以使用 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 連結快速鍵命令和程式碼。 如需預先定義的快速鍵的清單，請參閱 <<c0> [ 快速鍵](../windows/predefined-accelerator-keys.md)。

> [!NOTE]
> Windows 不允許您建立空的快速鍵對應表。 如果建立了沒有任何項目的快速鍵對應表，當您儲存資料表時它會自動刪除。

## <a name="accelerator-properties"></a>快速鍵屬性

您可以在設定快速鍵屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)在任何時間。 您也可以使用**快速鍵編輯器**修改快速鍵對應表中的快速鍵屬性。 使用所做的變更**屬性** 視窗或**快速鍵編輯器**有相同的結果，編輯會立即反映在快速鍵對應表。

**識別碼**屬性參考程式碼中的每個快速鍵對應表項目。 此項目是在使用者按下快速鍵或按鍵組合，則程式會收到的命令值。 若要讓功能表項目一樣加速器，請**識別碼**相同，因此只要**識別碼**加速器的資料表是相同**識別碼**功能表資源。

每個加速器**識別碼**有三個屬性：**修飾詞**，**金鑰**，和**類型**

**修飾詞**屬性會設定控制項的快速鍵組合。

> [!NOTE]
> 在 [**屬性**] 視窗中，**修飾詞**屬性會顯示為三個不同**布林**屬性，全部都可以獨立控制：**Alt**， **Ctrl**，以及**Shift**。

以下是合法的項目**修飾詞**快速鍵對應表中的屬性：

   |值|描述|
   |-----------|-----------------|
   |**None**|只有使用者按下**金鑰**值。<br/><br/>使用此值是最有效地以 ASCII/ANSI 值 001 026，透過它被解譯為 ^ A 到 ^ Z (**Ctrl + A**透過**Ctrl + Z**)。|
   |**Alt**|使用者必須按下**Alt**之前**金鑰**值。|
   |**Ctrl**|使用者必須按下**Ctrl**之前**金鑰**，不正確的值與 ASCII 類型。|
   |**Shift**|使用者必須按下**Shift**之前**金鑰**值。|
   |**Ctrl+Alt**|使用者必須按下**Ctrl**並**Alt**之前**金鑰**，不正確的值與 ASCII 類型。|
   |**Ctrl+Shift**|使用者必須按下**Ctrl**並**Shift**之前**金鑰**，不正確的值與 ASCII 類型。|
   |**Alt+Shift**|使用者必須按下**Alt**並**Shift**之前**金鑰**，不正確的值與 ASCII 類型。|
   |**Ctrl+Alt+Shift**|使用者必須按下**Ctrl**， **Alt**，並**Shift**之前**金鑰**，不正確的值與 ASCII 類型。|

**金鑰**屬性會設定要做為快速鍵的實際金鑰。

以下是合法的項目**金鑰**快速鍵對應表中的屬性：

   |值|描述|
   |-----------|-----------------|
   |介於 0 到 255 的十進位整數。|值會決定是否此值會被視為 ASCII 或 ANSI，如下所示：<br/><br/>   -單一位數的數字一律會解譯為相對應的索引鍵，而不是 ASCII 或 ANSI 值。<br/>   -1 到 26 範圍，加零的值會解譯為 ^ A 到 ^ Z，代表字母表的字母與按下時的 ASCII 值**Ctrl**按住按鍵。<br/>   -27 到 32 之間的值一律解譯為三位數十進位值 027 032 到。<br/>   -值 033 到 255，加上 0，還是不會被解譯為 ANSI 值。|
   |鍵盤字元。|大寫 A-Z 或數字 0-9 可以是 ASCII 或虛擬索引鍵值。 任何其他字元只為 ASCII。|
   |鍵盤字元 A – Z 範圍內 （僅有大寫） 例如，加上插入號 (^)、 ^ c。|此選項與按下時，請輸入索引鍵的 ASCII 值**Ctrl**按住按鍵。|
   |任何有效的虛擬索引鍵識別碼。|下拉式清單**金鑰**快速鍵對應表中的方塊中包含的標準虛擬的金鑰識別碼清單。|

> [!NOTE]
> 輸入 ASCII 值，當**修飾詞**屬性 選項會限制。 是唯一可用的控制鍵使用**Alt**索引鍵。

> [!TIP]
> 定義快速鍵的捷徑，就是以滑鼠右鍵按一下項目或快速鍵對應表中的多個項目，然後選擇 [**下一步] 輸入的按鍵**並按鍵盤上的任何按鍵或按鍵組合。
>
> 這**下一步 輸入的按鍵**命令也會提供**編輯**功能表。

**型別**屬性會決定是否與加速器相關聯的快速鍵組合**識別碼**會解譯為 ASCII/ANSI 金鑰值或 (VIRTKEY) 的虛擬按鍵組合。

- 如果**型別**屬性是**ASCII**，則**修飾詞**屬性只能`None`或`Alt`，或者可以有加速器使用**Ctrl**鍵，所指定的方法是使用金鑰`^`。

- 如果**型別**屬性是**VIRTKEY**的任意組合**修飾詞**並**金鑰**值無效。

> [!NOTE]
> 如果您想要進入快速鍵對應表中的值，且值為 ASCII/ANSI，選取**型別**中的資料表和選取的項目**ASCII**從下拉式清單中。 不過，如果您使用**下一個輸入的索引鍵**命令**編輯**指定的功能表**金鑰**，您必須變更**類型**屬性**VIRTKEY**要**ASCII** *之前*輸入**金鑰**程式碼。

## <a name="accelerator-tables"></a>快速鍵對應表

在 c + + 專案中，您可以直接使用就地編輯中編輯快速鍵對應表**快速鍵編輯器**。

使用標準內容頁，請參閱下列程序，不過，就地編輯和屬性頁方法有相同的結果。 使用屬性頁，或使用就地編輯所做的變更會立即反映在快速鍵對應表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取資料表中的項目，並選取即可啟動就地編輯。

1. 從下拉式清單方塊中選取或輸入位置進行變更：

   - 針對**識別碼**，從選取清單或輸入以編輯。

   - 針對**修飾詞**，從清單中選取。

   - 針對**金鑰**，從選取清單或輸入以編輯。

   - 針對**型別**，選取**ASCII**或是**VIRTKEY**從清單中。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在開啟的快速鍵對應表中尋找項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取的資料行行首，以依字母順序排序的資料行的內容。 例如，選取**識別碼**依字母順序顯示快速鍵對應表中的所有識別碼。

   然後就可以掃描清單並找到項目。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 快速鍵對應表內按一下滑鼠右鍵，然後選擇 **新的 Accelerator**，或選取之資料表底部的空白資料列項目。

1. 選取 [**識別碼**從下拉式清單中**識別碼**方塊中，或輸入新*識別碼*中**識別碼**] 方塊中。

1. 型別*金鑰*您想要做為快速鍵，或以滑鼠右鍵按一下並選擇 [**下一步] 輸入的按鍵**來設定按鍵組合，或移至功能表**編輯** >  **輸入的下一個按鍵**。

1. 變更**修飾詞**並**型別**，如有必要，然後按**Enter**。

> [!NOTE]
> 確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵的組合，指派給相同的影響，例如，ID **Ctrl**+**P**並**F8**可以同時指派給 ID_PRINT。 不過，將 指派給一個以上的識別碼不會正常運作，比方說，一個按鍵組合**Ctrl**+**Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要刪除，或按住項的目**Ctrl**或是**Shift**鍵同時選取來選擇多個項目。

1. 以滑鼠右鍵按一下，然後選擇 **刪除**，或移至功能表**編輯** > **刪除**。

> [!TIP]
> 您也可以按下**刪除**若要刪除的索引鍵。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 在這兩個資源指令碼檔案中開啟快速鍵對應表，然後選取您想要移動的項目。

1. 從**編輯**功能表上，選擇**複製**或是**剪下**。

1. 選取一個項目，在目標資源指令碼檔案，並從**編輯**功能表上，選擇**貼上**。

> [!NOTE]
> 您也可以使用快速鍵進行複製及貼上。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵屬性

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要變更按住的快速鍵**Ctrl**當您選取每個索引鍵。

1. 移至[屬性 視窗](/visualstudio/ide/reference/properties-window)和您想要選取加速器，若要共用的所有值的型別。

> [!NOTE]
> 每個修飾詞值會顯示為布林值屬性中**屬性**視窗。 如果您變更[修飾詞](../windows/accelerator-modifier-property.md)中的值**屬性** 視窗中，快速鍵對應表視為新的修飾詞的補充先前有任何修飾詞。 因為這個緣故，如果您設定任何修飾詞的值，您必須設定它們，以確保每個加速器共用相同的所有**修飾詞**設定。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[快速鍵](../windows/predefined-accelerator-keys.md)<br/>