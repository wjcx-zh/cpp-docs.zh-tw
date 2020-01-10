---
title: TN061：ON_NOTIFY 和 WM_NOTIFY 訊息
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302233"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061：ON_NOTIFY 和 WM_NOTIFY 訊息

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本技術提示提供新 WM_NOTIFY 訊息的背景資訊，並說明在 MFC 應用程式中處理 WM_NOTIFY 訊息的建議（和最常見）方式。

**Windows 3.x 中的通知訊息**

在 Windows 3.x 中，控制項會通知其父系的事件，例如滑鼠點按、內容和選取專案中的變更，以及藉由將訊息傳送至父系來控制背景繪製。 簡單通知會以特殊的 WM_COMMAND 訊息的形式傳送，並將通知碼（例如 BN_CLICKED）和控制項識別碼封裝成*wParam* ，以及*lParam*中的控制項控制碼。 請注意，由於*wParam*和*lParam*已滿，因此無法傳遞任何額外的資料，這些訊息只能是簡單的通知。 比方說，在 BN_CLICKED 通知中，當按下按鈕時，無法傳送滑鼠游標位置的相關資訊。

當 Windows 3.x 中的控制項需要傳送包含額外資料的通知訊息時，會使用各種特殊用途的訊息，包括 WM_CTLCOLOR、WM_VSCROLL、WM_HSCROLL、WM_DRAWITEM、WM_MEASUREITEM、WM_COMPAREITEM、WM_DELETEITEM、WM_CHARTOITEM、WM_VKEYTOITEM 等等。 這些訊息可以反映回傳送給他們的控制項。 如需詳細資訊，請參閱[TN062： Windows 控制項的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)。

**Win32 中的通知訊息**

對於存在於 Windows 3.1 中的控制項，WIN32 API 會使用 Windows 3.x 中使用的大部分通知訊息。 不過，Win32 也會在 Windows 3.x 中加入許多複雜的複雜控制項。 這些控制項經常需要傳送額外的資料及其通知訊息。 WIN32 API 的設計人員選擇只新增一則訊息（WM_NOTIFY），而不是為每個需要額外資料的新通知加入新的**WM_** <strong>\*</strong>訊息，而是以標準化的方式來傳遞任何數量的額外資料。

WM_NOTIFY 訊息包含在*wParam*中傳送訊息之控制項的識別碼，以及*lParam*中結構的指標。 這個結構可能是**NMHDR**結構或一些較大的結構，其具有**NMHDR**結構做為其第一個成員。 請注意，由於**NMHDR**成員是第一個，因此此結構的指標可以做為**NMHDR**的指標，或作為較大結構的指標（視您轉換的方式而定）。

在大部分的情況下，指標會指向較大的結構，而且您必須在使用它時將它轉換。 在只有幾個通知中，例如一般通知（其名稱開頭為**NM_** ）和工具提示控制項的 TTN_SHOW 和 TTN_POP 通知，都是實際使用的**NMHDR**結構。

**NMHDR**結構或初始成員包含傳送訊息之控制項的控制碼和識別碼，以及通知碼（例如 TTN_SHOW）。 **NMHDR**結構的格式如下所示：

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

若為 TTN_SHOW 訊息，程式**代碼**成員會設定為 TTN_SHOW。

大部分的通知會將指標傳遞至較大的結構，其中包含**NMHDR**結構做為其第一個成員。 比方說，請考慮清單視圖控制項的 LVN_KEYDOWN 通知訊息所使用的結構，當按下清單視圖控制項中的按鍵時，就會傳送此訊息。 指標會指向**LV_KEYDOWN**結構，如下所示：

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

請注意，由於**NMHDR**成員是在此結構中的第一個，因此您在通知訊息中傳遞的指標可以轉換成**NMHDR**的指標或**LV_KEYDOWN**的指標。

**所有新 Windows 控制項的通用通知**

有些通知通用於所有的新 Windows 控制項。 這些通知會將指標傳遞至**NMHDR**結構。

|通知碼|傳送原因|
|-----------------------|------------------|
|NM_CLICK|使用者已在控制項中按下滑鼠左鍵|
|NM_DBLCLK|使用者在控制項中按兩下滑鼠左鍵|
|NM_RCLICK|使用者在控制項中按一下滑鼠右鍵|
|NM_RDBLCLK|使用者按兩下控制項中的滑鼠右鍵|
|NM_RETURN|當控制項具有輸入焦點時，使用者已按下 ENTER 鍵|
|NM_SETFOCUS|控制項已獲得輸入焦點|
|NM_KILLFOCUS|控制項已失去輸入焦點|
|NM_OUTOFMEMORY|控制項無法完成作業，因為沒有足夠的記憶體可用|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY：在 MFC 應用程式中處理 WM_NOTIFY 訊息

函數 `CWnd::OnNotify` 處理通知訊息。 其預設的實作為檢查訊息對應，以取得要呼叫的通知處理常式。 一般來說，您不會覆寫 `OnNotify`。 相反地，您會提供處理函式，並將該處理常式的訊息對應專案新增至您擁有者視窗類別的訊息對應。

透過 ClassWizard 屬性工作表 ClassWizard，可以建立 ON_NOTIFY 訊息對應專案，並為您提供基本架構處理常式函式。 如需使用 ClassWizard 來簡化此作業的詳細資訊，請參閱將[訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式。

ON_NOTIFY 訊息對應宏具有下列語法：

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

其中的參數：

*wNotifyCode*<br/>
要處理之通知訊息的程式碼，例如 LVN_KEYDOWN。

*id*<br/>
傳送通知之控制項的子識別碼。

*memberFxn*<br/>
傳送此通知時所要呼叫的成員函式。

您的成員函式必須以下列原型宣告：

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

其中的參數：

*pNotifyStruct*<br/>
通知結構的指標，如上一節中所述。

*result*<br/>
要在傳回之前設定之結果碼的指標。

## <a name="example"></a>範例

若要指定成員函式 `OnKeydownList1` 從識別碼為 `IDC_LIST1`的 `CListCtrl` 處理 LVN_KEYDOWN 訊息，您可以使用 ClassWizard 將下列內容新增至您的訊息對應：

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

在上述範例中，ClassWizard 所提供的函式為：

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

請注意，ClassWizard 會自動提供適當類型的指標。 您可以透過*pNMHDR*或*pLVKeyDow*存取通知結構。

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

如果您需要為一組控制項處理相同的 WM_NOTIFY 訊息，您可以使用 ON_NOTIFY_RANGE 而不是 ON_NOTIFY。 例如，您可能會有一組按鈕，讓您針對特定的通知訊息執行相同的動作。

當您使用 ON_NOTIFY_RANGE 時，您可以指定範圍的開始和結束子識別碼，藉以指定要處理通知訊息的連續子識別碼範圍。

ClassWizard 不會處理 ON_NOTIFY_RANGE;若要使用它，您必須自行編輯訊息對應。

ON_NOTIFY_RANGE 的訊息對應專案和函數原型如下所示：

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

其中的參數：

*wNotifyCode*<br/>
要處理之通知訊息的程式碼，例如 LVN_KEYDOWN。

*id*<br/>
連續識別碼範圍中的第一個識別碼。

*idLast*<br/>
連續識別碼範圍中的最後一個識別碼。

*memberFxn*<br/>
傳送此通知時所要呼叫的成員函式。

您的成員函式必須以下列原型宣告：

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

其中的參數：

*id*<br/>
傳送通知之控制項的子識別碼。

*pNotifyStruct*<br/>
通知結構的指標，如上所述。

*result*<br/>
要在傳回之前設定之結果碼的指標。

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX，ON_NOTIFY_EX_RANGE

如果您想要通知路由中有多個物件來處理訊息，您可以使用 ON_NOTIFY_EX （或 ON_NOTIFY_EX_RANGE），而不是 ON_NOTIFY （或 ON_NOTIFY_RANGE）。 **Ex**版本和一般版本的唯一差異在於，針對**ex**版本呼叫的成員函式會傳回**布林**值，指出是否應該繼續處理訊息。 從這個函式傳回**FALSE** ，可讓您在一個以上的物件中處理相同的訊息。

ClassWizard 不會處理 ON_NOTIFY_EX 或 ON_NOTIFY_EX_RANGE;如果您想要使用其中一種，您必須自行編輯訊息對應。

ON_NOTIFY_EX 和 ON_NOTIFY_EX_RANGE 的訊息對應專案和函數原型如下所示。 參數的意義與非**EX**版本相同。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

上述兩種情況的原型都相同：

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

在這兩種情況下，*識別碼*會保存傳送通知之控制項的子識別碼。

如果通知訊息已完整處理，您的函式必須傳回**TRUE** ，如果命令路由中的其他物件應該有處理訊息的機會，則傳回**FALSE** 。

## <a name="see-also"></a>請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
