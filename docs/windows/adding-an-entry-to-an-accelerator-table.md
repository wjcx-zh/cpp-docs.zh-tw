---
title: 將項目新增至快速鍵對應表 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
ms.openlocfilehash: 63ae7296d7571bb70f4ca7abe05f39591cc40ced
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626846"
---
# <a name="adding-an-entry-to-an-accelerator-table-c"></a>將項目新增至快速鍵對應表 （c + +）

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目

1. 在 c + + 專案中，開啟快速鍵對應表在其圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 快速鍵對應表內按一下滑鼠右鍵，然後選擇 **新的 Accelerator**從捷徑功能表或按一下空白資料列項目底部的資料表。

3. 選取 [[識別碼](id-property.md)從識別碼中的下拉式清單方塊，或輸入新的識別碼，在**識別碼**] 方塊中。

4. 型別[金鑰](../windows/accelerator-key-property.md)您想要做為快速鍵或以滑鼠右鍵按一下，然後選擇**下一步 輸入的按鍵**從捷徑功能表，來設定按鍵組合 (**下一個輸入的索引鍵**命令也可從**編輯**功能表)。

5. 變更[修飾詞](../windows/accelerator-modifier-property.md)並[型別](../windows/accelerator-type-property.md)，如有必要。

6. 按 **ENTER** 鍵。

   > [!NOTE]
   > 確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵的組合，指派給相同的影響，例如，ID **Ctrl** + **P**並**F8**可以同時指派給 ID_PRINT。 不過，將 指派給一個以上的 ID 將無法正常運作，比方說，一個按鍵組合**Ctrl** + **Z**指派給 ID_SPELL_CHECK 和 ID_THESAURUS。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[編輯快速鍵對應表](../windows/editing-accelerator-tables.md)<br/>
[快速鍵編輯器](../windows/accelerator-editor.md)