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
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907642"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>更新狀態列窗格的文字

本文說明如何變更出現在 MFC 狀態列窗格中的文字。 狀態列（ [CStatusBar](../mfc/reference/cstatusbar-class.md)類別的視窗物件）包含數個「窗格」。 每個窗格都是狀態列的矩形區域，可供您用來顯示資訊。 例如，許多應用程式會在最右邊的窗格中顯示 CAPS LOCK、NUM LOCK 和其他按鍵的狀態。 應用程式通常也會在最左邊的窗格（窗格0）中顯示資訊文字，有時也稱為「訊息窗格」。 例如，預設 MFC 狀態列會使用 [訊息] 窗格來顯示字串，說明目前選取的功能表項目或工具列按鈕。 [狀態列](../mfc/status-bar-implementation-in-mfc.md)中的圖表會顯示由應用程式精靈建立的 MFC 應用程式所產生的狀態列。

根據預設，MFC 在建立窗格時`CStatusBar`不會啟用窗格。 若要啟動窗格，您必須針對狀態列上的每個窗格使用 ON_UPDATE_COMMAND_UI 宏，並更新窗格。 因為窗格不會傳送 WM_COMMAND 訊息（它們不像工具列按鈕），所以您必須手動輸入程式碼。

例如，假設有`ID_INDICATOR_PAGE`一個窗格的命令識別碼是，而且它包含檔中的目前頁碼。 下列程式描述如何在狀態列中建立新的窗格。

### <a name="to-make-a-new-pane"></a>若要建立新的窗格

1. 定義窗格的命令識別碼。

   在 [ **View** ] 功能表上，按一下 [**資源檢視**]。 以滑鼠右鍵按一下專案資源，然後按一下 [**資源符號**]。 在 [資源符號] 對話方塊中， `New`按一下 []。 輸入命令識別碼名稱：例如， `ID_INDICATOR_PAGE`。 指定 ID 的值，或接受 [資源符號] 對話方塊所建議的值。 例如，針對`ID_INDICATOR_PAGE`，接受預設值。 關閉 [資源符號] 對話方塊。

1. 定義要顯示在窗格中的預設字串。

   在資源檢視開啟時，在列出應用程式資源類型的視窗中按兩下 [**字串資料表**]。 開啟 [**字串表**編輯器]，從 [**插入**] 功能表中選擇 [**新字串**]。 選取您窗格的命令識別碼（例如， `ID_INDICATOR_PAGE`），並輸入預設字串值，例如 "Page"。 關閉 [字串編輯器]。 （您需要預設字串以避免編譯器錯誤。）

1. 將窗格加入至指標*陣列。*

   在 [檔案 MAINFRM.CPP] 中。CPP，找出*指示器*陣列。 此陣列會列出所有狀態列指標的命令識別碼，順序由左至右。 在陣列中的適當點上，輸入您窗格的命令識別碼，如下所示`ID_INDICATOR_PAGE`：

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

在窗格中顯示文字的建議方式是，在窗格的`SetText`更新處理常式函`CCmdUI`式中呼叫類別的成員函式。 例如，您可能會想要設定包含目前頁碼的整數變數*m_nPage* ，並使用`SetText`將窗格的文字設定為該數位的字串版本。

> [!NOTE]
>  建議`SetText`使用此方法。 您可以藉由呼叫`CStatusBar`成員函式，在稍微較低的層級上執行這項工作。 `SetPaneText` 就算如此，您仍然需要更新處理常式。 如果沒有此窗格的處理常式，MFC 會自動停用窗格，並清除其內容。

下列程式顯示如何使用更新處理常式函式，在窗格中顯示文字。

#### <a name="to-make-a-pane-display-text"></a>若要建立窗格顯示文字

1. 為命令新增命令更新處理常式。

   手動新增處理常式的原型，如下所示`ID_INDICATOR_PAGE` （在 mainfrm.cpp 中）。H）：

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 在適當的中。CPP 檔案，請新增處理常式的定義，如下所示`ID_INDICATOR_PAGE` （在 mainfrm.cpp 中）。CPP）：

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   這個處理常式的最後三行是顯示文字的程式碼。

1. 在適當的訊息對應中，新增 ON_UPDATE_COMMAND_UI 宏，如下所示`ID_INDICATOR_PAGE` （在 mainfrm.cpp 中）。CPP）：

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

一旦您定義了*m_nPage*成員變數（屬於類別`CMainFrame`）的值，這項技術會使頁碼在閒置處理期間顯示于窗格中，就像應用程式更新其他指示器的方式一樣。 如果*m_nPage*變更，則顯示會在下一個閒置迴圈期間變更。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [更新使用者介面物件（如何更新工具列按鈕和功能表項目做為程式條件變更）](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>另請參閱

[MFC 中的狀態列實作](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar 類別](../mfc/reference/cstatusbar-class.md)
