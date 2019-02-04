---
title: 將功能表命令 （c + +） 建立關聯
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703034"
---
# <a name="associating-menu-commands-c"></a>將功能表命令 （c + +） 建立關聯

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 藉由發出相同的命令** 功能表**編輯器，將相同的資源識別碼指派給功能表命令和您的應用程式快速鍵對應表中的項目。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯

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

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>若要建立功能表命令與狀態列文字字串中，MFC 應用程式的關聯

MFC 應用程式可以針對每個使用者可以選取功能表命令顯示描述性文字。 將文字字串指派給使用您建立每個功能表命令顯示描述性文字**提示**中的屬性**屬性**視窗。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。

1. 在 [ **功能表** ] 編輯器中，選取功能表命令。

1. 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。

> [!NOTE]
> 這組步驟需要 MFC。

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>為功能表命令指派便捷鍵 (快速鍵)

在 c + + 專案中，您可以加入您的功能表和功能表命令指派便捷鍵 （助憶鍵，可讓使用者選取 [鍵盤] 功能表）。

輸入連字號 (`&`) 內的功能表名稱或命令名稱，即可該字母指定為對應的便捷鍵的字母前面。 比方說，"& 檔案"集**Alt**+**F**做為快速鍵的**檔案**撰寫的 Microsoft Windows 應用程式中的功能表。

   功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。

   > [!NOTE]
   > 請在您的功能表上按一下滑鼠右鍵，確定功能表上的所有便捷鍵皆未重複，然後從捷徑功能表中選擇 [檢查助憶鍵]  。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)<br/>
[將命令新增至功能表](../windows/adding-commands-to-a-menu.md)<br/>
[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
