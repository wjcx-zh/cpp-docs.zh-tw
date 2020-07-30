---
title: TN006：訊息對應
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: 6b387b851f5a76cd0d11957a87e57307d624759e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228527"
---
# <a name="tn006-message-maps"></a>TN006：訊息對應

此附注描述 MFC 訊息對應功能。

## <a name="the-problem"></a>問題

Microsoft Windows 會在使用其訊息處理功能的視窗類別中，執行虛擬函式。 由於牽涉到大量的訊息，為每個 Windows 訊息提供個別的虛擬函式會建立非常大的 vtable。

由於系統定義的 Windows 訊息數目會隨著時間而改變，而且應用程式可以定義自己的 Windows 訊息，因此，訊息對應會提供一層間接取值，防止介面變更中斷現有的程式碼。

## <a name="overview"></a>概觀

MFC 提供 switch 語句的替代方法，在傳統的 Windows 程式中用來處理傳送至視窗的訊息。 可以定義訊息與方法之間的對應，如此一來，當視窗收到訊息時，就會自動呼叫適當的方法。 這種訊息對應功能的設計是為了與虛擬函式類似，但不能有額外的好處，可以使用 c + + 虛擬函數。

## <a name="defining-a-message-map"></a>定義訊息對應

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)宏會宣告類別的三個成員。

- 稱為 *_messageEntries*之 AFX_MSGMAP_ENTRY 專案的私用陣列。

- 受保護的 AFX_MSGMAP 結構，稱為*messageMap* ，指向 *_messageEntries*陣列。

- 名為的受保護虛擬函式 `GetMessageMap` ，會傳回*messageMap*的位址。

這個宏應該放在任何使用訊息對應之類別的宣告中。 依照慣例，它會在類別宣告的結尾。 例如：

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

這是在建立新的類別時，由程式設定和 ClassWizard 所產生的格式。 ClassWizard 需要//{{和//}} 的括弧。

訊息對應的資料表是使用一組擴充至訊息對應專案的宏來定義的。 資料表是以[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏呼叫為開頭，其定義此訊息對應所處理的類別，以及傳遞未處理之訊息的父類別。 資料表的結尾是[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏呼叫。

在這兩個宏呼叫之間，這是此訊息對應所要處理之每個訊息的專案。 每個標準 Windows 訊息都有一個表單的宏，它會產生該訊息的專案 ON_WM_*MESSAGE_NAME* 。

已定義標準函式簽章，以解除封裝每個 Windows 訊息的參數，並提供型別安全。 這些簽章可能會在[CWnd](../mfc/reference/cwnd-class.md)宣告的 afxwin.h 檔案中找到。 每一個都會標示關鍵字**afx_msg**以方便識別。

> [!NOTE]
> ClassWizard 會要求您在訊息對應處理常式宣告中使用**afx_msg**關鍵字。

這些函式簽章是使用簡單的慣例所衍生。 函式的名稱一律以 "開頭 `"On` 。 後面接著移除「WM_」的 Windows 訊息名稱，並將每個字組的第一個字母大寫。 參數的順序是*wParam* ，後面接著 `LOWORD` （*lParam*） then `HIWORD` （*lParam*）。 未使用的參數不會傳遞。 MFC 類別所包裝的任何控制碼都會轉換成適當 MFC 物件的指標。 下列範例示範如何處理 WM_PAINT 訊息，並讓呼叫函式 `CMyWnd::OnPaint` ：

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

訊息對應表必須在任何函式或類別定義的範圍外定義。 它不應該放在 extern "C" 區塊中。

> [!NOTE]
> ClassWizard 會修改//{{and//}} 批註括弧之間發生的訊息對應專案。

## <a name="user-defined-windows-messages"></a>使用者定義的 Windows 訊息

使用者定義的訊息可能會包含在訊息對應中，方法是使用[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)宏。 這個宏會接受下列格式的訊息編號和方法：

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

在此範例中，我們會建立自訂訊息的處理常式，其中具有衍生自標準 WM_USER 基底之使用者定義訊息的 Windows 訊息識別碼。 下列範例顯示如何呼叫此處理程式：

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

使用此方法的使用者自訂訊息範圍必須在0x7fff 的 WM_USER 範圍內。

> [!NOTE]
> ClassWizard 不支援從 ClassWizard 使用者介面輸入 ON_MESSAGE 處理常式常式。 您必須從 [Visual C++ 編輯器] 手動輸入它們。 ClassWizard 會剖析這些專案，並讓您像其他任何訊息對應專案一樣流覽它們。

## <a name="registered-windows-messages"></a>已註冊的 Windows 訊息

[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函數是用來定義新的視窗訊息，保證在整個系統中都是唯一的。 宏 ON_REGISTERED_MESSAGE 是用來處理這些訊息。 這個宏會接受包含已註冊之 windows 訊息識別碼之*UINT 近端*變數的名稱。 例如：

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

已註冊的 Windows 訊息識別碼變數（在此範例中 WM_FIND）必須是*接近*的變數，因為 ON_REGISTERED_MESSAGE 的執行方式。

使用此方法的使用者自訂訊息範圍會在0xC000 到0xFFFF 的範圍內。

> [!NOTE]
> ClassWizard 不支援從 ClassWizard 使用者介面輸入 ON_REGISTERED_MESSAGE 處理常式常式。 您必須從文字編輯器手動輸入它們。 ClassWizard 會剖析這些專案，並讓您像其他任何訊息對應專案一樣流覽它們。

## <a name="command-messages"></a>命令訊息

來自功能表和加速器的命令訊息會在訊息對應中使用 ON_COMMAND 宏來處理。 這個宏會接受命令 ID 和方法。 只有*wParam*等於指定命令識別碼的特定 WM_COMMAND 訊息，才會由訊息對應專案中指定的方法來處理。 命令處理常式成員函式不接受任何參數並傳回 **`void`** 。 宏的格式如下：

```cpp
ON_COMMAND(id, memberFxn)
```

命令更新訊息會透過相同的機制來路由傳送，但是請改用 ON_UPDATE_COMMAND_UI 宏。 命令更新處理常式成員函式接受單一參數、指向[CCmdUI](../mfc/reference/ccmdui-class.md)物件的指標，然後傳回 **`void`** 。 宏的格式為

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Advanced users 可以使用 ON_COMMAND_EX 宏，這是一種擴充形式的命令訊息處理常式。 宏提供 ON_COMMAND 功能的超集合。 擴充的命令處理常式成員函式會接受單一參數，也就是包含命令識別碼的**UINT** ，並傳回**BOOL**。 傳回值應為**TRUE** ，表示已處理此命令。 否則，路由會繼續進行其他命令目標物件。

這些表單的範例如下：

- 在 Resource. h 中（通常由 Visual C++ 產生）

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- 在類別宣告內

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- 在訊息對應定義內

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 在執行檔中

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

Advanced users 可以使用單一命令處理常式來處理某個範圍的命令： [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)或 ON_COMMAND_RANGE_EX。 如需這些宏的詳細資訊，請參閱產品檔。

> [!NOTE]
> ClassWizard 支援建立 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 處理常式，但不支援建立 ON_COMMAND_EX 或 ON_COMMAND_RANGE 處理常式。 不過，類別 Wizard 會進行剖析，並讓您流覽全部四個命令處理常式變體。

## <a name="control-notification-messages"></a>控制通知訊息

從子控制項傳送至視窗的訊息，其訊息對應專案中會有額外的資訊：控制項的識別碼。 只有在下列條件成立時，才會呼叫訊息對應專案中指定的訊息處理常式：

- 控制項通知碼（ *lParam*的高單字）（例如 BN_CLICKED）符合訊息對應專案中指定的通知碼。

- 控制項 ID （*wParam*）符合訊息對應專案中指定的控制項 id。

自訂控制項通知訊息可能會使用[ON_CONTROL](reference/message-map-macros-mfc.md#on_control)宏來定義具有自訂通知碼的訊息對應專案。 此宏的格式為

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

針對 advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)可以用來處理具有相同處理常式之控制項範圍內的特定控制項通知。

> [!NOTE]
> ClassWizard 不支援在使用者介面中建立 ON_CONTROL 或 ON_CONTROL_RANGE 處理常式。 您必須使用文字編輯器手動輸入它們。 ClassWizard 會剖析這些專案，並讓您像其他任何訊息對應專案一樣流覽它們。

Windows 通用控制項使用功能更強大的[WM_NOTIFY](/windows/win32/controls/wm-notify)來進行複雜的控制項通知。 這一版的 MFC 可直接支援這個新訊息，方法是使用 ON_NOTIFY 並 ON_NOTIFY_RANGE 宏。 如需這些宏的詳細資訊，請參閱產品檔。

## <a name="see-also"></a>另請參閱

[依數位的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)
