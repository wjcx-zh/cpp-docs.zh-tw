---
title: 建立功能表 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: da5fc355ae11ee5efb1c58be9e33bd4fb8bff02d
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320519"
---
# <a name="creating-menus-c"></a>建立功能表 （c + +）

> [!NOTE]
> **資源視窗**不適用於 Express 版本。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="create-a-standard-menu"></a>建立標準功能表

1. 從**檢視**功能表上，選取**資源檢視**，然後以滑鼠右鍵按一下**功能表**標題並選擇 **加入資源**。 選擇 [ **功能表**]。

1. 在功能表列上選取 [新增項目]  方塊 (有「在這裡輸入」的矩形)。

   ![功能表編輯器中的新項目方塊](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   新增項目方塊

1. 輸入新功能表的名稱，例如「檔案」。

   您輸入的文字會出現在 **功能表** 編輯器和 **[屬性] 視窗** 中的 [[標題]](/visualstudio/ide/reference/properties-window)方塊中。 您可以在任一位置編輯新功能表的屬性。

   一旦在功能表列上指定了新的功能表名稱，[新增項目] 方塊就會右移 (讓您加入另一個功能表)，並在第一個功能表底下開啟另一個 [新增項目] 方塊，讓您加入功能表命令。

   ![展開新的項目方塊](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   輸入功能表名稱之後，[新增項目] 方塊的焦點會移位

   > [!NOTE]
   > 若要建立單一項目 功能表的功能表列上，設定**快顯**屬性設**False**。

## <a name="create-a-submenu"></a>建立子功能表

1. 選取您要建立子功能表的功能表命令。

1. 在顯示於右側的 [ **新增項目** ] 方塊中，輸入新功能表命令的名稱。 這個新命令會先出現在子功能表的功能表上。

1. 將其他功能表命令加入至子功能表的功能表。

## <a name="to-insert-a-new-menu-between-existing-menus"></a>在現有的功能表間插入新的功能表

選取現有的功能表名稱並按**插入**索引鍵。 **新的項目** 方塊中選取的項目之前插入。

   \-或-

在功能表列上按一下滑鼠右鍵，然後選擇 **插入新**從捷徑功能表。

## <a name="add-commands-to-a-menu"></a>將命令加入至功能表

1. 建立功能表。

1. 選取功能表名稱，例如**檔案**。

   每個功能表會展開並公開命令的新項目方塊。 比方說，您可以將命令加入**新增**，**開放**，並**關閉**至**檔案**功能表。

1. 在新的項目方塊中，輸入新功能表命令的名稱。

   > [!NOTE]
   > 您輸入的文字會出現在 **功能表** 編輯器和 **[屬性] 視窗** 中的 [[標題]](/visualstudio/ide/reference/properties-window)方塊中。 您可以在任一位置編輯新功能表的屬性。

   > [!TIP]
   > 您可以定義可讓使用者選取功能表命令的助憶鍵 (熱鍵)。 輸入連字號 (`&`) 將它指定為助憶鍵的字母前面。 使用者可以輸入該字母來選取功能表命令。

1. 在 **屬性**視窗中，選取功能表命令時套用的屬性。 如需詳細資訊，請參閱 <<c0> [ 功能表命令屬性](../windows/menu-command-properties.md)。

1. 在 [**提示字元**方塊中**屬性**] 視窗中，輸入您想要在您的應用程式狀態列中顯示的提示字串。

   此步驟中建立與您建立功能表命令相同的資源識別碼的字串資料表中的項目。

   > [!NOTE]
   > 提示只能套用至功能表項目**快顯**屬性 **，則為 True**。 例如，如果最上層功能表項目有子功能表項目，就可以有提示。 目的**提示**表示會發生什麼情況是如果使用者選取功能表項目。

1. 按下**Enter**完成功能表命令。

   已選取新項目方塊，您就可以建立其他的功能表命令。

## <a name="create-pop-up-menus"></a>建立快顯功能表

[快顯功能表](../mfc/menus-mfc.md) 會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。

一旦您建立功能表資源，您的應用程式程式碼必須載入功能表資源，並使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)讓功能表顯示。 一旦使用者已關閉快顯功能表選取之外，或選取命令，該函數會傳回。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。

### <a name="to-create-a-pop-up-menu"></a>建立快顯功能表

1. 以空白的標題 (請不要提供[標題](../windows/creating-a-menu.md) ) **建立功能表**。

1. [將功能表命令加入至新功能表](../windows/adding-commands-to-a-menu.md)。 移至空白功能表標題下方的第一個功能表命令 (暫時標題顯示為 「 `Type Here`)。 輸入 **標題** 和任何其他資訊。

   對快顯功能表中的其他功能表命令重複此程序。

1. 儲存功能表資源。

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>將快顯功能表連接至您的應用程式

1. （舉例來說） WM_CONTEXTMENU 新增的訊息處理常式。 如需詳細資訊，請參閱 <<c0> [ 將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。

1. 將下列程式碼加入至訊息處理常式：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)傳遞的訊息處理常式是在螢幕座標。

   > [!NOTE]
   > 將快顯功能表連接至您的應用程式需要 MFC。

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>以快顯功能表方式檢視功能表資源

一般來說，當您身處** 功能表**編輯器中，功能表資源會顯示為功能表列。 不過，當程式執行時，您可能有加入至應用程式功能表列的功能表資源。

以滑鼠右鍵按一下  功能表，然後選擇 **快顯視窗以檢視**從捷徑功能表。

   此選項只檢視的喜好設定，且不會修改您的功能表。

   > [!NOTE]
   > 若要變更回功能表列檢視，請按一下**快顯視窗以檢視**一次 （這會移除核取記號並傳回您的功能表列檢視）。

## <a name="edit-multiple-menus-or-menu-commands"></a>編輯多個功能表或功能表命令

### <a name="to-select-multiple-menu-commands"></a>選取多個功能表命令

您可以選取多個功能表名稱或功能表命令來執行大量作業，例如刪除或變更屬性。

按住**Ctrl**機碼，請選取您想要的子功能表命令的功能表。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>移動及複製功能表和功能表命令

您可以移動或複製功能表和功能表命令，方法是使用拖放方法或使用捷徑功能表的命令 (在功能表上按一下滑鼠右鍵)。

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移動或複製功能表或功能表命令

1. 將您要移動的項目拖曳或複製到：

   - 目前功能表中的新位置

   - 其他功能表。 (您可以藉由拖曳滑鼠指標停留在上面以瀏覽至其他功能表。)

1. 當插入輔助線顯示想要的位置時，請放下功能表命令。

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用捷徑功能表命令移動或複製功能表或功能表命令

1. 在一或多個功能表或功能表命令上按一下滑鼠右鍵。

1. 從捷徑功能表選擇 [ **剪下** ] (以移動) 或 [ **複製**]。

1. 如果您要將項目移到另一個功能表資源或資源指令碼檔案，[另一個視窗中開啟](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

1. 選取您要移動或複製目標的功能表或功能表命令位置。

1. 從捷徑功能表上選擇 [ **貼上**]。 移動或複製的項目會放在您選取的項目之前。

   > [!NOTE]
   > 您也可以拖曳、複製和貼上到其他功能表視窗中的其他功能表。

### <a name="to-delete-a-menu-or-menu-command"></a>刪除功能表或功能表命令

1. 以滑鼠右鍵按一下功能表名稱或命令。

1. 從捷徑功能表選擇 [ **刪除** ]。

   > [!NOTE]
   > 同樣地，您可以使用捷徑功能表來執行其他動作，例如複製、剪下、貼上、插入新項目、插入分隔字元、編輯 ID、以快顯方式檢視、檢查助憶鍵等。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)