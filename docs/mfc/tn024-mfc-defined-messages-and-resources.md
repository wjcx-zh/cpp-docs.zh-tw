---
title: TN024:定義的訊息和資源
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 029177821d37d5d26abe0b39ea1581e8a5ad602b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306021"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024:定義的訊息和資源

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本提示描述 MFC 使用的格式建置資源與內部的 Windows 訊息。 這項資訊會說明的 framework，實作，並協助您在偵錯您的應用程式。 探險，即使這項資訊是正式不受支援，您可以使用這項資訊的一些進階的實作。

此提示會包含 MFC 私用實作詳細資料;所有內容在未來都會有所變更。 MFC 私人 Windows 訊息的一個應用程式範圍中具有意義，但未來會變更為包含全系統的訊息。

範圍的 MFC 私人 Windows 訊息和資源類型會保留 「 系統 」 範圍中設定的 Microsoft Windows。 使用目前並非所有的數字的範圍，而且在未來，用於新的數字，範圍中。 目前使用的數字可能會變更。

MFC 私人 Windows 訊息是在範圍內 0x360]-> [0x37F。

MFC 私人資源類型是在範圍內 0xF0]-> [0xFF。

**MFC 私人 Windows 訊息**

這些 Windows 訊息用來取代C++視窗物件之間需要較鬆散的結合性所在的虛擬函式和位置C++無法適當虛擬函式。

在 MFC private 標頭中宣告這些私人 Windows 訊息和相關聯的參數結構 ' AFXPRIV。H'。 會收到警告，任何包含此標頭的程式碼可能會依賴未記載的行為，就會斷開在未來版本的 MFC。

在罕見的需要來處理這些訊息的其中一個案例中，您應該使用 ON_MESSAGE 訊息對應巨集，並處理一般 LRESULT/WPARAM/LPARAM 格式中的訊息。

**WM_QUERYAFXWNDPROC**

此訊息會傳送至視窗的建立。 這一個方法來決定 WndProc 是否為會傳送在建立程序非常早期**AfxWndProc。AfxWndProc**會傳回 1。

|||
|-|-|
|wParam|未使用|
|lParam|未使用|
|傳回|如果所處理的 1 **AfxWndProc**|

**WM_SIZEPARENT**

此訊息由框架視窗期間傳送至其直屬子系調整大小 (`CFrameWnd::OnSize`呼叫`CFrameWnd::RecalcLayout`其會呼叫`CWnd::RepositionBars`) 要調整控制列，周圍框架的側邊的位置。 AFX_SIZEPARENTPARAMS 結構包含目前可用的用戶端矩形的父代和 HDWP （這可能是 NULL），用來呼叫`DeferWindowPos`降到最低重新繪製。

|||
|-|-|
|wParam|未使用|
|lParam|AFX_SIZEPARENTPARAMS 結構的位址|
|傳回|不使用 (0)|

忽略訊息，指出視窗不參與版面配置。

**WM_SETMESSAGESTRING**

此訊息會傳送到框架視窗，詢問其更新狀態 列中的訊息列。 字串識別碼或 LPCSTR 可以指定 （但非兩者皆是）。

|||
|-|-|
|wParam|字串識別碼 （或零）|
|lParam|LPCSTR 字串 （或 NULL）|
|傳回|不使用 (0)|

**WM_IDLEUPDATECMDUI**

若要實作更新命令 UI 處理常式的閒置時間更新閒置時間中傳送此郵件。 如果視窗 （通常是一種控制列） 會處理訊息，它會建立`CCmdUI`物件 （或衍生類別的物件），並呼叫`CCmdUI::DoUpdate`針對每個 「 項目 」 視窗中。 這會接著檢查 ON_UPDATE_COMMAND_UI 處理常式中的命令處理常式鏈結的物件。

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|不使用 (0)|
|傳回|不使用 (0)|

*bDisableIfNoHandler*為非零值以停用 UI 物件，如果沒有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 處理常式。

**WM_EXITHELPMODE**

此訊息張貼至`CFrameWnd`，結束即時線上說明模式。 接收此訊息會終止由啟動強制回應迴圈`CFrameWnd::OnContextHelp`。

|||
|-|-|
|wParam|不使用 (0)|
|lParam|不使用 (0)|
|傳回|未使用|

**WM_INITIALUPDATE**

此訊息會傳送文件範本至所有子系框架視窗的安全，才能進行其初始更新時。 它會對應到呼叫`CView::OnInitialUpdate`但也可用在其他`CWnd`-衍生的類別，其他單次發生的更新。

|||
|-|-|
|wParam|不使用 (0)|
|lParam|不使用 (0)|
|傳回|不使用 (0)|

**WM_RECALCPARENT**

此訊息會由檢視傳送至其父視窗 (透過取得`GetParent`) 來強制配置重新計算 (通常，父代會呼叫`RecalcLayout`)。 這是 OLE 伺服器應用程式的情況使用它所需的畫面格以檢視的大小總計成長大小變大。

如果父視窗處理此訊息應該傳回 TRUE，並填滿傳入的工作區的新大小的 lParam RECT。 這用於`CScrollView`可正確處理捲軸 （然後在視窗中，新加入的外部位置） 的伺服器物件時就地啟用。

|||
|-|-|
|wParam|不使用 (0)|
|lParam|LPRECT rectClient，可能是 NULL|
|傳回|則為 TRUE，如果是新的用戶端矩形，FALSE 否則傳回|

**WM_SIZECHILD**

此訊息會傳送所`COleResizeBar`給其主控視窗 (透過`GetOwner`) 當使用者調整大小的調整大小控點的大小調整列。 `COleIPFrameWnd` 會透過嘗試調整框架視窗的位置，因為使用者已要求回應此訊息。

新的矩形中，指定在工作區座標相對於框架視窗包含 [調整] 列中，指向由 lParam。

|||
|-|-|
|wParam|不使用 (0)|
|lParam|LPRECT rectNew|
|傳回|不使用 (0)|

**WM_DISABLEMODAL**

此訊息會傳送給正在停用的框架視窗所擁有的所有快顯視窗。 框架視窗會使用結果來判斷要停用快顯視窗。

您可以使用這個框架進入強制回應狀態時，您的快顯視窗中執行特殊處理，或防止遭到停用特定的快顯視窗。 工具提示會使用此訊息，當框架視窗會進入強制回應狀態，例如終結本身。

|||
|-|-|
|wParam|不使用 (0)|
|lParam|不使用 (0)|
|傳回|以非零**不**停用視窗中，0 表示視窗將會停用|

**WM_FLOATSTATUS**

此訊息會傳送給框架啟用或停用另一個最上層框架視窗時，框架視窗所擁有的所有快顯視窗。 這由在 MFS_SYNCACTIVE 實作`CMiniFrameWnd`，以保留啟用一個快顯視窗的上層框架視窗啟用同步。

|||
|-|-|
|wParam|是下列值之一：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|不使用 (0)|

傳回的值應為非零是否 FS_SYNCACTIVE 組和視窗將其啟用與父框架。 `CMiniFrameWnd` 樣式設定為 MFS_SYNCACTIVE 時，會傳回非零。

如需詳細資訊，請參閱 < 實作`CMiniFrameWnd`。

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

此訊息會傳送至最上層的視窗中，其 「 最上層群組 」 中的視窗啟用或停用時。 如果它是最上層視窗 （沒有父代或擁有者），或隸屬於這種視窗，視窗會是最上層群組的一部分。 此訊息中使用 WM_ACTIVATEAPP，類似，但在單一視窗階層架構 （通常在 OLE 應用程式） 中混用情況屬於不同的程序的 windows 中運作。

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP，WM_HELPHITTEST，WM_EXITHELPMODE

這些訊息可在實作中的即時線上說明。 請參閱[技術提示 28](../mfc/tn028-context-sensitive-help-support.md)如需詳細資訊。

## <a name="mfc-private-resource-formats"></a>MFC 私用的格式建置資源

目前，MFC 會定義兩個私用資源的格式：RT_TOOLBAR 和 RT_DLGINIT。

## <a name="rttoolbar-resource-format"></a>RT_TOOLBAR 資源格式

AppWizard 所提供的預設工具列根據 RT_TOOLBAR 」 自訂資源，MFC 4.0 中引進。 您可以編輯此資源，使用工具列編輯器。

## <a name="rtdlginit-resource-format"></a>RT_DLGINIT 資源格式

一種 MFC 私用資源的格式用來儲存額外的對話方塊初始化資訊。 這包括初始下拉式方塊中所儲存的字串。 此資源的格式不是以手動方式編輯，但視覺效果由C++。

視覺化C++和這個 RT_DLGINIT 資源不需要使用 MFC 的相關的功能，因為沒有 API 替代項目使用中資源的資訊。 使用視覺效果C++可讓您更容易撰寫、 維護和轉換您的應用程式中，長期。

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

重複的區段包含的控制項識別碼，訊息傳送訊息 # 來傳送 （標準 Windows 訊息） 和可變長度的資料。 Windows 訊息會傳送表單中：

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

這是非常一般的格式，並允許任何 Windows 訊息和資料內容。 視覺效果C++資源編輯器和 MFC 只支援 Windows 訊息的有限的子集：如需初始 （資料是文字字串） 的下拉式方塊清單-選擇 CB_ADDSTRING。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
