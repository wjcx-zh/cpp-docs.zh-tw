---
title: 設定快速鍵屬性 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232132"
---
# <a name="setting-accelerator-properties"></a>設定快速鍵屬性

您可以在設定快速鍵屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)在任何時間。 您也可以使用[快速鍵編輯器](../windows/accelerator-editor.md)修改快速鍵對應表中的快速鍵屬性。 所做的變更**屬性** 視窗或**加速器**編輯器有相同的結果： 編輯會立即反映在快速鍵對應表。

## <a name="id-property"></a>ID 屬性

**識別碼**屬性參考程式碼中的每個快速鍵對應表項目。 此項目是在使用者按下快速鍵或按鍵組合，程式將收到的命令值。 若要讓功能表項目相同加速器，讓它們的 Id 相同 （只要快速鍵對應表的識別碼是功能表資源的識別碼相同）。

有三個屬性的每個快速鍵 ID:**修飾詞**屬性，**金鑰**屬性，而**型別**屬性。

## <a name="modifier-property"></a>Modifier 屬性

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

## <a name="key-property"></a>Key 屬性

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

## <a name="type-property"></a>Type 屬性

**型別**屬性會決定是否要將快速鍵 ID 相關聯的快速鍵組合解譯為 ASCII/ANSI 機碼值或 (VIRTKEY) 的虛擬按鍵組合。

- 如果**型別**屬性是 ASCII，**修飾詞**屬性只能`None`或`Alt`，或它可能會使用加速器**Ctrl**索引鍵 （指定的方法是使用金鑰`^`)。

- 如果**型別**屬性是 VIRTKEY 的任意組合`Modifier`和`Key`值無效。

> [!NOTE]
> 如果您想要快速鍵對應表中輸入值，且值為 ASCII/ANSI，只要按一下**型別**從下拉式清單中的選取 ASCII 與資料表中的項目。 不過，如果您使用**下一步 輸入的按鍵**命令 (**編輯**功能表) 來指定`Key`，您必須變更**型別**屬性從 VIRTKEY 為 ASCII *之前先*輸入`Key`程式碼。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[在快速鍵對應表中編輯](../windows/editing-in-an-accelerator-table.md)<br/>
[預先定義的快速鍵](../windows/predefined-accelerator-keys.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>
