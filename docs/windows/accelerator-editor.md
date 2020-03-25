---
title: 快速鍵編輯器（C++）
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
ms.openlocfilehash: 80ef6cc9ec956d0041c4aa3fb6a6211868cc9d73
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167559"
---
# <a name="accelerator-editor-c"></a>快速鍵編輯器（C++）

快速鍵對應表是一C++種 Windows 資源，其中包含快速鍵的清單，稱為快速鍵，以及與這些索引鍵相關聯的命令識別碼。 程式可有多個快速鍵對應表。

一般而言，快速鍵是用作程式命令的鍵盤快速鍵，功能表或工具列也使用這些命令。 不過，您可以使用快速鍵對應表定義和使用者介面物件沒有關聯性的命令鍵組合。

> [!TIP]
> 使用**快速鍵編輯器**時，以滑鼠右鍵按一下以顯示常用命令的快捷方式功能表。 可用的命令取決於指標所指項目。

您可以使用 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 連結快速鍵命令和程式碼。 如需預先定義的快速鍵清單，請參閱[快速鍵](../windows/predefined-accelerator-keys.md)。

> [!NOTE]
> Windows 不允許您建立空的快速鍵對應表。 如果建立了沒有任何項目的快速鍵對應表，當您儲存資料表時它會自動刪除。

## <a name="accelerator-properties"></a>快速鍵屬性

您可以隨時在[屬性視窗](/visualstudio/ide/reference/properties-window)中設定快速鍵屬性。 您也可以使用**快速鍵編輯器**來修改快速鍵對應表中的快速鍵屬性。 使用 [**屬性**] 視窗或**快速鍵編輯器**所做的變更具有相同的結果，而編輯會立即反映在快速鍵對應表中。

**ID**屬性會參考程式碼中的每個快速鍵對應表專案。 此專案是當使用者按下快速鍵或按鍵組合時，程式所收到的命令值。 若要讓快速鍵與功能表項目相同，請將**識別碼**設為相同，只要快速鍵對應表的**識別碼**與功能表資源的**識別碼**相同即可。

每個加速器**識別碼**都有三個屬性：**修飾**詞、索引**鍵**和**類型**

[**修飾**詞] 屬性會設定快速鍵的控制按鍵組合。

> [!NOTE]
> 在 [**屬性**] 視窗中，[**修飾**詞] 屬性會顯示為三個不同的**布林值**屬性，它們全都可以獨立控制： **Alt**、 **Ctrl**和**Shift**。

以下是快速鍵對應表中的 [**修飾**詞] 屬性的合法專案：

   |值|描述|
   |-----------|-----------------|
   |**None**|使用者只按下索引**鍵值**。<br/><br/>這個值最適用于 ASCII/ANSI 值001到026，這會被解釋為 ^ A 到 ^ Z （**ctrl + A**到**ctrl + Z**）。|
   |**Alt**|使用者必須在索引**鍵值**之前按**Alt** 。|
   |**Ctrl**|使用者必須在索引**鍵值**之前按下**Ctrl** ，但不能以 ASCII 類型有效。|
   |**Shift**|使用者必須在索引**鍵值**前面按**Shift**鍵。|
   |**Ctrl + Alt**|使用者必須在索引**鍵值**之前按下**Ctrl**和**Alt** ，而不是以 ASCII 類型有效。|
   |**Ctrl + Shift**|使用者必須在索引**鍵值**之前按下**Ctrl**和**Shift** ，而不是以 ASCII 類型有效。|
   |**Alt + Shift**|使用者必須在索引**鍵值**之前按**Alt**和**Shift** ，而不是以 ASCII 類型有效。|
   |**Ctrl + Alt + Shift**|使用者必須在索引**鍵值**之前按下**Ctrl**、 **Alt**和**Shift** ，而不是以 ASCII 類型有效。|

索引**鍵**屬性會設定要當做快速鍵使用的實際金鑰。

以下是快速鍵對應表中**Key**屬性的合法專案：

   |值|描述|
   |-----------|-----------------|
   |十進位格式的整數，介於0到255之間。|值會決定是否將值視為 ASCII 或 ANSI，如下所示：<br/><br/>   -單一位數的數位一律會解讀為對應的索引鍵，而不是 ASCII 或 ANSI 值。<br/>   -從1到26的值，在前面加上零時，會被解釋為 ^ A 到 ^ Z，這表示當按下**Ctrl**鍵時，字母的 ASCII 值。<br/>   -27-32 的值一律會轉譯為027到032的三位數十進位值。<br/>   -從033到255的值，前面加上0的或不會解讀為 ANSI 值。|
   |單一鍵盤字元。|大寫 A-z 或數位 0-9 可以是 ASCII 或虛擬機器碼值。 任何其他字元只是 ASCII。|
   |在範圍 a-z （僅限大寫）中的單一鍵盤字元，前面加上插入號（^），例如 ^ C。|當按下**Ctrl**鍵時，此選項會輸入索引鍵的 ASCII 值。|
   |任何有效的虛擬金鑰識別碼。|快速鍵對應表中的下拉式 [索引**鍵**] 方塊包含標準虛擬索引鍵識別碼的清單。|

> [!NOTE]
> 輸入 ASCII 值時，[**修飾**詞] 屬性選項會受到限制。 唯一可供使用的控制索引鍵是**Alt**鍵。

> [!TIP]
> 定義快速鍵的快捷方式是以滑鼠右鍵按一下快速鍵對應表中的一個或多個專案，然後選擇 [**下一個輸入按鍵]** ，然後按鍵盤上的任何按鍵或按鍵組合。
>
> 您也可以從 [**編輯**] 功能表取得這個**下一個關鍵類型**的命令。

**Type**屬性會決定與快速鍵**識別碼**相關聯的快速鍵組合是否會解讀為 ASCII/ANSI 索引鍵值或虛擬索引鍵（VIRTKEY）組合。

- 如果**Type**屬性為**ASCII**，則**修飾**詞屬性只能 `None` 或 `Alt`，或者可以有使用**Ctrl**鍵的快速鍵，如同使用 `^`的索引鍵之前所指定。

- 如果**Type**屬性是**VIRTKEY**，則**修飾**詞和索引**鍵值**的任何組合都是有效的。

> [!NOTE]
> 如果您想要在快速鍵對應表中輸入值，並將值視為 ASCII/ANSI，請在資料表中選取專案的**類型**，並從下拉式清單中選取 [ **ASCII** ]。 不過，如果您使用 [**編輯**] 功能表中的 **[下一個輸入的按鍵]** 命令來指定**金鑰**，則必須先將**Type**屬性從**VIRTKEY**變更為**ASCII** ，*然後再*輸入**金鑰**代碼。

## <a name="accelerator-tables"></a>快速鍵對應表

在C++專案中，您可以在**快速鍵編輯器**中，直接使用就地編輯來編輯快速鍵對應表。

下列程式會參考標準屬性頁的使用，不過，就地編輯和屬性頁方法的結果相同。 使用屬性頁或使用就地編輯所做的變更會立即反映在快速鍵對應表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 按兩下快速鍵對應表中的圖示，即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取資料表中的專案，然後選取以啟用就地編輯。

1. 從下拉式方塊中選取，或輸入就地進行變更：

   - 針對 [**識別碼**]，從清單中選取或輸入以編輯。

   - 針對 [**修飾**詞]，從清單中選取。

   - 針對 [**金鑰**]，從清單中選取或輸入以編輯。

   - 針對 [**類型**]，請從清單中選取 [ **ASCII** ] 或 [ **VIRTKEY** ]。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在開啟的快速鍵對應表中尋找項目

1. 按兩下快速鍵對應表中的圖示，即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取資料行標題，依字母順序排序資料行的內容。 例如，選取 [**識別碼**] 以依字母順序顯示快速鍵對應表中的所有識別碼。

   然後就可以掃描清單並找到項目。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 按兩下快速鍵對應表中的圖示，即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 在快速鍵對應表中按一下滑鼠右鍵，然後選擇 [**新增加速器**]，或選取資料表底部的空白資料列專案。

1. 從 [**識別碼**] 方塊的下拉式清單中選取**識別碼**，或在 [**識別碼**] 方塊中輸入新的*識別碼*。

1. 輸入要當做快速鍵使用的*金鑰*，或按一下滑鼠右鍵並選擇 **[下一個輸入的按鍵**] 來設定按鍵組合，或移至 [功能表] **[編輯] > 下一個輸入的按鍵**。 **Edit**

1. 視需要變更 [**修飾**詞] 和 [**類型**]，然後按**enter**鍵。

> [!NOTE]
> 確定定義的所有快速鍵都是唯一的。 您可以將數個金鑰組合指派給相同的識別碼，而不會產生任何不良的效果，例如， **Ctrl**+**P**和**F8**都可以指派給 ID_PRINT。 不過，指派給多個識別符的按鍵組合將無法正常運作，例如，將**Ctrl**+**Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 按兩下快速鍵對應表中的圖示，即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您要刪除的專案，或按住**Ctrl**或**Shift**鍵，同時選取以選擇多個專案。

1. 按一下滑鼠右鍵並選擇 **刪除**，或移至功能表 **編輯** > **刪除**。

> [!TIP]
> 您也可以按**delete**鍵來刪除。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 開啟這兩個資源腳本檔案中的快速鍵對應表，然後選取您想要移動的專案。

1. 從 [**編輯**] 功能表中，選擇 [**複製**] 或 [**剪**下]。

1. 選取目標資源腳本檔案中的專案，然後從 [**編輯**] 功能表選擇 [**貼**上]。

> [!NOTE]
> 您也可以使用快速鍵進行複製及貼上。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵的屬性

1. 按兩下快速鍵對應表中的圖示，即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要變更的快速鍵，方法是按住**Ctrl**鍵，然後選取每一個按鍵。

1. 移至 [[屬性視窗](/visualstudio/ide/reference/properties-window)]，然後輸入您想要讓所有選取的加速器共用的值。

> [!NOTE]
> 在 [**屬性**] 視窗中，每個 [修飾詞] 值都會顯示為布林屬性。 如果您在 [**屬性**] 視窗中變更 [[修飾](../windows/accelerator-modifier-property.md)詞] 值，快速鍵對應表會將新的修飾詞視為除了先前在其中的任何修飾詞以外的加入。 因此，如果您設定了任何修飾詞值，就必須設定所有的輔助按鍵，以確保每個加速器會共用相同的**修飾**詞設定。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[快速鍵](../windows/predefined-accelerator-keys.md)<br/>
