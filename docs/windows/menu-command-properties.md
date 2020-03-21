---
title: 功能表命令（C++）
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: 972478923a7c4c60d8ff949c5532b00a1de1efc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075509"
---
# <a name="menu-commands-c"></a>功能表命令（C++）

下列資訊是根據您選取功能表命令時，出現在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中的**功能表**屬性來組織。 雖然 [**屬性**] 視窗也可讓您依類別目錄來查看這些屬性，但這些會以字母順序列出。

|屬性|描述|
|--------------|-----------------|
|**Break**|它可以是下列值之一：<br/>  - **無**：不中斷。 這是預設值。<br/>  - **資料行**：對於靜態功能表，這個值會將功能表命令放在新行上。<br/>      對於快顯功能表，這個值會將功能表命令放在資料行中，而且資料行之間沒有分隔線。<br/>      設定這個屬性只會在執行階段影響功能表的外觀，但在功能表編輯器中卻不會。<br />   - **列**：與資料行相同，除了針對快顯功能表，此值會以垂直線分隔新的資料行與舊**的欄。**<br/>      設定這個屬性只會在執行時間影響功能表的外觀，而不是在**功能表編輯器**中。|
|**Caption**|標示功能表命令的文字 (功能表名稱)。 若要讓功能表命令的其中一個大寫字母成為助憶鍵，請在其前面加下連字號 (&)。|
|**已核取**|若**為 True**，則一開始會核取功能表命令。 類型： **Bool**。 預設值： **False**。|
|**已啟用**|若為 **False**，則會停用功能表項目。|
|**呈現灰色**|若**為 True**，則表示功能表命令一開始為灰色且非使用中。 類型： **Bool**。 預設值： **False**。|
|**說明**|將功能表項目對齊右邊。 預設值： **False**。<br/><br/>例如，[ **說明** ] 功能表命令一律在所有 Windows 應用程式的右邊。 如果您在功能表項目上設定這個屬性，該項目將出現在功能表的最右邊和最尾端。 適用於最上層項目。|
|**識別碼**|定義在標頭中的符號。 類型：**符號**、**整數**或**加上引號的字串**。<br/><br/>您可以使用任何通常可在任何編輯器使用的符號，即使 [屬性視窗](/visualstudio/ide/reference/properties-window) 未提供可讓您從中選取的下拉式清單也一樣。|
|**Popup**|若**為 True**，則功能表命令是快顯功能表。 類型： **Bool**。 預設值：如果是功能表列上的最上層功能表，**則為 True** ，否則為**False**。|
|**Prompt**|包含反白顯示此功能表命令時要出現在狀態列的文字。 文字會放在字串表中，其識別碼與功能表命令相同。<br/><br/>這個屬性適用於任何類型的專案，但執行階段功能則專屬於 MFC。|
|**由右至左對齊**|在執行階段將功能表列上的功能表命令靠右對齊。 類型： **Bool**。 預設值： **False**。|
|**順序由右至左**|當介面當地語系化為任何由右至左讀取的語言 (例如希伯來文或阿拉伯文) 時，可讓功能表命令由右至左顯示。|
|**Separator**|如果**為 True**，則表示功能表命令是分隔符號。 類型： **Bool**。 預設值： **False**。|

## <a name="associate-menu-commands"></a>建立功能表命令的關聯

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 使用**功能表編輯器**來發出相同的命令，以將相同的資源識別碼指派給功能表命令以及應用程式的快速鍵對應表中的專案。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯

1. 在**功能表編輯器**中，選取您想要的功能表命令。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，將快速鍵的名稱加入 [標題] 屬性中：

   - 在功能表標題後面輸入定位鍵 (\t) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。

   - 輸入輔助按鍵（**Ctrl**、 **Alt**或**Shift**）的名稱，後面接著加號（ **+** ）和其他索引鍵的名稱、字母或符號。

   例如，若要將**Ctrl**+**O**指派給 [檔案 **] 功能表上**的 [**開啟**] 命令，您可以修改功能表命令的**標題**，使其看起來像下列文字：

   ```
   &Open...\tCtrl+O
   ```

   **功能表編輯器**中的功能表命令會更新，以在您輸入時反映新的標題。

1. 在[快速鍵](../windows/adding-an-entry-to-an-accelerator-table.md) 編輯器中 **建立快速鍵對應表項目** ，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。

您的 MFC 應用程式可以顯示使用者可選取之每個功能表命令的描述性文字。 使用 [**屬性**] 視窗中的 [**提示**] 屬性，將文字字串指派給每個功能表命令，以顯示描述性文字。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。

- 若要在 MFC 應用程式中將功能表命令與狀態列文字字串建立關聯，請在**功能表編輯器**中，選取功能表命令。 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。

在C++專案中，您可以指派存取金鑰（允許使用者使用鍵盤選取功能表的助憶鍵）至功能表和功能表命令。

- 若要指派存取權（快捷方式）索引鍵至功能表命令，請在 [功能表名稱] 或 [命令名稱] 中，輸入字母前面的連字號（`&`），將該字母指定為對應的存取金鑰。

   例如，「& 檔案」會將**Alt**+**F**設定為針對 Microsoft Windows 撰寫之應用程式中的 [檔案 **] 功能表的**快速鍵。

   功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。

> [!NOTE]
> 以滑鼠右鍵按一下功能表，然後選擇 [**檢查助記**鍵]，確定功能表上的所有存取金鑰都是唯一的。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->