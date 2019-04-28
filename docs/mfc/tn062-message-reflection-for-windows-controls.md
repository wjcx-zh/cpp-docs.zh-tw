---
title: TN062:Windows 控制項的訊息反映
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: aa189eec430d72bef753fef7ebbe9ad929d76c87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351837"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062:Windows 控制項的訊息反映

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

這個技術提示說明訊息反映，MFC 4.0 的新功能。 它也包含用來建立簡單的可重複使用控制項，會使用訊息反映的指示進行。

這個技術提示不討論訊息反映，因為這適用於 ActiveX 控制項 （先前稱為 OLE 控制項）。 請參閱文章[ActiveX 控制項：子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

**何謂訊息反映**

Windows 控制項通常會傳送通知訊息至其父視窗。 比方說，許多控制項會將控制色彩通知訊息 （WM_CTLCOLOR 或其中一個變化） 傳送至其父代，以便提供繪製控制項的背景筆刷的父代。

在 Windows 和 MFC 4.0 版之前，就有一個父視窗，通常是對話方塊中，負責處理這些訊息。 這表示，處理訊息的程式碼必須在父視窗的類別，而且它具有需要處理該訊息的每個類別內的重複。 在上述案例中，每個想要使用自訂背景的控制項的對話方塊者必須處理控制項的色彩通知訊息。 它會更容易重複使用程式碼，如果可寫入的控制項類別，會處理自己的背景色彩。

在 MFC 4.0 中的舊機制仍能運作，父視窗可以處理通知訊息。 此外，不過，MFC 4.0 促進重複使用藉由提供一項稱為 「 訊息反映 」 功能，可讓子控制項視窗或 [父] 視窗中，或在處理這些通知訊息。 在控制項背景的色彩範例中，您現在可以撰寫控制項類別，藉由處理反映的 WM_CTLCOLOR 訊息設定自己的背景色彩，完全不需要依賴父代。 (請注意，因為訊息反映實作 mfc，不透過 Windows，父視窗類別必須衍生自`CWnd`的訊息反映來運作。)

舊版的 MFC 未類似訊息反映藉由提供一些訊息，例如訊息為主控描繪清單方塊 （WM_DRAWITEM，等等） 的虛擬函式。 新的訊息反映機制是通用且一致。

訊息反映為 4.0 之前的版本的 MFC 撰寫程式碼的回溯相容。

如果您有提供特定訊息的處理常式，或某個範圍內的父視窗的類別中的訊息，則會覆寫反映相同的訊息的訊息處理常式，提供您不要在您自己的處理常式中呼叫基底類別處理常式函式。 比方說，如果您在您的對話方塊類別中處理 WM_CTLCOLOR，您的處理將會覆寫任何反映的訊息處理常式。

如果在父視窗類別中，您可以提供特定的 WM_NOTIFY 訊息或範圍的 WM_NOTIFY 訊息的處理常式，將會傳送這些訊息的子控制項沒有透過反映的訊息處理常式時，才會呼叫您的處理常式`ON_NOTIFY_REFLECT()`。 如果您使用`ON_NOTIFY_REFLECT_EX()`在訊息對應中，您的訊息處理常式可能會或可能不允許的父視窗，以處理訊息。 如果處理常式傳回**假**，由父代，傳回的呼叫時處理訊息 **，則為 TRUE**不允許處理它的父代。 請注意，處理反映的訊息的通知訊息之前。

WM_NOTIFY 訊息傳送時，控制項就會提供第一次的機會處理它。 如果任何其他反映的訊息傳送時，父視窗已處理的第一個機會，而且控制項會收到反映的訊息。 若要這樣做，它需要的處理常式函式和適當的項目在控制項的類別訊息對應中。

反映訊息的訊息對應巨集已與通知規則稍有不同： 它有 *_REFLECT*附加至其一般名稱。 比方說，以處理 WM_NOTIFY 訊息父項中的，您會使用在父項的訊息對應中的 ON_NOTIFY 巨集。 若要處理反映的訊息中的子控制項，請在 子控制項的訊息對應中使用 ON_NOTIFY_REFLECT 巨集。 在某些情況下，參數也有不同。 請注意 ClassWizard 可以通常為您新增的訊息對應項目，並提供基本架構的函式實作，使用正確的參數。

請參閱[TN061:ON_NOTIFY 和 WM_NOTIFY 訊息](../mfc/tn061-on-notify-and-wm-notify-messages.md)針對新的 WM_NOTIFY 訊息的詳細資訊。

**訊息對應項目和反映訊息的處理常式函式原型**

若要處理反映的控制項通知訊息，使用訊息對應巨集和函式原型列在表中。

ClassWizard 通常可以為您新增這些訊息對應項目，並提供基本架構的函式實作。 請參閱[定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)如需有關如何定義反映訊息的處理常式資訊。

若要轉換的訊息名稱反映巨集名稱，前面加上*ON_* 附加 *_REFLECT*。 例如，WM_CTLCOLOR 會變成 ON_WM_CTLCOLOR_REFLECT。 （若要查看哪些訊息可以會反映，執行相反的轉換，在下表中的巨集項目上）。

上述規則的三個例外狀況如下所示：

- WM_COMMAND 通知巨集是 ON_CONTROL_REFLECT。

- WM_NOTIFY 反射巨集是 ON_NOTIFY_REFLECT。

- ON_UPDATE_COMMAND_UI 反射巨集是 ON_UPDATE_COMMAND_UI_REFLECT。

在每個上述的特殊情況下，您必須指定處理常式成員函式的名稱。 在其他情況下，您必須使用您的處理常式函式的標準名稱。

參數的意義和函式的傳回值記載於函式名稱] 或 [函式名稱之下*上*前面加上。 比方說，`CtlColor`記載於`OnCtlColor`。 幾個反映的訊息處理常式需要較少的參數，比在父視窗中類似的處理常式。 只要符合下表中的文件中的型式參數名稱的名稱。

|對應項目|函式原型|
|---------------|------------------------|
|**ON_CONTROL_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( );**|
|**ON_NOTIFY_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT(** `memberFxn` **)**|**afx_msg void** `memberFxn` **( CCmdUI**<strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT( )**|**afx_msg HBRUSH CtlColor ( CDC**<strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT( )**|**afx_msg void DrawItem ( LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT( )**|**afx_msg void MeasureItem ( LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT( )**|**afx_msg void DeleteItem ( LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT( )**|**afx_msg int CompareItem ( LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT( )**|**afx_msg int CharToItem ( UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT( )**|**afx_msg int VKeyToItem ( UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT( )**|**afx_msg void HScroll ( UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT( )**|**afx_msg void VScroll ( UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT( )**|**afx_msg void ParentNotify ( UINT** `message` **, LPARAM** `lParam` **);**|

ON_NOTIFY_REFLECT 和 ON_CONTROL_REFLECT 巨集必須以處理特定的訊息允許多個物件 （例如控制項和其父系） 的變化。

|對應項目|函式原型|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_CONTROL_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( );**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>處理反映訊息：可重複使用的控制項範例

這個簡單的範例會建立可重複使用的控制項稱為`CYellowEdit`。 控制項運作方式與一般的編輯控制項相同，不同之處在於它會顯示黃色背景的黑色文字。 它可以輕鬆地加入允許的成員函式`CYellowEdit`控制項來顯示不同的色彩。

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>若要嘗試建立可重複使用的控制項範例

1. 在現有的應用程式中建立新的對話方塊。 如需詳細資訊，請參閱 <<c0> [ 對話方塊編輯器](../windows/dialog-editor.md)主題。

   您必須擁有用來開發可重複使用的控制項中的應用程式。 如果您沒有要使用現有的應用程式，建立使用 AppWizard 的對話方塊架構應用程式。

2. 與您的專案載入到視覺效果C++，用以建立新的類別，稱為 ClassWizard`CYellowEdit`根據`CEdit`。

3. 將三個成員變數加入您`CYellowEdit`類別。 前兩個都*COLORREF*變數來保存的文字色彩和背景色彩。 第三個會`CBrush`物件會包含對於繪製背景的筆刷。 `CBrush`物件可讓您建立一次，只是在那之後，參考它的筆刷，以及當自動終結筆刷`CYellowEdit`控制項被終結。

4. 初始化成員變數，如下所示撰寫建構函式：

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. 使用 ClassWizard，加入反映 WM_CTLCOLOR 訊息處理常式您`CYellowEdit`類別。 請注意，等號，您可以處理的訊息清單中的訊息名稱前面會指出訊息反映。 這中所述[定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。

   ClassWizard 會為您加入下列的訊息對應巨集和基本架構函數：

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. 取代為下列程式碼中的函式的主體。 程式碼會指定的文字色彩、 文字背景色彩和其他控制項的背景色彩。

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. 在您的對話方塊中，建立一個編輯控制項，然後將它附加至成員變數中，按住 control 鍵按兩下編輯控制項。 在 [加入成員變數] 對話方塊中，完成的變數名稱，然後選擇 「 控制項 」 分類中，然後 「 CYellowEdit"變數的類型。 別忘了在對話方塊中設定定位順序。 此外，務必要包含的標頭檔`CYellowEdit`對話方塊的標頭檔中的控制項。

8. 建置並執行您的應用程式。 編輯控制項將會有黃色背景。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
