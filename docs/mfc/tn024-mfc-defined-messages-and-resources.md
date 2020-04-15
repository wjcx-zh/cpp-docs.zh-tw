---
title: TN024：MFC 定義的訊息和資源
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370357"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024：MFC 定義的訊息和資源

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明描述了 MFC 使用的內部 Windows 消息和資源格式。 此資訊解釋了框架的實現,並將説明您調試應用程式。 對於冒險者,即使所有這些資訊被正式不支援,您也可能將其中一些資訊用於高級實現。

本說明包含 MFC 私有實現詳細資訊;所有內容將來都可能發生變化。 MFC 專用 Windows 消息僅在一個應用程式的範圍內有意義,但將來將更改為包含系統範圍的消息。

MFC 專用 Windows 消息和資源類型的範圍位於 Microsoft Windows 預留的「系統」範圍內。 目前,並非所有範圍中的數位都使用,並且將來可以使用範圍中的新數位。 可能更改當前使用的數位。

MFC 專用 Windows 消息的範圍為 0x360->0x37F。

MFC 專用資源類型在 0xF0->0xFF 範圍內。

**MFC 專用視窗訊息**

這些 Windows 消息用於代替 C++虛擬函數,其中視窗物件之間需要相對鬆散的耦合,並且 C++虛擬函數不合適。

這些專用 Windows 消息和相關參數結構在 MFC 專用標頭「AFXPRIV」中聲明。H.. 請注意,包含此標頭的任何代碼都可能依賴於未記錄的行為,並且可能會在未來版本的 MFC 中中斷。

在極少數情況下需要處理這些消息之一,應使用ON_MESSAGE消息映射宏,並使用泛型 LRESULT/WPARAM/LPARAM 格式處理消息。

**WM_QUERYAFXWNDPROC**

此消息將發送到正在創建的視窗。 這在創建過程的早期發送,作為確定 WndProc 是否為**AfxWndProc 的方法。AfxWndProc**返回 1。

|||
|-|-|
|wParam|未使用|
|lParam|未使用|
|傳回|1 如果由**AfxWndProc**處理|

**WM_SIZEPARENT**

在調整大小(`CFrameWnd::OnSize`呼`CFrameWnd::RecalcLayout``CWnd::RepositionBars`叫 呼叫)以重新定位框架一側周圍的控制欄時,此消息透過幀視窗發送到其直接子級。 AFX_SIZEPARENTPARAMS結構包含父項的當前可用用戶端矩形和 HDWP(可能是 NULL),用於`DeferWindowPos`調用 該矩形可最大限度地減少重新繪製。

|||
|-|-|
|wParam|未使用|
|lParam|AFX_SIZEPARENTPARAMS結構的位址|
|傳回|未使用 (0)|

忽略該消息表示視窗不參與佈局。

**WM_SETMESSAGESTRING**

此消息將發送到幀視窗,要求其更新狀態列中的消息行。 可以指定字串 ID 或 LPCSTR(但不能同時指定這兩者)。

|||
|-|-|
|wParam|字串識別碼(或零)|
|lParam|字串的 LPCSTR(或 NULL)|
|傳回|未使用 (0)|

**WM_IDLEUPDATECMDUI**

此消息在空閒時間發送,以實現更新命令 UI 處理程式的空閒時間更新。 如果視窗(通常是控制項)處理消息,它將創建一個`CCmdUI`物件(或派生類的物件),並調用`CCmdUI::DoUpdate`視窗中的每個"項" 這將檢查命令處理程式鏈中物件的ON_UPDATE_COMMAND_UI處理程式。

|||
|-|-|
|wParam|BOOL bDisableifNoHandler|
|lParam|未使用 (0)|
|傳回|未使用 (0)|

*bDisableIfNoHandler*是非零禁用 UI 物件,如果沒有ON_UPDATE_COMMAND_UI也沒有ON_COMMAND處理程式。

**WM_EXITHELPMODE**

此消息將發佈到退出`CFrameWnd`上下文敏感説明模式的。 此消息的接收終止由啟動`CFrameWnd::OnContextHelp`的模式迴圈。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|傳回|未使用|

**WM_INITIALUPDATE**

當文件範本可以安全地執行初始更新時,此消息由文檔範本發送給框架視窗的所有後代。 它映射到呼叫,`CView::OnInitialUpdate`但可用於`CWnd`其他 派生類進行其他單次更新。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|傳回|未使用 (0)|

**WM_RECALCPARENT**

此消息由檢視發送到其父視窗(通過`GetParent`獲得)以強制重新計算佈局(通常,父級將調用`RecalcLayout`)。 這在 OLE 伺服器應用程式中使用,其中幀的大小需要隨著檢視的總大小的增長而增大。

如果父視窗處理此消息,則應返回 TRUE,並將在 lParam 中傳遞的 RECT 與工作區的新大小填充。 當伺服器物件就`CScrollView`地啟動時,這用於正確處理滾動條(然後放在視窗外部時)。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|LPRECT 整流客戶,可能是 NULL|
|傳回|如果返回了新的用戶端矩形,則為 TRUE,否則為 FALSE|

**WM_SIZECHILD**

當使用者調整具有調整大小`COleResizeBar`的控點的大小時`GetOwner`, 此消息將發送到其擁有者視窗(通過 )。 `COleIPFrameWnd`通過嘗試根據使用者請求重新置出幀視窗來回應此消息。

新矩形位於客戶端座標中,相對於包含調整大小的條形的幀視窗,由 lParam 指向。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|LPRECT 重新|
|傳回|未使用 (0)|

**WM_DISABLEMODAL**

此消息將發送到正在停用的幀視窗擁有的所有彈出視窗。 幀視窗使用結果來確定是否禁用彈出視窗。

當幀進入模態狀態時,可以使用它在彈出視窗中執行特殊處理,或防止某些彈出視窗被禁用。 例如,工具提示使用此消息在幀視窗進入模態狀態時自行銷毀。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|傳回|非零到**不**關閉視窗,0 表示視窗將被關閉|

**WM_FLOATSTATUS**

當幀被另一個頂級框架視窗啟動或停用時,此消息將發送到幀窗口擁有的所有彈出視窗。 這在`CMiniFrameWnd`中 實現MFS_SYNCACTIVE用於保持這些彈出視窗的啟動與頂層框架視窗的啟動同步。

|||
|-|-|
|wParam|是下列其中一個值：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|未使用 (0)|

如果設置了FS_SYNCACTIVE並且視窗將其啟動與父幀同步,則返回值應為非零。 `CMiniFrameWnd`當樣式設置為MFS_SYNCACTIVE時,返回非零。

有關詳細資訊,請參閱的`CMiniFrameWnd`實現。

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

當「頂級群組」中的視窗被啟動或停用時,此消息將發送到頂級視窗。 如果視窗是頂級視窗(沒有父視窗或擁有者),或者由此類視窗擁有,則視窗是頂級組的一部分。 此消息與WM_ACTIVATEAPP類似,但在屬於不同進程的視窗混合在單個視窗層次結構中(在 OLE 應用程式中很常見)的情況下,則適用於此消息。

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP,WM_HELPHITTEST,WM_EXITHELPMODE

這些消息用於實現上下文相關的説明。 有關詳細資訊,請參閱[技術說明 28。](../mfc/tn028-context-sensitive-help-support.md)

## <a name="mfc-private-resource-formats"></a>MFC 私有資源格式

目前,MFC 定義了兩種私有資源格式:RT_TOOLBAR和RT_DLGINIT。

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR資源格式

AppWizard 提供的預設工具列基於 RT_TOOLBAR自定義資源,該資源在 MFC 4.0 中引入。 您可以使用工具列編輯器編輯此資源。

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT資源格式

一種 MFC 專用資源格式用於存儲額外的對話框初始化資訊。 這包括儲存在組合框中的初始字串。 此資源的格式不是設計為手動編輯,而是由 Visual C++處理。

可視化C++和此RT_DLGINIT資源不需要使用 MFC 的相關功能,因為使用資源中的資訊有 API 替代方法。 使用 Visual C++可以簡化應用程式的長期編寫、維護和翻譯。

RT_DLGINIT資源的基本結構如下:

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

重複部分包含要將消息發送到的控制 ID、要發送的消息 +(普通 Windows 消息)和可變數據長度。 Windows 訊息以以下形式送出:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

這是一種非常通用的格式,允許任何 Windows 消息和數據內容。 Visual C++資源編輯器和 MFC 僅支援有限的 Windows 消息子集:CB_ADDSTRING組合框的初始清單選擇(數據是文字字串)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
