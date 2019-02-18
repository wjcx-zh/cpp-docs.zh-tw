---
title: 功能表命令 （c + +）
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
ms.openlocfilehash: 9f91973fdf2d5a45c631f24d3eed41482a91a834
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336601"
---
# <a name="menu-commands-c"></a>功能表命令 （c + +）

下列資訊會根據組織** 功能表**屬性中出現[屬性 視窗](/visualstudio/ide/reference/properties-window)當您選取功能表命令。 這些字母順序列出雖然**屬性**視窗也可讓您依類別檢視這些屬性。

|屬性|描述|
|--------------|-----------------|
|**Break**|可以是下列值之一：<br /><br />- **無**（預設）：不換行。<br />- **資料行**:對於靜態功能表，這個值會將功能表命令放在新的一行。 對於快顯功能表，這個值會將功能表命令放在資料行中，而且資料行之間沒有分隔線。 設定這個屬性只會在執行階段影響功能表的外觀，但在功能表編輯器中卻不會。<br />- **列**:與相同**資料行**除了針對快顯功能表，這個值會區隔新的資料行從舊的資料行，以垂直線。 設定這個屬性會影響功能表的外觀，只有在執行階段，不是在** 功能表**編輯器。|
|**標題**|標示功能表命令的文字 (功能表名稱)。 若要讓功能表命令的其中一個大寫字母成為助憶鍵，請在其前面加下連字號 (&)。|
|**已核取**|如果 **，則為 True**，功能表命令一開始選取。 類型：**Bool**。 預設：**False**。|
|**已啟用**|若為 **False**，則會停用功能表項目。|
|**呈現灰色**|如果 **，則為 True**，功能表命令是一開始呈現灰色，而且非使用中。 類型：**Bool**。 預設：**False**。|
|**說明**|將功能表項目對齊右邊。 例如，[ **說明** ] 功能表命令一律在所有 Windows 應用程式的右邊。 如果您在功能表項目上設定這個屬性，該項目將出現在功能表的最右邊和最尾端。 適用於最上層項目。 預設：**False**。|
|**ID**|定義在標頭中的符號。 類型：**符號**，**整數**，或**加引號的字串**。 您可以使用任何通常可在任何編輯器使用的符號，即使 [屬性視窗](/visualstudio/ide/reference/properties-window) 未提供可讓您從中選取的下拉式清單也一樣。|
|**快顯**|如果 **，則為 True**，功能表命令是快顯功能表。 類型：**Bool**。 預設：**真**最上層功能表的功能表列; 否則為**False**。|
|**提示**|包含反白顯示此功能表命令時要出現在狀態列的文字。 文字會放在字串表中，其識別碼與功能表命令相同。 這個屬性適用於任何類型的專案，但執行階段功能則專屬於 MFC。|
|**由右至左對齊**|在執行階段將功能表列上的功能表命令靠右對齊。 類型：**Bool**。 預設：**False**。|
|**順序由右至左**|當介面當地語系化為任何由右至左讀取的語言 (例如希伯來文或阿拉伯文) 時，可讓功能表命令由右至左顯示。|
|**Separator**|如果 **，則為 True**，功能表命令為分隔符號。 類型：**Bool**。 預設：**False**。|

## <a name="associate-menu-commands"></a>關聯的功能表命令

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 藉由發出相同的命令** 功能表**編輯器，將相同的資源識別碼指派給功能表命令和您的應用程式快速鍵對應表中的項目。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯

1. 在 **功能表** 編輯器中，選取您想要的功能表命令。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，將快速鍵的名稱加入 [標題]  屬性中：

   - 在功能表標題後面輸入定位鍵 (\t) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。

   - 輸入輔助按鍵的名稱 (**Ctrl**， **Alt**，或**Shift**) 後面接著加號 (**+**) 和名稱、 字母，或額外的索引鍵的符號。

   例如，若要指派**Ctrl**+**O**來**開啟**命令**檔案** 功能表中，您可以修改功能表命令**標題**使它看起來類似下列文字：

   ```
   &Open...\tCtrl+O
   ```

   中的功能表命令 **功能表**編輯器會更新以反映新的標題，當您輸入它。

1. 在[快速鍵](../windows/adding-an-entry-to-an-accelerator-table.md) 編輯器中 **建立快速鍵對應表項目** ，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>若要建立功能表命令與狀態列文字字串中，MFC 應用程式的關聯

MFC 應用程式可以針對每個使用者可以選取功能表命令顯示描述性文字。 將文字字串指派給使用您建立每個功能表命令顯示描述性文字**提示**中的屬性**屬性**視窗。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。

1. 在 [ **功能表** ] 編輯器中，選取功能表命令。

1. 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。

> [!NOTE]
> 這組步驟需要 MFC。

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>為功能表命令指派便捷鍵 (快速鍵)

在 c + + 專案中，您可以加入您的功能表和功能表命令指派便捷鍵 （助憶鍵，可讓使用者選取 [鍵盤] 功能表）。

輸入連字號 (`&`) 內的功能表名稱或命令名稱，即可該字母指定為對應的便捷鍵的字母前面。 比方說，"& 檔案"集**Alt**+**F**做為快速鍵的**檔案**撰寫的 Microsoft Windows 應用程式中的功能表。

   功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。

   > [!NOTE]
   > 請在您的功能表上按一下滑鼠右鍵，確定功能表上的所有便捷鍵皆未重複，然後從捷徑功能表中選擇 [檢查助憶鍵]  。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)<br/>
[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>