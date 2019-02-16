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
ms.openlocfilehash: 90ef142336cf88c5e40f78f6cc651b2bb35a0f6c
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320636"
---
# <a name="accelerator-editor-c"></a>快速鍵編輯器 （c + +）

快速鍵對應表是包含一份快速鍵 （也稱為快速鍵） 的 c + + Windows 資源，以及與它們相關聯的命令識別碼。 程式可有多個快速鍵對應表。

一般而言，快速鍵是用作程式命令的鍵盤快速鍵，功能表或工具列也使用這些命令。 不過，您可以使用快速鍵對應表定義和使用者介面物件沒有關聯性的命令鍵組合。

您可以使用 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 連結快速鍵命令和程式碼。

如需預先定義的快速鍵的清單，請參閱 <<c0> [ 預先定義的快速鍵](../windows/predefined-accelerator-keys.md)。

   > [!TIP]
   > 在使用時**加速器**編輯器中，您可以按一下滑鼠右鍵顯示常用命令的捷徑功能表。 可用的命令取決於指標所指項目。

   > [!NOTE]
   > Windows 不允許建立空的快速鍵對應表。 如果建立了沒有任何項目的快速鍵對應表，當您儲存資料表時它會自動刪除。

## <a name="accelerator-properties"></a>快速鍵屬性

您可以在設定快速鍵屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)在任何時間。 您也可以使用**加速器**編輯器來修改快速鍵對應表中的快速鍵屬性。 所做的變更**屬性** 視窗或**加速器**編輯器有相同的結果： 編輯會立即反映在快速鍵對應表。

### <a name="id-property"></a>ID 屬性

**識別碼**屬性參考程式碼中的每個快速鍵對應表項目。 此項目是在使用者按下快速鍵或按鍵組合，程式將收到的命令值。 若要讓功能表項目相同加速器，讓它們的 Id 相同 （只要快速鍵對應表的識別碼是功能表資源的識別碼相同）。

有三個屬性的每個快速鍵 ID:**修飾詞**屬性，**金鑰**屬性，而**型別**屬性。

#### <a name="modifier-property"></a>Modifier 屬性

**修飾詞**屬性會設定控制項的快速鍵組合。

> [!NOTE]
> 在 [**屬性**] 視窗中，這個屬性會顯示為三個不同**布林**屬性，全部都可以獨立控制：**Alt**， **Ctrl**，以及**Shift**。

以下是合法的項目**修飾詞**快速鍵對應表中的屬性：

   |值|描述|
   |-----------|-----------------|
   |**無**|只有使用者按下**金鑰**值。 使用此值是最有效地以 ASCII/ANSI 值 001 026，透過它被解譯為 ^ A 到 ^ Z (**Ctrl + A**透過**Ctrl + Z**)。|
   |**Alt**|使用者必須按下**Alt**金鑰之前**金鑰**值。|
   |**Ctrl**|使用者必須按下**Ctrl**金鑰之前**金鑰**值。 ASCII 類型無效。|
   |**Shift**|使用者必須按下**Shift**金鑰之前**金鑰**值。|
   |**Ctrl+Alt**|使用者必須按下**Ctrl**機碼並**Alt**金鑰之前**金鑰**值。 ASCII 類型無效。|
   |**Ctrl+Shift**|使用者必須按下**Ctrl**機碼並**Shift**金鑰之前**金鑰**值。 ASCII 類型無效。|
   |**Alt+Shift**|使用者必須按下**Alt**機碼並**Shift**金鑰之前**金鑰**值。 ASCII 類型無效。|
   |**Ctrl+Alt+Shift**|使用者必須按下**Ctrl**， **Alt**，並**Shift**之前**金鑰**值。 ASCII 類型無效。|

#### <a name="key-property"></a>Key 屬性

**金鑰**屬性會設定要做為快速鍵的實際金鑰。

以下是合法的項目**金鑰**快速鍵對應表中的屬性：

   |值|描述|
   |-----------|-----------------|
   |介於 0 到 255 的十進位整數。|值會決定是否此值會被視為 ASCII 或 ANSI，如下所示：<br/><br/>-單一位數的數字一律會解譯為相對應的索引鍵，而不是 ASCII 或 ANSI 值。<br/>-1 到 26 範圍，加零的值會解譯為 ^ A 到 ^ Z，代表字母表的字母與按下時的 ASCII 值**Ctrl**按住按鍵。<br/>-27 到 32 之間的值一律解譯為三位數十進位值 027 032 到。<br/>-值 033 到 255，加上 0，還是不會被解譯為 ANSI 值。|
   |鍵盤字元。|大寫 A-Z 或數字 0-9 可以是 ASCII 或虛擬索引鍵值;任何其他字元只為 ASCII。|
   |鍵盤字元 A – Z 範圍內 （僅有大寫） 加上插入號 (^) (例如，^ C)。|此選項與按下時，請輸入索引鍵的 ASCII 值**Ctrl**按住按鍵。|
   |任何有效的虛擬索引鍵識別碼。|快速鍵對應表中的 [下拉式清單金鑰] 方塊包含一份標準的虛擬索引鍵識別碼。|

> [!NOTE]
> 時輸入 ASCII 值，輔助按鍵屬性選項將會受到限制。 是唯一可用的控制鍵使用**Alt**索引鍵。

> [!TIP]
> 定義快速鍵的另一個方法是以滑鼠右鍵按一下某個項目或快速鍵對應表中的多個項目，請選擇**下一步 輸入的按鍵**從捷徑功能表，然後在鍵盤上按任何按鍵或按鍵組合。 **下一步 輸入的按鍵**命令也會提供**編輯**功能表。

#### <a name="type-property"></a>Type 屬性

**型別**屬性會決定是否要將快速鍵 ID 相關聯的快速鍵組合解譯為 ASCII/ANSI 機碼值或 (VIRTKEY) 的虛擬按鍵組合。

- 如果**型別**屬性是 ASCII，**修飾詞**屬性只能`None`或`Alt`，或它可能會使用加速器**Ctrl**索引鍵 （指定的方法是使用金鑰`^`)。

- 如果**型別**屬性是 VIRTKEY 的任意組合`Modifier`和`Key`值無效。

> [!NOTE]
> 如果您想要快速鍵對應表中輸入值，且值為 ASCII/ANSI，只要按一下**型別**從下拉式清單中的選取 ASCII 與資料表中的項目。 不過，如果您使用**下一步 輸入的按鍵**命令 (**編輯**功能表) 來指定`Key`，您必須變更**型別**屬性從 VIRTKEY 為 ASCII *之前先*輸入`Key`程式碼。

## <a name="accelerator-tables"></a>快速鍵對應表

在 c + + 專案中，您可以直接使用就地編輯中編輯快速鍵對應表**加速器**編輯器。

使用標準內容頁，請參閱下列程序，不過，就地編輯和屬性頁方法有相同的結果。 使用屬性頁，或使用就地編輯所做的變更會立即反映在快速鍵對應表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取資料表中的項目，並選取即可啟動就地編輯。

1. 從下拉式方塊中選取，或輸入位置進行變更。

   - 針對**識別碼**，從選取清單或輸入以編輯。

   - 針對**修飾詞**，從清單中選取。

   - 針對**金鑰**，從選取清單或輸入以編輯。

   - 針對**型別**，選取**ASCII**或是**VIRTKEY**從清單中。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在開啟的快速鍵對應表中尋找項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取的資料行行首，以依字母順序排序的資料行的內容。 例如，選取**識別碼**依字母順序顯示快速鍵對應表中的所有識別碼。

然後就可以掃描清單並找到項目。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 快速鍵對應表內按一下滑鼠右鍵，然後選擇 **新的 Accelerator**從捷徑功能表或選取之資料表底部的空白資料列項目。

1. 選取 [**識別碼**從識別碼中的下拉式清單方塊，或輸入新的識別碼，在**識別碼**] 方塊中。

1. 型別**金鑰**您想要做為快速鍵或以滑鼠右鍵按一下，然後選擇**下一步 輸入的按鍵**從捷徑功能表，來設定按鍵組合 (**下一個輸入的索引鍵**命令也可從**編輯**功能表)。

1. 變更**修飾詞**並**型別**，如有必要。

1. 按 **Enter** 鍵。

   > [!NOTE]
   > 確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵的組合，指派給相同的影響，例如，ID **Ctrl** + **P**並**F8**可以同時指派給 ID_PRINT。 不過，將 指派給一個以上的 ID 將無法正常運作，比方說，一個按鍵組合**Ctrl** + **Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取您要刪除的項目。 (按住**Ctrl**或是**Shift**鍵同時選取來選擇多個項目。)

1. 以滑鼠右鍵按一下，然後選擇 **刪除**從捷徑功能表 (或選取**刪除**從**編輯**功能表)。

> [!TIP]
> 刪除快速鍵是按下**刪除**索引鍵。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 在這兩個資源指令碼檔案中開啟快速鍵對應表。

1. 選取您要移動的項目。

1. 從**編輯**功能表上，選擇**複製**或是**剪下**。

1. 選取目標資源指令碼檔案中的項目。

1. 從**編輯**功能表上，選擇**貼上**。

   > [!NOTE]
   > 您也可以使用快速鍵進行複製及貼上。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵屬性

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取您想要變更按住的快速鍵**Ctrl**當您選取每個索引鍵。

1. 移至[屬性 視窗](/visualstudio/ide/reference/properties-window)和您想要選取加速器，若要共用的所有值的型別。

   > [!NOTE]
   > 每個修飾詞值會顯示為布林值屬性中**屬性**視窗。 如果您變更[修飾詞](../windows/accelerator-modifier-property.md)中的值**屬性** 視窗中，快速鍵對應表視為新的修飾詞的補充先前有任何修飾詞。 因為這個緣故，如果您設定任何修飾詞的值，您必須設定它們，以確保每個加速器共用相同的所有**修飾詞**設定。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[預先定義的快速鍵](../windows/predefined-accelerator-keys.md)<br/>