---
title: 功能表編輯器 (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
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
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: 09d385404edbc33883d2d2add2328b33876d23ae
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504647"
---
# <a name="menu-editor-c"></a>功能表編輯器 (C++)

功能表允許您以有邏輯和容易尋找的方式排列命令。 具有**功能表編輯器**，您可以建立和編輯功能表直接使用功能表列，密切類似於中完成的應用程式。

> [!TIP]
> 在使用時**功能表編輯器**，在許多情況下，您可以按一下滑鼠右鍵顯示常用命令的快顯功能表。 可用的命令取決於指標所指項目。

## <a name="how-to"></a>如何

**功能表編輯器**可讓您：

### <a name="to-create-a-standard-menu"></a>建立標準功能表

1. 移至功能表**檢視** > **資源檢視**並以滑鼠右鍵按一下**功能表**標題。 選擇**加入資源**，然後**功能表**。

1. 選取 [**新的項目**] 方塊中 (包含的矩形*這裡輸入*) 功能表列上。

   ![功能表編輯器中的新項目方塊](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **新的項目**方塊

1. 例如，輸入新的功能表中，名稱*檔案*。

   您輸入的文字會出現在**功能表編輯器**然後在**標題**方塊中[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以在任一位置編輯新功能表的屬性。

   一旦在功能表列上指定了新的功能表名稱，[新增項目] 方塊就會右移 (讓您加入另一個功能表)，並在第一個功能表底下開啟另一個 [新增項目] 方塊，讓您加入功能表命令。

   ![展開新的項目方塊](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **新的項目**之後輸入功能表名稱方塊具有焦點會移位

   > [!NOTE]
   > 若要建立單一項目 功能表的功能表列上，設定**快顯**屬性設**False**。

### <a name="to-create-a-submenu"></a>建立子功能表

1. 選取您要建立子功能表的功能表命令。

1. 在顯示於右側的 [ **新增項目** ] 方塊中，輸入新功能表命令的名稱。 這個新命令會先出現在子功能表的功能表上。

1. 將其他功能表命令加入至子功能表的功能表。

### <a name="to-insert-a-new-menu-between-existing-menus"></a>在現有的功能表間插入新的功能表

選取現有的功能表名稱並按**插入**鍵，或以滑鼠右鍵按一下功能表列上，選擇**插入新**。

   **新的項目** 方塊中選取的項目之前插入。

### <a name="to-add-commands-to-a-menu"></a>將命令新增至功能表

1. 建立功能表。 然後選取功能表名稱，例如**檔案**。

   每個功能表會展開並公開命令的新項目方塊。 比方說，您可以將命令加入**新增**，**開放**，並**關閉**至**檔案**功能表。

1. 在新的項目方塊中，輸入新功能表命令的名稱。

   > [!NOTE]
   > 您輸入的文字會出現在**功能表編輯器**然後在**標題**方塊中[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以在任一位置編輯新功能表的屬性。

   > [!TIP]
   > 您可以定義可讓使用者選取功能表命令的助憶鍵 (熱鍵)。 輸入連字號 (`&`) 將它指定為助憶鍵的字母前面。 使用者可以輸入該字母來選取功能表命令。

1. 在 **屬性**視窗中，選取功能表命令時套用的屬性。 如需詳細資訊，請參閱 <<c0> [ 功能表命令屬性](../windows/menu-command-properties.md)。

1. 在 [**提示字元**方塊中**屬性**] 視窗中，輸入您想要在您的應用程式狀態列中顯示的提示字串。

   此步驟中建立與您建立功能表命令相同的資源識別碼的字串資料表中的項目。

   > [!NOTE]
   > 提示只能套用至功能表項目**快顯**屬性 **，則為 True**。 例如，如果最上層功能表項目有子功能表項目，就可以有提示。 目的**提示**表示會發生什麼情況是如果使用者選取功能表項目。

1. 按下**Enter**完成功能表命令。

   已選取新項目方塊，您就可以建立其他的功能表命令。

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>若要選取多個功能表命令，以執行大量作業，例如刪除或變更屬性

按住**Ctrl**機碼，請選取您想要的子功能表命令的功能表。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>移動及複製功能表和功能表命令

- 使用拖放的方法：

   1. 將您要移動的項目拖曳或複製到：

      - 目前功能表中的新位置

      - 其他功能表。 您可以藉由拖曳滑鼠指標停留的瀏覽至其他功能表。

   1. 當插入輔助線顯示想要的位置時，請放下功能表命令。

- 使用捷徑功能表命令：

   1. 以滑鼠右鍵按一下其中一個或多個功能表或功能表命令，然後選擇**剪下**（以移動） 或**複製**。

   1. 如果您要將項目移到另一個功能表資源或資源指令碼檔案，[另一個視窗中開啟](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

   1. 選取您要移動或複製目標的功能表或功能表命令位置。

   1. 從捷徑功能表上選擇 [ **貼上**]。 移動或複製的項目會放在您選取的項目之前。

> [!NOTE]
> 您也可以拖曳、複製和貼上到其他功能表視窗中的其他功能表。

### <a name="to-delete-a-menu-or-menu-command"></a>刪除功能表或功能表命令

以滑鼠右鍵按一下功能表名稱或命令，然後選擇 **刪除**。

> [!NOTE]
> 同樣地，您可以使用捷徑功能表來執行其他動作，例如複製、剪下、貼上、插入新項目、插入分隔字元、編輯 ID、以快顯方式檢視、檢查助憶鍵等。

## <a name="pop-up-menus"></a>快顯功能表

[快顯功能表](../mfc/menus-mfc.md) 會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。

一旦您建立功能表資源，您的應用程式程式碼必須載入功能表資源，並使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)讓功能表顯示。 一旦使用者已關閉快顯功能表選取之外，或選取命令，該函數會傳回。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。

> [!NOTE]
> Microsoft Foundation Class (MFC) 程式庫程式和 ATL 程式，請使用**程式碼精靈**連結至程式碼的功能表命令。 如需詳細資訊，請參閱 <<c0> [ 加入事件](../ide/adding-an-event-visual-cpp.md)並[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。

- 若要建立快顯功能表，建立以空白的標題的功能表，並不提供*標題*。 然後，新增至新功能表的 功能表命令，移至第一個功能表命令，使用暫存的標題空白功能表標題下方*在這裡輸入*並輸入*標題*和任何其他資訊。

   針對快顯功能表中的其他功能表命令重複此程序，並務必儲存功能表資源。

- 若要連接您的應用程式的快顯功能表，比方說，新增訊息處理常式，如 WM_CONTEXTMENU，那麼訊息處理常式中加入下列程式碼：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)傳遞的訊息處理常式是在螢幕座標。

一般來說，當您身處**功能表編輯器**，功能表資源會顯示為功能表列。 不過，當程式執行時，您可能有加入至應用程式功能表列的功能表資源。

- 若要檢視為快顯功能表的功能表資源，以滑鼠右鍵按一下  功能表，然後選擇**快顯視窗以檢視**。

   此選項只檢視的喜好設定，且不會修改您的功能表。

> [!TIP]
> 若要變更回功能表列檢視，請選取**快顯視窗以檢視**一次。 此動作會移除核取記號，並傳回您的功能表列檢視。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[功能表命令](../windows/menu-command-properties.md)<br/>
[使用者介面物件和命令識別碼](../mfc/user-interface-objects-and-command-ids.md)<br/>
[功能表](../mfc/menus-mfc.md)<br/>
[功能表](/windows/desktop/menurc/menus)