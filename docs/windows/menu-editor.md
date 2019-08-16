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
ms.openlocfilehash: f2a5f1ac63007bf44dc331e2104c6e9e5cac23da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514821"
---
# <a name="menu-editor-c"></a>功能表編輯器 (C++)

功能表允許您以有邏輯和容易尋找的方式排列命令。 使用**功能表編輯器**, 您可以直接使用與已完成的應用程式相似的功能表列, 來建立和編輯功能表。

> [!TIP]
> 使用**功能表編輯器**時, 在許多情況下, 您可以用滑鼠右鍵按一下來顯示常用命令的快顯功能表。 可用的命令取決於指標所指項目。

## <a name="how-to"></a>如何

**功能表編輯器**可讓您:

### <a name="to-create-a-standard-menu"></a>建立標準功能表

1. 移至功能表**視圖** > **資源檢視**, 並在**功能表**標題上按一下滑鼠右鍵。 依序選擇 [**新增資源**]、[**功能表**]。

1. 在功能表列上選取 [**新增專案**] 方塊 (此處包含 [*類型*] 的矩形)。

   ![功能表編輯器中的 [新增專案]] 方塊(../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   [**新增專案**] 方塊

1. 輸入新功能表的名稱, 例如 [檔案]。

   您輸入的文字會出現在**功能表編輯器**和 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [**標題**] 方塊中。 您可以在任一位置編輯新功能表的屬性。

   一旦在功能表列上指定了新的功能表名稱，[新增項目] 方塊就會右移 (讓您加入另一個功能表)，並在第一個功能表底下開啟另一個 [新增項目] 方塊，讓您加入功能表命令。

   ![展開的 [新增專案]] 方塊(../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   輸入功能表名稱後已移動焦點的 [**新增專案**] 方塊

   > [!NOTE]
   > 若要在功能表列上建立單一專案功能表, 請將**Popup**屬性設定為**False**。

### <a name="to-create-a-submenu"></a>建立子功能表

1. 選取您要建立子功能表的功能表命令。

1. 在顯示於右側的 [ **新增項目** ] 方塊中，輸入新功能表命令的名稱。 這個新命令會先出現在子功能表的功能表上。

1. 將其他功能表命令加入至子功能表的功能表。

### <a name="to-insert-a-new-menu-between-existing-menus"></a>在現有的功能表間插入新的功能表

選取現有的功能表名稱, 然後按下**Insert**鍵, 或在功能表列上按一下滑鼠右鍵, 然後選擇 [**插入新**的]。

   [**新增專案**] 方塊會插入選取的專案之前。

### <a name="to-add-commands-to-a-menu"></a>將命令新增至功能表

1. 建立功能表。 然後選取功能表名稱, 例如 [檔案]。

   每個功能表會展開並公開命令的新項目方塊。 例如, 您可以在 [檔案] 功能表中加入 [**新增**]、[ **開啟**] 和 [**關閉**] 命令。

1. 在新的項目方塊中，輸入新功能表命令的名稱。

   > [!NOTE]
   > 您輸入的文字會出現在**功能表編輯器**和 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [**標題**] 方塊中。 您可以在任一位置編輯新功能表的屬性。

   > [!TIP]
   > 您可以定義可讓使用者選取功能表命令的助憶鍵 (熱鍵)。 在字母前面輸入`&`連字號 (), 將它指定為助憶鍵。 使用者可以輸入該字母來選取功能表命令。

1. 在 [**屬性**] 視窗中, 選取適用的功能表命令屬性。 如需詳細資訊, 請參閱[功能表命令屬性](../windows/menu-command-properties.md)。

1. 在 [**屬性**] 視窗的 [**提示**] 方塊中, 輸入您要在應用程式的狀態列中顯示的提示字串。

   此步驟會在字串資料表中建立一個專案, 其資源識別碼與您建立的功能表命令相同。

   > [!NOTE]
   > 提示只能套用至**Popup**屬性為**True**的功能表項目。 例如，如果最上層功能表項目有子功能表項目，就可以有提示。 **提示**的目的是要指出當使用者選取功能表項目時, 會發生什麼事。

1. 按**enter**鍵以完成功能表命令。

   已選取新項目方塊，您就可以建立其他的功能表命令。

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>若要選取多個功能表命令來執行大量作業, 例如刪除或變更屬性

按住**Ctrl**鍵時, 選取您想要的功能表或子功能表命令。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>移動和複製功能表和功能表命令

- 使用拖放方法:

   1. 將您要移動的項目拖曳或複製到：

      - 目前功能表中的新位置

      - 其他功能表。 您可以藉由將滑鼠指標拖曳至其他功能表, 流覽至其他功能表。

   1. 當插入輔助線顯示想要的位置時，請放下功能表命令。

- 使用快捷方式功能表命令:

   1. 以滑鼠右鍵按一下一或多個功能表或功能表命令, 然後選擇 [**剪**下] (以移動) 或 [**複製**]。

   1. 如果您要將專案移至另一個功能表資源或資源腳本檔案, 請[在另一個視窗中開啟](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

   1. 選取您要移動或複製目標的功能表或功能表命令位置。

   1. 從捷徑功能表上選擇 [ **貼上**]。 移動或複製的項目會放在您選取的項目之前。

> [!NOTE]
> 您也可以拖曳、複製和貼上到其他功能表視窗中的其他功能表。

### <a name="to-delete-a-menu-or-menu-command"></a>刪除功能表或功能表命令

以滑鼠右鍵按一下功能表名稱或命令, 然後選擇 [**刪除**]。

> [!NOTE]
> 同樣地，您可以使用捷徑功能表來執行其他動作，例如複製、剪下、貼上、插入新項目、插入分隔字元、編輯 ID、以快顯方式檢視、檢查助憶鍵等。

## <a name="pop-up-menus"></a>快顯功能表

[快顯功能表](../mfc/menus-mfc.md) 會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。

建立功能表資源之後, 您的應用程式程式碼必須載入功能表資源, 並使用[trackpopupmenu 讓](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)讓功能表出現。 一旦使用者在其外部選取快顯功能表或選取了命令, 該功能就會傳回。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。

> [!NOTE]
> 若為 Microsoft Foundation Class (MFC) 程式庫程式和 ATL 程式, 請使用程式**代碼嚮導**將功能表命令連結至程式碼。 如需詳細資訊, 請參閱[新增事件](../ide/adding-an-event-visual-cpp.md)和將[訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式。

- 若要建立快顯功能表, 請建立具有空白標題的功能表, 而不要提供*標題*。 然後, 將功能表命令新增至 [新增] 功能表, 移至空白功能表標題下方的第一個功能表命令, 並在*這裡*輸入臨時標題類型, 並輸入*標題*和任何其他資訊。

   針對快顯功能表中的任何其他功能表命令重複此程式, 並務必儲存功能表資源。

- 例如, 若要將快顯功能表連接至您的應用程式, 請新增 WM_CONTEXTMENU 的訊息處理常式, 然後將下列程式碼新增至訊息處理常式:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > 訊息處理常式所傳遞的[CPoint](../atl-mfc-shared/reference/cpoint-class.md)是在螢幕座標中。

一般來說, 當您在**功能表編輯器**中工作時, 功能表資源會顯示為功能表列。 不過，當程式執行時，您可能有加入至應用程式功能表列的功能表資源。

- 若要將功能表資源視為快顯功能表, 請以滑鼠右鍵按一下功能表, 然後選擇 [**視圖為**快顯]。

   此選項只是一個流覽喜好設定, 不會修改您的功能表。

> [!TIP]
> 若要變更回功能表列的視圖, 請再次選取 [ **view As Popup** ]。 此動作會移除核取記號, 並返回您的功能表列視圖。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[功能表命令](../windows/menu-command-properties.md)<br/>
[使用者介面物件和命令識別碼](../mfc/user-interface-objects-and-command-ids.md)<br/>
[功能表](../mfc/menus-mfc.md)<br/>
[功能表](/windows/win32/menurc/menus)