---
title: 建立快顯功能表 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702826"
---
# <a name="creating-pop-up-menus-c"></a>建立快顯功能表 （c + +）

[快顯功能表](../mfc/menus-mfc.md) 會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。

一旦您建立功能表資源，您的應用程式程式碼必須載入功能表資源，並使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)讓功能表顯示。 一旦使用者已關閉快顯功能表選取之外，或選取命令，該函數會傳回。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。

## <a name="to-create-a-pop-up-menu"></a>建立快顯功能表

1. 以空白的標題 (請不要提供[標題](../windows/creating-a-menu.md) ) **建立功能表**。

1. [將功能表命令加入至新功能表](../windows/adding-commands-to-a-menu.md)。 移至空白功能表標題下方的第一個功能表命令 (暫時標題顯示為 「 `Type Here`)。 輸入 **標題** 和任何其他資訊。

   對快顯功能表中的其他功能表命令重複此程序。

1. 儲存功能表資源。

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>將快顯功能表連接至您的應用程式

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

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>以快顯功能表方式檢視功能表資源

一般來說，當您身處** 功能表**編輯器中，功能表資源會顯示為功能表列。 不過，當程式執行時，您可能有加入至應用程式功能表列的功能表資源。

以滑鼠右鍵按一下  功能表，然後選擇 **快顯視窗以檢視**從捷徑功能表。

   此選項只檢視的喜好設定，且不會修改您的功能表。

   > [!NOTE]
   > 若要變更回功能表列檢視，請按一下**快顯視窗以檢視**一次 （這會移除核取記號並傳回您的功能表列檢視）。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)
