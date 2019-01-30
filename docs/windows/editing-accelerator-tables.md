---
title: 編輯快速鍵對應表 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
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
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232171"
---
# <a name="editing-accelerator-tables-c"></a>編輯快速鍵對應表 （c + +）

在 c + + 專案中，您可以直接使用就地編輯中編輯快速鍵對應表**加速器**編輯器。

使用標準內容頁，請參閱下列程序，不過，就地編輯和屬性頁方法有相同的結果。 使用屬性頁，或使用就地編輯所做的變更會立即反映在快速鍵對應表中。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

## <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取資料表中的項目，並選取即可啟動就地編輯。

1. 從下拉式方塊中選取，或輸入位置進行變更。

   - 針對[識別碼](id-property.md)，從選取清單或輸入以編輯。

   - 針對[修飾詞](../windows/accelerator-modifier-property.md)，從清單中選取。

   - 針對[金鑰](../windows/accelerator-key-property.md)，從選取清單或輸入以編輯。

   - 針對[型別](../windows/accelerator-type-property.md)，選取**ASCII**或是**VIRTKEY**從清單中。

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在開啟的快速鍵對應表中尋找項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取的資料行行首，以依字母順序排序的資料行的內容。 例如，選取**識別碼**依字母順序顯示快速鍵對應表中的所有識別碼。

然後就可以掃描清單並找到項目。

## <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 快速鍵對應表內按一下滑鼠右鍵，然後選擇 **新的 Accelerator**從捷徑功能表或選取之資料表底部的空白資料列項目。

1. 選取 [[識別碼](id-property.md)從識別碼中的下拉式清單方塊，或輸入新的識別碼，在**識別碼**] 方塊中。

1. 型別[金鑰](../windows/accelerator-key-property.md)您想要做為快速鍵或以滑鼠右鍵按一下，然後選擇**下一步 輸入的按鍵**從捷徑功能表，來設定按鍵組合 (**下一個輸入的索引鍵**命令也可從**編輯**功能表)。

1. 變更[修飾詞](../windows/accelerator-modifier-property.md)並[型別](../windows/accelerator-type-property.md)，如有必要。

1. 按 **Enter** 鍵。

   > [!NOTE]
   > 確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵的組合，指派給相同的影響，例如，ID **Ctrl** + **P**並**F8**可以同時指派給 ID_PRINT。 不過，將 指派給一個以上的 ID 將無法正常運作，比方說，一個按鍵組合**Ctrl** + **Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取您要刪除的項目。 (按住**Ctrl**或是**Shift**鍵同時選取來選擇多個項目。)

1. 以滑鼠右鍵按一下，然後選擇 **刪除**從捷徑功能表 (或選取**刪除**從**編輯**功能表)。

\-或-

- 按下**刪除**索引鍵。

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 在這兩個資源指令碼檔案中開啟快速鍵對應表。

1. 選取您要移動的項目。

1. 從**編輯**功能表上，選擇**複製**或是**剪下**。

1. 選取目標資源指令碼檔案中的項目。

1. 從**編輯**功能表上，選擇**貼上**。

   > [!NOTE]
   > 您也可以使用快速鍵進行複製及貼上。

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵屬性

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

1. 選取您想要變更按住的快速鍵**Ctrl**當您選取每個索引鍵。

1. 移至[屬性 視窗](/visualstudio/ide/reference/properties-window)和您想要選取加速器，若要共用的所有值的型別。

   > [!NOTE]
   > 每個修飾詞值會顯示為布林值屬性中**屬性**視窗。 如果您變更[修飾詞](../windows/accelerator-modifier-property.md)中的值**屬性** 視窗中，快速鍵對應表視為新的修飾詞的補充先前有任何修飾詞。 因為這個緣故，如果您設定任何修飾詞的值，您必須設定它們，以確保每個加速器共用相同的所有**修飾詞**設定。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[快速鍵編輯器](../windows/accelerator-editor.md)<br/>
[資源編輯器](../windows/resource-editors.md)
