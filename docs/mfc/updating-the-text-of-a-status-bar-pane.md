---
title: 更新狀態列窗格的文字
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: baf5013e34f262dd3bfed82941697ab9ca21e637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180781"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>更新狀態列窗格的文字

這篇文章說明如何變更會出現在 MFC 狀態列窗格的文字。 狀態列，類別的視窗物件[CStatusBar](../mfc/reference/cstatusbar-class.md) — 包含數個 「 窗格 」。 每個窗格是您可用來顯示資訊的 [狀態] 列的一個矩形區域。 比方說，許多應用程式會在最右邊的窗格中，顯示 CAPS LOCK、 NUM LOCK 和其他索引鍵的狀態。 應用程式也經常顯示的資訊文字，最左邊的窗格 （窗格 0），有時也稱為 「 訊息窗格 」。 例如，預設 MFC 狀態列會使用 [訊息] 窗格，來顯示說明目前選取之功能表項目或工具列按鈕的字串。 中的圖表[狀態列](../mfc/status-bar-implementation-in-mfc.md)顯示從應用程式精靈 建立 MFC 應用程式的狀態列。

根據預設，MFC 不會啟用`CStatusBar`時它會建立窗格 窗格。 若要啟用的窗格中，您必須使用 ON_UPDATE_COMMAND_UI 巨集的 [狀態] 列中的每個窗格，並且更新窗格。 因為窗格不會傳送 WM_COMMAND 訊息 （不像工具列按鈕），您必須以手動方式輸入程式碼。

例如，假設有一個窗格`ID_INDICATOR_PAGE`做為其命令識別碼，它包含文件中目前的頁碼。 下列程序描述如何在狀態列中建立新的窗格。

### <a name="to-make-a-new-pane"></a>若要建立新窗格

1. 定義窗格的命令識別碼。

   在 **檢視**功能表上，按一下**資源檢視**。 以滑鼠右鍵按一下專案資源，然後按一下 **資源符號**。 在 資源符號 對話方塊中，按一下  `New`。 輸入的命令識別碼名稱： 例如， `ID_INDICATOR_PAGE`。 識別碼的指定值，或接受建議的 [資源符號] 對話方塊中的值。 例如，對於`ID_INDICATOR_PAGE`，接受預設值。 關閉 [資源符號] 對話方塊。

1. 定義在窗格中顯示的預設字串。

   資源檢視中開啟，按兩下**字串資料表**在視窗中列出您的應用程式的資源類型。 具有**字串表**編輯器中開啟，選擇**新字串**從**插入**功能表。 在字串屬性 視窗中，選取窗格的命令 ID (例如`ID_INDICATOR_PAGE`) 輸入的預設字串值，例如 「 頁面 」。 關閉字串編輯器。 （您需要預設的字串，以避免編譯器錯誤）。

1. 新增窗格，即可*指標*陣列。

   在 MAINFRM 檔案中。CPP、 找出*指標*陣列。 這個陣列會列出所有 [狀態] 列中的指標，從左到右的順序的命令 Id。 在陣列中的適當點，輸入您的窗格的命令識別碼，如下所示的`ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

若要顯示的文字在窗格中的建議的方式是呼叫`SetText`類別成員函式`CCmdUI`中窗格的更新處理常式函式。 比方說，您可能想要設定將整數變數*m_nPage*包含目前的頁碼和使用`SetText`窗格的文字設該數字的字串版本。

> [!NOTE]
>  `SetText`建議方法。 可以藉由呼叫中執行這項工作，稍微較低層級`CStatusBar`成員函式`SetPaneText`。 即便如此，您仍然需要更新處理常式。 沒有這類處理常式的窗格，MFC 會自動停用 窗格中，清除其內容。

下列程序示範如何使用在窗格中顯示文字的更新處理常式函式。

#### <a name="to-make-a-pane-display-text"></a>要顯示的文字窗格

1. 新增命令的命令更新處理常式。

   手動加入處理常式，原型，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 在適當的。CPP 檔案中，加入處理常式的定義，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   此處理常式的最後三行是程式碼，以便顯示您的文字。

1. 在適當的訊息對應中，新增 ON_UPDATE_COMMAND_UI 巨集，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

一旦您定義的值*m_nPage*成員變數 (類別的`CMainFrame`)，這項技術會導致應用程式會更新其他指標的相同方式出現在窗格中閒置處理期間的頁碼。 如果*m_nPage*變更、 下一步 的閒置迴圈期間顯示變更。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [更新使用者介面物件 （如何更新程式狀況變更工具列按鈕和功能表項目）](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>另請參閱

[MFC 中的狀態列實作](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar 類別](../mfc/reference/cstatusbar-class.md)
