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
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366604"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061：ON_NOTIFY 和 WM_NOTIFY 訊息

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本技術說明提供有關新WM_NOTIFY消息的背景資訊,並描述了在 MFC 應用程式中處理WM_NOTIFY消息的建議(也是最常見的)方法。

**Windows 3.x 中的通知訊息**

在 Windows 3.x 中,控制件通過向父級發送消息來通知其父級有關諸如滑鼠按一下、內容和選擇更改以及控制背景繪製等事件。 簡單的通知作為特殊WM_COMMAND消息發送,通知代碼(如BN_CLICKED)和控制 ID 打包到*wParam*中,控制件的句柄在*lParam*中。 請注意,由於*wParam*和*lParam*已滿,因此無法傳遞任何其他數據 – 這些消息只能是簡單的通知。 例如,在BN_CLICKED通知中,無法發送有關按一下按鈕時滑鼠游標位置的資訊。

當 Windows 3.x 中的控制項需要發送包含其他數據的通知消息時,它們使用各種特殊用途的消息,包括WM_CTLCOLOR、WM_VSCROLL、WM_HSCROLL、WM_DRAWITEM、WM_MEASUREITEM、WM_COMPAREITEM、WM_DELETEITEM、WM_CHARTOITEM、WM_VKEYTOITEM等。 這些消息可以反射回發送它們的控制件。 有關詳細資訊,請參閱[TN062:Windows 控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)。

**Win32 中的通知訊息**

對於 Windows 3.1 中存在的控制項,Win32 API 使用 Windows 3.x 中使用的大多數通知消息。 但是,Win32 還會向 Windows 3.x 中支援的控制件添加許多複雜、複雜的控制項。 通常,這些控制者需要發送其他數據及其通知訊息。 Win32 API 的設計者選擇只添加一條消息,即WM_NOTIFY,該消息可以以標準化的方式傳遞任意數量的附加數據,而不是為每個需要額外數據的新通知添加新**WM_**<strong>\*</strong>消息。

WM_NOTIFY消息包含在*wParam*中發送消息的控制項的 ID 和指向*lParam*中結構的指標。 此結構要麼是**NMHDR**結構,要麼是具有**NMHDR**結構作為其第一個成員的較大結構。 請注意,由於**NMHDR**成員是第一個,因此指向此結構的指標可用作指向**NMHDR**的指標或指向較大結構的指標,具體取決於您如何施放它。

在大多數情況下,指標將指向較大的結構,並且在使用它時需要強制轉換它。 在少數通知中,例如常見通知(其名稱以**NM_** 開頭)和工具提示控件的TTN_SHOW和TTN_POP通知)實際上是實際使用的**NMHDR**結構。

**NMHDR**結構或初始成員包含發送消息的控制項的句柄和 ID 以及通知代碼(如TTN_SHOW)。 **NMHDR**結構的格式如下所示:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

對於TTN_SHOW消息,**代碼**成員將設置為TTN_SHOW。

大多數通知傳遞指向包含**NMHDR**結構作為其第一個成員的較大結構的指標。 例如,請考慮列表檢視控制式資訊LVN_KEYDOWN通知消息所使用的結構,該結構在清單檢視控制項中按下鍵時發送。 指標指向**LV_KEYDOWN**結構,該結構的定義如下所示:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

請注意,由於**NMHDR**成員是此結構中的第一個,因此在通知消息中傳遞的指標可以轉換為指向**NMHDR**的指標或指向**LV_KEYDOWN**的指標。

**所有新視窗控制件的訊息**

某些通知是所有新的 Windows 控制件所共有的。 這些通知傳遞指向**NMHDR**結構的指標。

|通知代碼|傳送是因為|
|-----------------------|------------------|
|NM_CLICK|使用者按下控制的左滑鼠按鈕|
|NM_DBLCLK|控制項中使用者按滑鼠按鈕|
|NM_RCLICK|使用者按下控制的滑鼠右鍵|
|NM_RDBLCLK|控制項使用者按下右滑鼠按鈕|
|NM_RETURN|使用者按下 ENTER 鍵,而控制項具有輸入焦點|
|NM_SETFOCUS|已給予控制項輸入焦點|
|NM_KILLFOCUS|控制已遺失輸入焦點|
|NM_OUTOFMEMORY|控制項無法完成操作,因為記憶體不足|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY:在 MFC 應用程式中處理WM_NOTIFY消息

該函數`CWnd::OnNotify`處理通知消息。 其默認實現檢查消息映射,以便通知處理程式呼叫。 通常,您不重寫`OnNotify`。 相反,您提供一個處理程式函數,並將該處理程式的消息映射條目添加到擁有者視窗類的消息映射中。

ClassWizard 通過 ClassWizard 屬性表可以創建ON_NOTIFY消息映射條目,併為您提供骨架處理程式函數。 有關使用 ClassWizard 使其更容易的詳細資訊,請參閱[將消息映射到函數](../mfc/reference/mapping-messages-to-functions.md)。

ON_NOTIFY訊息對應巨集具有以下語法:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

其中的參數：

*wNotifyCode*<br/>
要處理的通知消息的代碼,如LVN_KEYDOWN。

*id*<br/>
發送通知的控制項的子識別碼。

*成員Fxn*<br/>
發送此通知時要調用的成員函數。

成員函數必須使用以下原型聲明:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

其中的參數：

*通知*<br/>
指向通知結構的指標,如上一節所述。

*result*<br/>
返回前要設置的結果代碼的指標。

## <a name="example"></a>範例

要指定成員函數`OnKeydownList1`處理`CListCtrl`來自其`IDC_LIST1`ID 的消息 LVN_KEYDOWN,請使用 ClassWizard 將以下內容新增到消息映射中:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

在上面的範例中,ClassWizard 提供的函數是:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

請注意,ClassWizard 會自動提供正確類型的指標。 您可以通過*pNMHDR*或*pLVKeyDow*訪問通知結構。

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

如果需要為一組控件處理相同的WM_NOTIFY消息,則可以使用ON_NOTIFY_RANGE而不是ON_NOTIFY。 例如,您可能有一組按鈕,您希望對特定通知消息執行相同的操作。

使用ON_NOTIFY_RANGE時,您可以指定一個連續的子標識符範圍,通過指定範圍的開頭和結尾子標識符來處理通知消息。

類嚮導不處理ON_NOTIFY_RANGE;要使用它,您需要自己編輯郵件映射。

ON_NOTIFY_RANGE的消息映射條目和函數原型如下所示:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

其中的參數：

*wNotifyCode*<br/>
要處理的通知消息的代碼,如LVN_KEYDOWN。

*id*<br/>
連續標識符範圍內的第一個標識符。

*idLast*<br/>
連續標識符範圍中的最後一個標識符。

*成員Fxn*<br/>
發送此通知時要調用的成員函數。

成員函數必須使用以下原型聲明:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

其中的參數：

*id*<br/>
發送通知的控制項的子識別碼。

*通知*<br/>
如上所述,指向通知結構的指標。

*result*<br/>
返回前要設置的結果代碼的指標。

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX,ON_NOTIFY_EX_RANGE

如果希望通知路由中有多個對象來處理消息,則可以使用ON_NOTIFY_EX(或ON_NOTIFY_EX_RANGE),而不是ON_NOTIFY(或ON_NOTIFY_RANGE)。 **EX**版本和常規版本的唯一區別是,EX**版本調用**的成員函數返回**BOOL,** 指示消息處理是否應繼續。 透過從此函數傳**回 FALSE,** 您可以在多個物件中處理同一訊息。

ClassWizard 不處理ON_NOTIFY_EX或ON_NOTIFY_EX_RANGE;如果要使用其中任一,則需要自己編輯郵件映射。

ON_NOTIFY_EX和ON_NOTIFY_EX_RANGE的消息映射條目和函數原型如下。 參數的含義與非**EX**版本的含義相同。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

上述兩個原型都相同:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

在這兩種情況下 *,id*都保存發送通知的控制項的子識別碼。

如果通知消息已完全處理,則函數必須返回**TRUE;** 如果命令路由中的其他物件應有機會處理該消息,則函數必須返回**TRUE。**

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
