---
title: TN006： 訊息對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121672"
---
# <a name="tn006-message-maps"></a>TN006：訊息對應

此提示描述 MFC 訊息對應工具。

## <a name="the-problem"></a>問題

Microsoft Windows 使用其傳訊功能的視窗類別中實作虛擬函式。 因為有大量的相關訊息，每個 Windows 訊息提供個別的虛擬函式會建立極大型的 vtable。

因為系統定莪 Windows 訊息的數目隨著時間變更，而且因為應用程式可以定義自己的 Windows 訊息，訊息對應提供中斷現有的程式碼時，防止介面變更的間接取值層級。

## <a name="overview"></a>概觀

MFC 提供傳統 windows 程式中使用來處理訊息傳送至視窗的 switch 陳述式的替代方案。 如此一來當視窗收到一則訊息，會自動呼叫適當的方法，可以定義從訊息對應至方法。 此訊息對應功能設計類似於虛擬函式，但還有其他好處無法以 c + + 虛擬函式。

## <a name="defining-a-message-map"></a>定義訊息對應

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)巨集宣告三個類別的成員。

- 私用陣列 AFX_MSGMAP_ENTRY 項目稱為 *_messageEntries*。

- 受保護的 AFX_MSGMAP 結構稱為*messageMap* ，它會指向 *_messageEntries*陣列。

- 受保護的虛擬函式，呼叫`GetMessageMap`所傳回的位址*messageMap*。

這個巨集都應該放在使用訊息對應任何類別的宣告。 依照慣例，它是在類別宣告的結尾。 例如: 

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

這是在建立新的類別時，AppWizard 及 ClassWizard 所產生的格式。 / / {{，/ /}} ClassWizard 需要方括號。

使用一組訊息對應項目展開的巨集已定義的訊息對應的資料表。 表格最開始先[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)巨集呼叫，定義處理此訊息對應的類別和未處理的訊息傳遞到父類別。 在資料表結尾[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)巨集呼叫。

這些兩個巨集呼叫會針對每個訊息來處理此訊息對應項目。 每個標準 Windows 訊息有巨集的表單 ON_WM_*MESSAGE_NAME*產生該訊息的項目。

已定義的標準函式簽章來解除封裝的每個 Windows 訊息的參數及提供類型安全。 這些簽章可能會找到檔 Afxwin.h 中宣告的[CWnd](../mfc/reference/cwnd-class.md)。 關鍵字會標示每個**afx_msg**為了易於識別。

> [!NOTE]
> ClassWizard 會要求您使用**afx_msg**您訊息對應處理常式宣告中的關鍵字。

 使用簡單的慣例所衍生這些函式簽章。 函式的名稱永遠會以啟動`"On`"。 這被後面接著"WM_"移除與 Windows 訊息的名稱和每個字大寫的第一個字母。 參數的順序是*wParam*後面`LOWORD`(*lParam*) 然後`HIWORD`(*lParam*)。 未使用的參數不會傳遞。 任何 MFC 類別所包裝的控制代碼會轉換成適當的 MFC 物件的指標。 下列範例示範如何處理 WM_PAINT 訊息及造成`CMyWnd::OnPaint`呼叫函式：

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 訊息對應表格必須定義範圍以外的任何函式或類別定義。 不應在 extern"C"區塊中。

> [!NOTE]
> ClassWizard 會修改訊息對應項目之間發生的 / / {{，/ /}} 註解括號。

## <a name="user-defined-windows-messages"></a>使用者定義的 Windows 訊息

使用者定義的訊息可能會包含在訊息對應使用[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)巨集。 這個巨集接受訊息編號和形式的方法：

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

在此範例中，我們會建立包含衍生自使用者定義訊息的標準 WM_USER 基底的 Windows 訊息識別碼的自訂訊息的處理常式。 下列範例會示範如何呼叫這個處理常式：

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

使用此方法的使用者定義訊息的範圍必須是要 0x7fff WM_USER 範圍中。

> [!NOTE]
> ClassWizard 不支援從 ClassWizard 使用者介面的輸入 ON_MESSAGE 處理常式。 您必須手動輸入他們從 Visual c + + 編輯器。 類別精靈將會剖析這些項目，並可讓您瀏覽它們，就像任何其他訊息對應項目。

## <a name="registered-windows-messages"></a>已註冊的 Windows 訊息

[RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函式用來定義新的視窗訊息，保證是唯一的整個系統。 ON_REGISTERED_MESSAGE 巨集用來處理這些訊息。 此巨集接受名稱*UINT 附近*變數，其中包含已註冊的 windows 訊息識別碼。 例如

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

已註冊的 Windows 訊息識別碼變數 (在此範例中 WM_FIND) 必須是*NEAR* ON_REGISTERED_MESSAGE 實作方式的變數。

使用此方法的使用者定義訊息的範圍會在 0xC000 到 0xFFFF 的範圍內。

> [!NOTE]
> ClassWizard 不支援從 ClassWizard 使用者介面的輸入 ON_REGISTERED_MESSAGE 處理常式。 您必須手動輸入他們從文字編輯器。 類別精靈將會剖析這些項目，並可讓您瀏覽它們，就像任何其他訊息對應項目。

## <a name="command-messages"></a>命令訊息

ON_COMMAND 巨集使用的訊息對應處理命令訊息，從功能表和快速鍵。 這個巨集接受命令 ID 和方法。 只有特定 WM_COMMAND 訊息具有*wParam*等於指定的命令 ID 由訊息對應項目中指定的方法。 命令處理常式成員函式不接受任何參數，並傳回**void**。 巨集具有下列格式：

```cpp
ON_COMMAND(id, memberFxn)
```

命令更新訊息會路由傳送到相同的機制，但改為使用 ON_UPDATE_COMMAND_UI 巨集。 命令更新處理常式成員函式採用單一參數的指標[CCmdUI](../mfc/reference/ccmdui-class.md)物件，並傳回**void**。 巨集已表單

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

進階的使用者可以使用 ON_COMMAND_EX 巨集，也就是命令訊息處理常式的延伸的格式。 巨集提供 ON_COMMAND 功能的超集。 擴充的命令處理常式成員函式採用單一參數， **UINT**包含命令 ID，但傳回**BOOL**。 傳回值應為**TRUE**指出命令已經處理過。 否則路由將會繼續其他命令目標物件。

這些格式的範例包括：

- 在 Resource.h （通常是由 Visual c + + 所產生）

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- 類別宣告中

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- 訊息對應定義內

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 在實作檔

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

 進階的使用者可以使用單一命令處理常式來處理命令的範圍： [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)或 ON_COMMAND_RANGE_EX。 請參閱產品文件，如需有關這些巨集。

> [!NOTE]
> ClassWizard 支援建立的 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 處理常式，但不支援建立 ON_COMMAND_EX 或 ON_COMMAND_RANGE 處理常式。 不過，類別精靈將會剖析，並可讓您瀏覽所有四個命令處理常式的變數。

## <a name="control-notification-messages"></a>控制項通知訊息

從視窗的子控制項具有額外的位元其訊息中的資訊傳送的訊息對應項目： 控制項的 id。 只有當下列條件成立時，才呼叫訊息對應項目中指定的訊息處理常式：

- 控制項通知碼 (高的字組的*lParam*)，例如 BN_CLICKED，符合指定的訊息對應項目中的通知碼。

- 控制項 ID (*wParam*) 符合指定的訊息對應項目中的控制項識別碼。

自訂控制項通知訊息可能會使用[ON_CONTROL](reference/message-map-macros-mfc.md#on_control)巨集來定義自訂通知碼的訊息對應項目。 這個巨集已表單

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

供進階使用[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)可以用來處理特定的控制項通知從相同的處理常式之控制項的範圍。

> [!NOTE]
> ClassWizard 不支援使用者介面中建立 ON_CONTROL 或 ON_CONTROL_RANGE 處理常式。 必須由您手動輸入的文字編輯器。 類別精靈將會剖析這些項目，並可讓您瀏覽它們，就像任何其他訊息對應項目。

Windows 通用控制項使用功能更強大[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)複雜控制項通知。 這個版本的 MFC 使用 ON_NOTIFY 和 ON_NOTIFY_RANGE 巨集已直接支援此新訊息。 請參閱產品文件，如需有關這些巨集。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
