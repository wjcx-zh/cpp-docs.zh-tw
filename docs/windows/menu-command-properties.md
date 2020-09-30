---
title: " (c + +) 的功能表命令"
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
ms.openlocfilehash: a950e7d0156d1b952782fddcdff26718fcf0e291
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504328"
---
# <a name="menu-commands-c"></a> (c + +) 的功能表命令

下列資訊會根據您選取功能表命令時出現在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中的**功能表**屬性進行組織。 雖然 [ **屬性** ] 視窗也可讓您依分類來查看這些屬性，但是這些會依字母順序列出。

|屬性|描述|
|--------------|-----------------|
|**打破**|它可以是下列值之一：<br/>  - **None**：無 break。 此為預設值。<br/>  - 資料**行：對於**靜態功能表，這個值會將功能表命令放在新行上。<br/>      對於快顯功能表，這個值會將功能表命令放在資料行中，而且資料行之間沒有分隔線。<br/>      設定這個屬性只會在執行階段影響功能表的外觀，但在功能表編輯器中卻不會。<br />   - **Bar**：與資料行相同 **，除了針對** 快顯功能表，此值會將新的資料行與舊的資料行分隔。<br/>      設定這個屬性只會在執行時間影響功能表的外觀，而不會影響 **功能表編輯器**中的功能表。|
|**Caption**|標示功能表命令的文字 (功能表名稱)。 若要讓功能表命令的其中一個大寫字母成為助憶鍵，請在其前面加下連字號 (&)。|
|**已核取**|若 **為 True**，則會先檢查功能表命令。 類型： **Bool**。 預設值： **False**。|
|**Enabled**|若為 **False**，則會停用功能表項目。|
|**呈現灰色**|若 **為 True**，功能表命令一開始會呈現灰色且為非使用中。 類型： **Bool**。 預設值： **False**。|
|**說明**|將功能表項目對齊右邊。 預設值： **False**。<br/><br/>例如，[ **說明** ] 功能表命令一律在所有 Windows 應用程式的右邊。 如果您在功能表項目上設定這個屬性，該項目將出現在功能表的最右邊和最尾端。 適用於最上層項目。|
|**識別碼**|定義在標頭中的符號。 類型： **符號**、 **整數**或 **加上引號的字串**。<br/><br/>您可以使用任何通常可在任何編輯器使用的符號，即使 [屬性視窗](/visualstudio/ide/reference/properties-window) 未提供可讓您從中選取的下拉式清單也一樣。|
|**Popup**|若 **為 True**，則功能表命令為快顯功能表。 類型： **Bool**。 預設值：在功能表列上的最上層功能表為 **True** ，否則為 **False**。|
|**提示**|包含反白顯示此功能表命令時要出現在狀態列的文字。 文字會放在字串表中，其識別碼與功能表命令相同。<br/><br/>這個屬性適用於任何類型的專案，但執行階段功能則專屬於 MFC。|
|**由右至左對齊**|在執行階段將功能表列上的功能表命令靠右對齊。 類型： **Bool**。 預設值： **False**。|
|**順序由右至左**|當介面當地語系化為任何由右至左讀取的語言 (例如希伯來文或阿拉伯文) 時，可讓功能表命令由右至左顯示。|
|**Separator**|若 **為 True**，則功能表命令為分隔符號。 類型： **Bool**。 預設值： **False**。|

## <a name="associate-menu-commands"></a>建立功能表命令的關聯

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 使用 **功能表編輯器** 來發出相同的命令，將相同的資源識別碼指派給功能表命令和應用程式快速鍵對應表中的專案。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯

1. 在 **功能表編輯器**中，選取您要的功能表命令。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，將快速鍵的名稱加入 [標題] **** 屬性中：

   - 在功能表標題後面輸入定位鍵 (\t) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。

   - 輸入輔助按鍵的名稱 (**Ctrl**、 **Alt**或 **Shift**) 後面接著加號 (**+**) 以及其他索引鍵的名稱、字母或符號。

   例如，若要將**Ctrl** + **O**指派給 **[檔案**] 功能表上的 [**開啟**] 命令，您可以修改功能表命令的**標題**，使其看起來類似下列文字：

   ```
   &Open...\tCtrl+O
   ```

   當您輸入時， **功能表編輯器** 中的功能表命令會更新，以反映新的標題。

1. 在[快速鍵](./accelerator-editor.md) 編輯器中 **建立快速鍵對應表項目** ，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。

您的 MFC 應用程式可以顯示使用者可選取之每個功能表命令的描述性文字。 使用 [**屬性**] 視窗中的 [**提示**] 屬性，將文字字串指派給每個功能表命令，以顯示描述性文字。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。

- 若要在 MFC 應用程式中建立功能表命令與狀態列文字字串之間的關聯，請在 **功能表編輯器**中，選取功能表命令。 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。

在 c + + 專案中，您可以將存取金鑰指派 (助憶鍵，讓使用者可以在功能表和功能表命令中選取鍵盤) 的功能表。

- 若要將存取權指派給功能表命令) 機碼 (快速鍵，請在 `&` 功能表名稱或命令名稱的字母前面輸入連字號 () ，以將該字母指定為對應的存取金鑰。

   例如，「&檔案」會將**Alt** + **F**設為針對 Microsoft Windows 所**File**撰寫之應用程式中 [檔案] 功能表的快速鍵。

   功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。

> [!NOTE]
> 以滑鼠右鍵按一下功能表，然後選擇 [ **檢查助記**鍵]，確定功能表上的所有存取金鑰都是唯一的。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->
