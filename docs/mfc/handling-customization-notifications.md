---
title: 處理自訂告知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
dev_langs:
- C++
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34d9a0fad325c95b9de43e28269b00ad7ced4b95
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416704"
---
# <a name="handling-customization-notifications"></a>處理自訂告知

Windows 工具列通用控制項內建自訂功能 (包括系統定義的自訂對話方塊)，可讓使用者插入、刪除或重新排列工具列按鈕。 應用程式會判斷是否可以使用自訂功能，並控制使用者可自訂工具列的範圍。

您可以將這些自訂功能提供給使用者讓工具列**CCS_ADJUSTABLE**樣式。 自訂功能可讓使用者將按鈕拖曳至新的位置，或者拖曳出工具列以移除按鈕。 此外，使用者可以按兩下工具列顯示 [自訂工具列]  對話方塊，讓使用者加入、刪除及重新排列工具列按鈕。 應用程式可以使用 [[自訂]](../mfc/reference/ctoolbarctrl-class.md#customize) 成員函式來顯示此對話方塊。

工具列控制項會在自訂程序中的每個步驟，將通知訊息傳送至父視窗。 如果使用者按住 SHIFT 鍵並開始拖曳按鈕，工具列會自動處理拖曳作業。 工具列會將 **TBN_QUERYDELETE** 通知訊息傳送至父視窗，以判斷是否可刪除此按鈕。 如果父視窗傳回 **FALSE**，則結束拖曳作業。 否則，工具列會擷取滑鼠輸入，並等候使用者放開滑鼠按鈕。

當使用者放開滑鼠按鈕時，工具列控制項會判斷滑鼠游標的位置。 如果游標位於工具列之外，則已刪除按鈕。 如果游標位於另一個工具列按鈕上，則工具列會將 **TBN_QUERYINSERT** 通知訊息傳送至父視窗，以判斷是否可將按鈕插入指定按鈕的左方。 如果父視窗傳回 **TRUE**，則已插入按鈕；否則未插入。 工具列傳送 **TBN_TOOLBARCHANGE** 通知訊息來表示結束拖曳作業。

如果使用者未按住 SHIFT 鍵便開始拖曳作業，工具列控制項會將 **TBN_BEGINDRAG** 通知訊息傳送至主控視窗。 自行實作按鈕拖曳程式碼的應用程式可以使用這則訊息來表示開始拖曳作業。 工具列傳送 **TBN_ENDDRAG** 通知訊息來表示結束拖曳作業。

當使用者使用 [自訂工具列]  對話方塊自訂工具列時，工具列控制項會傳送通知訊息。 在使用者按兩下工具列之後到建立對話方塊之前，工具列會傳送 **TBN_BEGINADJUST** 通知訊息。 接下來，工具列會開始傳送一系列的 **TBN_QUERYINSERT** 通知訊息，以判斷工具列是否允許插入按鈕。 當父視窗傳回 **TRUE**時，工具列會停止傳送 **TBN_QUERYINSERT** 通知訊息。 如果父視窗未針對任何按鈕傳回 **TRUE** ，則工具列會終結對話方塊。

接下來，工具列控制項會針對工具列中的每個按鈕傳送一則 **TBN_QUERYDELETE** 通知訊息，來判斷是否可從工具列中刪除任何按鈕。 父視窗傳回 **TRUE** 表示可刪除按鈕，否則會傳回 **FALSE**。 工具列會將所有工具列按鈕加入對話方塊中，但將那些無法刪除的按鈕設為灰色。

每當工具列控制項需要 [自訂工具列] 對話方塊中按鈕的相關資訊時，便會傳送 **TBN_GETBUTTONINFO** 通知訊息，並指定需要資訊的按鈕索引，以及 **TBNOTIFY** 結構的位址。 父視窗必須以相關資訊填入結構。

[自訂工具列]  對話方塊包含 [說明] 按鈕和 [重設] 按鈕。 當使用者選擇 [說明] 按鈕時，工具列控制項會傳送 **TBN_CUSTHELP** 通知訊息。 父視窗應該會顯示說明資訊來回應。 當使用者選取 [重設] 按鈕時，對話方塊會傳送 **TBN_RESET** 通知訊息。 這則訊息表示工具列即將重新初始化對話方塊。

這些訊息全部都是 **WM_NOTIFY** 訊息，可在您的主控視窗中進行處理，方法是將下列格式訊息對應項目加入主控視窗的訊息對應中：

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   通知訊息識別項代碼，例如 **TBN_BEGINADJUST**。

- **idControl**

   傳送通知之控制項的識別項。

- **memberFxn**

   收到這則通知時所要呼叫的成員函式。

您的成員函式會使用下列原型宣告：

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

如果通知訊息處理常式傳回一個值，應將該值放在 **result** 所指向的 *LRESULT*。

針對每則訊息， `pNotifyStruct` 會指向 **NMHDR** 結構或 **TBNOTIFY** 結構。 這些結構的說明如下：

**NMHDR** 結構包含下列成員：

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   傳送通知之控制項的視窗控制代碼。 若要將這個控制代碼轉換成 `CWnd` 指標，請使用 [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle)。

- **idFrom**

   傳送通知之控制項的識別項。

- **程式碼**

   通知碼。 這個成員可以是控制項類型的特定值 (例如 **TBN_BEGINADJUST** 或 **TTN_NEEDTEXT**)，也可以是下列其中一個一般通知值：

   - **NM_CLICK** 使用者在控制項內按一下滑鼠左鍵。

   - **NM_DBLCLK** 使用者在控制項內按兩下滑鼠左鍵。

   - **NM_KILLFOCUS** 控制項已遺失輸入焦點。

   - **NM_OUTOFMEMORY** 控制項無法完成作業，因為沒有足夠的記憶體可供使用。

   - **NM_RCLICK** 使用者在控制項內按一下滑鼠右鍵。

   - **NM_RDBLCLK** 使用者在控制項內按兩下滑鼠右鍵。

   - **NM_RETURN** 控制項有輸入焦點，而且使用者已按下 ENTER 鍵。

   - **NM_SETFOCUS** 控制項已收到輸入焦點。

**TBNOTIFY** 結構包含下列成員：

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   所有 **WM_NOTIFY** 訊息的共通資訊。

- **iItem**

   與通知相關聯的按鈕索引。

- **tbButton**

   **TBBUTTON**與通知相關聯的結構，其中包含工具列按鈕的相關資訊。

- **cchText**

   按鈕文字中的字元計數。

- **lpszText**

   按鈕文字的指標。

工具列傳送的通知如下：

- **TBN_BEGINADJUST**

   當使用者開始自訂工具列控制項時，就會傳送。 指向包含通知資訊之 **NMHDR** 結構的指標。 此處理常式不需要傳回任何特定值。

- **TBN_BEGINDRAG**

   當使用者開始拖曳工具列控制項中的按鈕時，就會傳送。 指向 **TBNOTIFY** 結構的指標。 **iItem** 成員包含所要拖曳的按鈕之以零為起始的索引。 此處理常式不需要傳回任何特定值。

- **TBN_CUSTHELP**

   當使用者在 [自訂工具列] 對話方塊中選擇 [說明] 按鈕時，就會傳送。 沒有傳回值。 指向包含通知訊息資訊之 **NMHDR** 結構的指標。 此處理常式不需要傳回任何特定值。

- **TBN_ENDADJUST**

   當使用者停止自訂工具列控制項時，就會傳送。 指向包含通知訊息資訊之 **NMHDR** 結構的指標。 此處理常式不需要傳回任何特定值。

- **TBN_ENDDRAG**

   當使用者停止拖曳工具列控制項中的按鈕時，就會傳送。 指向 **TBNOTIFY** 結構的指標。 **iItem** 成員包含所要拖曳的按鈕之以零為起始的索引。 此處理常式不需要傳回任何特定值。

- **TBN_GETBUTTONINFO**

   當使用者正在自訂工具列控制項時，就會傳送。 工具列會使用這項通知訊息，來擷取 [自訂工具列] 對話方塊所需的資訊。 指向 **TBNOTIFY** 結構的指標。 **iItem** 成員指定按鈕之以零為起始的索引。 **pszText** 和 **cchText** 成員指定目前按鈕文字的的位址和長度 (以字元為單位)。 應用程式應該以按鈕的相關資訊填入結構。 如果按鈕資訊已複製到結構，則傳回 **TRUE** ；否則傳回 **FALSE** 。

- **TBN_QUERYDELETE**

   使用者正在自訂工具列，以判斷是否可刪除按鈕從工具列控制項時傳送。 指向 **TBNOTIFY** 結構的指標。 **iItem** 成員包含所要刪除的按鈕之以零為起始的索引。 傳回 **TRUE** 表示可刪除按鈕，傳回 **FALSE** 表示無法刪除按鈕。

- **TBN_QUERYINSERT**

   當使用者正在自訂工具列控制項，以判斷是否可以將按鈕插入指定按鈕的左邊時傳送。 指向 **TBNOTIFY** 結構的指標。 **iItem** 成員包含所要插入的按鈕之以零為起始的索引。 傳回 **TRUE** 表示可在指定按鈕之前插入按鈕，傳回 **FALSE** 表示無法插入按鈕。

- **TBN_RESET**

   當使用者重設 [自訂工具列] 對話方塊中的內容時，就會傳送。 指向包含通知訊息資訊之 **NMHDR** 結構的指標。 此處理常式不需要傳回任何特定值。

- **TBN_TOOLBARCHANGE**

   使用者已自訂工具列控制項之後傳送。 指向包含通知訊息資訊之 **NMHDR** 結構的指標。 此處理常式不需要傳回任何特定值。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

