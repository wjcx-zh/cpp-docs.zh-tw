---
title: TN024：MFC 定義的訊息和資源
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 9ad6827e4a46bb9f2ff3b02986a01737772e0858
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839214"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024：MFC 定義的訊息和資源

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此附注描述 MFC 使用的內部 Windows 訊息和資源格式。 這項資訊說明架構的執行，並可協助您進行應用程式的偵錯工具。 在冒險中，即使所有這項資訊都正式受到支援，您也可以使用這項資訊來進行先進的實施。

此附注包含 MFC 私用執行詳細資料;所有內容在未來都有可能變更。 MFC 私用 Windows 訊息在某個應用程式的範圍內具有意義，但未來將會變更，以包含全系統的訊息。

MFC 私用 Windows 訊息和資源類型的範圍是由 Microsoft Windows 所設定的保留「系統」範圍。 目前不會使用範圍中的所有數位，未來會使用範圍中的新數位。 目前使用的數位可能會變更。

MFC 私用 Windows 訊息位於 0x360->0x37F 的範圍內。

MFC 私用資源類型位於 0xF0->0xFF 的範圍內。

**MFC 私用 Windows 訊息**

這些 Windows 訊息是用來取代 c + + 虛擬函式，在視窗物件與 c + + 虛擬函式不適當的情況下，需要較鬆散的結合性。

這些私用 Windows 訊息和相關聯的參數結構會在 MFC 私用標頭 ' AFXPRIV.H 中宣告。H '。 請注意，任何包含此標頭的程式碼都可能依賴未記載的行為，而且可能會在未來的 MFC 版本中中斷。

在罕見的情況下，需要處理其中一個訊息，您應該使用 ON_MESSAGE 訊息對應宏，並以一般 LRESULT/WPARAM/LPARAM 格式來處理訊息。

**WM_QUERYAFXWNDPROC**

這則訊息會傳送至正在建立的視窗。 在建立過程中，這會隨著決定 WndProc 是否 AfxWndProc 的方法，在建立過程中提早傳送 **。AfxWndProc** 會傳回1。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用|
|lParam|未使用|
|傳回|1（若由**AfxWndProc**處理）|

**WM_SIZEPARENT**

這則訊息會在調整大小 (呼叫的大小時傳送給它的直屬子系， `CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` 而呼叫 `CWnd::RepositionBars`) 來調整框架側邊的控制列位置。 AFX_SIZEPARENTPARAMS 結構包含父系的目前可用用戶端矩形和 HDWP (，它可能是 Null) ，用來呼叫以將重新 `DeferWindowPos` 繪製最小化。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用|
|lParam|AFX_SIZEPARENTPARAMS 結構的位址|
|傳回|未使用 (0) |

如果忽略此訊息，則表示該視窗不會納入版面配置中。

**WM_SETMESSAGESTRING**

這則訊息會傳送至框架視窗，要求它更新狀態列中的訊息行。 您可以 (指定字串識別碼或 LPCSTR，但不能同時指定這兩個) 。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|字串識別碼 (或零) |
|lParam|LPCSTR 字串 (或 Null) |
|傳回|未使用 (0) |

**WM_IDLEUPDATECMDUI**

這則訊息會在閒置時間內傳送，以執行更新命令 UI 處理常式的閒置時間更新。 如果視窗 (通常是控制列) 處理訊息，它會建立 `CCmdUI` 物件 (或衍生類別的物件) 並 `CCmdUI::DoUpdate` 針對視窗中的每個 "items" 進行呼叫。 這會接著檢查命令處理常式鏈中物件的 ON_UPDATE_COMMAND_UI 處理常式。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|未使用 (0) |
|傳回|未使用 (0) |

如果沒有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 處理常式，則*bDisableIfNoHandler*為非零值，可停用 UI 物件。

**WM_EXITHELPMODE**

這則訊息會張貼至 `CFrameWnd` ，以結束上下文相關的說明模式。 此訊息的接收會終止由啟動的強制回應迴圈 `CFrameWnd::OnContextHelp` 。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用 (0) |
|lParam|未使用 (0) |
|傳回|未使用|

**WM_INITIALUPDATE**

檔範本會將此訊息傳送至框架視窗的所有下階，以安全地進行初始更新。 它會對應至的呼叫， `CView::OnInitialUpdate` 但可以在其他衍生類別中用來 `CWnd` 進行其他一次的更新。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用 (0) |
|lParam|未使用 (0) |
|傳回|未使用 (0) |

**WM_RECALCPARENT**

此訊息是由視圖傳送至其父視窗， (透過) 取得， `GetParent` 以強制進行版面配置重新計算 (通常是父代會呼叫 `RecalcLayout`) 。 這是在 OLE 伺服器應用程式中使用，在此情況下，框架必須隨著視圖的總大小成長而成長。

如果父視窗處理此訊息，它應該會傳回 TRUE，並以工作區的新大小填滿 lParam 中傳遞的 RECT。 這是用在中 `CScrollView` ，以適當地處理捲軸， (接下來在視窗的外部，在伺服器物件為就地啟用時) 。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用 (0) |
|lParam|LPRECT rectClient，可能是 Null|
|傳回|如果傳回新的用戶端矩形則為 TRUE，否則為 FALSE。|

**WM_SIZECHILD**

`COleResizeBar`當使用者以調整大小控點調整調整列的大小時，會透過) 將此訊息傳送至其擁有者視窗 (`GetOwner` 。 `COleIPFrameWnd` 藉由嘗試在使用者要求的情況下重新調整框架視窗的位置，來回應此訊息。

在與包含調整大小列的框架視窗相關的用戶端座標中提供的新矩形，會由 lParam 指向。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用 (0) |
|lParam|LPRECT rectNew|
|傳回|未使用 (0) |

**WM_DISABLEMODAL**

這則訊息會傳送至已停用的框架視窗所擁有的所有快顯視窗。 框架視窗會使用結果來判斷是否要停用快顯視窗。

當框架進入強制回應狀態時，您可以使用此功能在快顯視窗中執行特殊處理，或防止某些快顯視窗被停用。 例如，當框架視窗進入強制回應狀態時，工具提示會使用這個訊息來終結本身。

| 參數和傳回值 | 描述 |
|-|-|
|wParam|未使用 (0) |
|lParam|未使用 (0) |
|傳回|非零表示 **不** 停用視窗，0表示將停用視窗|

**WM_FLOATSTATUS**

當其他最上層框架視窗啟用或停用框架時，此訊息會傳送至框架視窗擁有的所有快顯視窗。 這是用來執行中的 MFS_SYNCACTIVE `CMiniFrameWnd` ，讓這些快顯視窗與最上層框架視窗的啟用保持同步。

| 參數 | 描述 |
|-|-|
|wParam|是下列其中一個值：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTI加值稅E<br /><br /> FS_DEACTI加值稅E<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|未使用 (0) |

如果已設定 FS_SYNCACTIVE，且視窗 syncronizes 其啟用與父框架，則傳回值應為非零。 `CMiniFrameWnd` 當樣式設定為 MFS_SYNCACTIVE 時，會傳回非零。

如需詳細資訊，請參閱的實作為 `CMiniFrameWnd` 。

## <a name="wm_activatetoplevel"></a>WM_ACTI加值稅ETOPLEVEL

當「最上層群組」中的視窗已啟用或停用時，此訊息會傳送至最上層視窗。 如果視窗是最上層視窗 (沒有父代或擁有者) ，或是由這類視窗所擁有，則視窗是最上層群組的一部分。 這則訊息與 WM_ACTI加值稅EAPP 的用法類似，但適用于屬於不同進程的 windows 會混合在單一視窗階層中， (在 OLE 應用程式) 中常見的情況。

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP、WM_HELPHITTEST WM_EXITHELPMODE

這些訊息是用來執行即時線上說明。 如需詳細資訊，請參閱 [技術提示 28](../mfc/tn028-context-sensitive-help-support.md) 。

## <a name="mfc-private-resource-formats"></a>MFC 私用資源格式

目前，MFC 會定義兩種私用資源格式： RT_TOOLBAR 和 RT_DLGINIT。

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR 資源格式

執行程式所提供的預設工具列是以 MFC 4.0 中引進的 RT_TOOLBAR 自訂資源為基礎。 您可以使用工具列編輯器來編輯此資源。

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT 資源格式

一個 MFC 私用資源格式可用來儲存額外的對話初始化資訊。 這包括儲存在下拉式方塊中的初始字串。 此資源的格式不是為了手動編輯而設計，而是由 Visual C++ 處理。

Visual C++ 和此 RT_DLGINIT 資源不需要使用 MFC 的相關功能，因為使用資源中的資訊可替代 API。 使用 Visual C++ 可讓您更輕鬆地在長時間內撰寫、維護和轉譯您的應用程式。

RT_DLGINIT 資源的基本結構如下所示：

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

重複的區段包含要將訊息傳送至其中的控制項識別碼，訊息 # 可傳送 (一般 Windows 訊息) 和可變長度的資料。 Windows 訊息會以下列格式傳送：

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

這是非常一般的格式，可允許任何 Windows 訊息和資料內容。 Visual C++ 資源編輯器和 MFC 僅支援一組有限的 Windows 訊息子集： CB_ADDSTRING 用於下拉式方塊的初始清單選項， (資料是) 的文字字串。

## <a name="see-also"></a>另請參閱

[依編號的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)
