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
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366684"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>更新狀態列窗格的文字

本文介紹如何更改 MFC 狀態列窗格中顯示的文本。 狀態列([類別 CStatusBar](../mfc/reference/cstatusbar-class.md)的視窗物件)包含多個「窗格」。 每個窗格都是狀態列的矩形區域,可用於顯示資訊。 例如,許多應用程式在最右側的窗格中顯示 CAPS 鎖定、NUM LOCK 和其他鍵的狀態。 應用程式還經常在最左側窗格(窗格 0)中顯示資訊性文本,有時稱為"消息窗格"。 例如,預設 MFC 狀態列使用消息窗格顯示解釋當前選擇的功能表項或工具列按鈕的字串。 [狀態列](../mfc/status-bar-implementation-in-mfc.md)中的圖顯示應用程式精靈建立的 MFC 應用程式的狀態列。

默認情況下,MFC 在`CStatusBar`創建窗格時不會啟用窗格。 要啟動窗格,必須對狀態列中的每個窗格使用ON_UPDATE_COMMAND_UI宏並更新窗格。 由於窗格不發送WM_COMMAND消息(它們不喜歡工具列按鈕),因此必須手動鍵入代碼。

例如,假設一個窗格具有`ID_INDICATOR_PAGE`其命令標識符,並且它包含文檔中的當前頁碼。 以下過程介紹如何在狀態列中創建新窗格。

### <a name="to-make-a-new-pane"></a>建立新窗格

1. 定義窗格的命令 ID。

   在 **「視圖」** 選單上,按一下 **「資源檢視**」 。。 右鍵單擊項目資源,然後單擊 **「資源符號**」。。 在「資源符號」 對話框中,`New`按下 。 鍵入命令 ID 名稱:`ID_INDICATOR_PAGE`例如。 指定 ID 的值,或接受資源符號對話方塊建議的值。 例如,對於`ID_INDICATOR_PAGE`,接受預設值。 關閉"資源符號"對話方塊。

1. 定義要在窗格中顯示的預設字串。

   開啟資源檢視後,在列出應用程式資源類型的視窗中按兩下**字串表**。 開啟**字串表編輯**器後,從 **'插入'選**單中選擇 **'新建字串**"。 選擇窗格的命令 ID(`ID_INDICATOR_PAGE`例如 ),然後鍵入預設字串值,如"頁"。 關閉字串編輯器。 (您需要一個預設字串以避免編譯器錯誤。

1. 將窗格添加到*指示器*陣列。

   在檔中 MAINFRM 中。CPP,找到*指標*數位。 此陣列按從左至右的順序出所有狀態列指示器的命令指示。 在陣列中的相應點,輸入窗格的指令 ID,如下所`ID_INDICATOR_PAGE`示 :

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

建議在窗格中顯示文本的方法是在窗格的更新處理程式函數中`SetText`調用`CCmdUI`類 的成員函數。 例如,您可能希望設置包含當前頁碼的整數變數*m_nPage,* 並`SetText`用於將窗格的文本設置為該數位的字串版本。

> [!NOTE]
> 建議`SetText`使用此方法。 通過調用`CStatusBar`成員函`SetPaneText`數 ,可以在稍低的級別執行此任務。 即便如此,您仍然需要一個更新處理程式。 如果沒有窗格的此類處理程式,MFC 會自動禁用窗格,從而停用其內容。

以下過程展示如何使用更新處理程式函數在窗格中顯示文本。

#### <a name="to-make-a-pane-display-text"></a>製作窗格顯示文字

1. 為命令添加命令更新處理程式。

   手動添加處理程式的原型,如下所示`ID_INDICATOR_PAGE`(在 MAINFRM 中)。H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 在適當的 中。CPP 檔,添加處理程式的定義,如下所`ID_INDICATOR_PAGE`示 (在 MAINFRM 中)。CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   此處理程式的最後三行是顯示文本的代碼。

1. 在相應的消息映射中,添加ON_UPDATE_COMMAND_UI宏,如下所示`ID_INDICATOR_PAGE`(在 MAINFRM 中)。CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

定義*m_nPage*成員變數(`CMainFrame`類 )的值後,此技術會導致在空閒處理期間頁碼以與應用程式更新其他指標相同的方式顯示在窗格中。 如果*m_nPage*更改,則顯示在下一個空閒迴圈期間更改。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [更新使用者介面物件(如何更新工具列按鈕和選單項目,因為應用程式條件發生變化)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>另請參閱

[MFC 中的狀態列實作](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar 類別](../mfc/reference/cstatusbar-class.md)
