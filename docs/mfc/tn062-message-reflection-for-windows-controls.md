---
title: TN062： 訊息反映的 Windows 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0bcfdefa0ba15bb374c61e6a6eb61b13c6a784e
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122081"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062：Windows 控制項的訊息反映

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

這個技術提示說明訊息反映，MFC 4.0 的新功能。 它也包含用來建立使用訊息反映簡單可重複使用控制項的方向。

這個技術提示將不會討論訊息反映套用於 ActiveX 控制項 （先前稱為 OLE 控制項）。 請參閱文章[ActiveX 控制項： 子類別化 Windows 控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

**何謂訊息反映**

Windows 控制項通常會傳送通知訊息至其父視窗。 比方說，許多控制項會傳送至其父代，以便提供繪製控制項的背景的筆刷父控制項色彩通知訊息 （WM_CTLCOLOR 或其中一個變化）。

在 Windows 和 MFC 4.0 版之前，父視窗，通常對話方塊中，負責處理這些訊息。 這表示，必須是父視窗的類別中處理訊息的程式碼，而且它具有需要處理該訊息的每個類別內的重複。 在上述情況中，每個想要使用自訂背景的控制項的對話方塊者必須處理控制項色彩通知訊息。 將能更輕鬆地重複使用程式碼，如果可寫入的控制項類別，會處理其本身的背景色彩。

在 MFC 4.0 中的舊機制仍能運作，父視窗可以處理通知訊息。 此外，不過，MFC 4.0 促進重複使用藉由提供一項稱為 「 訊息反映 」 功能，可讓在子控制項視窗、 父視窗，或同時處理這些通知訊息。 在控制項背景色彩範例中，您現在可以撰寫處理反映的 WM_CTLCOLOR 訊息，設定其本身的背景色彩的控制項類別，而不需依賴父代。 (請注意，由於訊息反映 mfc 實作時，不由 Windows 中，父視窗類別必須衍生自`CWnd`運作的訊息反映。)

舊版的 MFC 未類似訊息反映藉由提供一些訊息，例如訊息為主控描繪清單方塊 （WM_DRAWITEM，等等） 的虛擬函式。 新的訊息反映機制是通用且一致。

訊息反映與 4.0 之前的 MFC 版本撰寫的程式碼的回溯相容。

如果您提供為特定的訊息處理常式，或某個範圍的父視窗的類別中的訊息，則會覆寫反映相同訊息的訊息處理常式，提供您不要在您自己的處理常式中呼叫基底類別處理常式函式。 例如，如果您在對話方塊類別中處理 WM_CTLCOLOR，您的處理將會覆寫任何反映的訊息處理常式。

如果在父視窗類別中，您可以提供特定的 WM_NOTIFY 訊息或範圍的 WM_NOTIFY 訊息的處理常式，您的處理常式會傳送這些訊息的子控制項沒有透過反映的訊息處理常式時，才呼叫`ON_NOTIFY_REFLECT()`。 如果您使用`ON_NOTIFY_REFLECT_EX()`在訊息對應中，您的訊息處理常式可能會或可能不允許的父視窗，以處理訊息。 如果處理常式傳回**FALSE**，父系，所傳回的呼叫時處理訊息**TRUE**不允許要處理它的父系。 請注意，處理反映的訊息是之前的通知訊息。

WM_NOTIFY 訊息傳送時，控制項則提供給第一個有機會處理它。 如果其他反映的訊息傳送時，父視窗已處理的第一個機會，控制項將接收反映的訊息。 若要這樣做，它需要的處理常式函式和控制項的類別訊息對應中的適當項目。

反映訊息的訊息對應巨集是比一般通知稍有不同： 它有 *_REFLECT*附加至其一般名稱。 比方說，以處理 WM_NOTIFY 訊息父系中的，您會使用在父系的訊息對應中 ON_NOTIFY 巨集。 若要處理反映的訊息中的子控制項，請在子控制項的訊息對應中使用 ON_NOTIFY_REFLECT 巨集。 在某些情況下，參數是不同，以及。 請注意，ClassWizard 的通常是為您新增的訊息對應項目，提供基本架構函數實作，使用正確的參數。

請參閱[TN061: ON_NOTIFY 和 WM_NOTIFY 訊息](../mfc/tn061-on-notify-and-wm-notify-messages.md)新 WM_NOTIFY 訊息上的資訊。

**訊息對應項目 」 和 「 反映訊息的處理常式函式原型**

若要處理反映的控制項通知訊息，使用訊息對應巨集和函式原型如下表中列出。

ClassWizard 通常可以讓您將這些訊息對應項目，並提供基本架構的函式實作。 請參閱[定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)如需有關如何定義反映訊息的處理常式資訊。

若要將訊息名稱轉換為反映的巨集名稱，前面加上*ON_* 附加 *_REFLECT*。 例如，WM_CTLCOLOR 會變成 ON_WM_CTLCOLOR_REFLECT。 （若要查看可反映的訊息，執行相反的轉換，如下表中的巨集項目上）。

上述規則的三個例外狀況是，如下所示：

- WM_COMMAND 通知巨集是 ON_CONTROL_REFLECT。

- WM_NOTIFY 反射用巨集是 ON_NOTIFY_REFLECT。

- ON_UPDATE_COMMAND_UI 反射用巨集是 ON_UPDATE_COMMAND_UI_REFLECT。

在每一個上述的特殊情況下，您必須指定處理常式成員函式的名稱。 在其他情況下，您必須使用您的處理常式函式的標準名稱。

參數的意義和函式傳回的值記載於函式名稱或函數名稱與下*上*前面加上。 比方說，`CtlColor`記載於`OnCtlColor`。 數個反映的訊息處理常式需要較少的參數，比在父視窗中類似的處理常式。 只符合下表中的名稱，與文件中的型式參數的名稱。

|對應項目|函式原型|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg void** `memberFxn` **（);**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR \***  `pNotifyStruct` **，LRESULT\***  *結果* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI\***  `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT （)**|**afx_msg HBRUSH CtlColor (CDC\***  `pDC` **，UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT （)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT （)**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT （)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT （)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT （)**|**afx_msg int CharToItem (UINT** `nKey` **，UINT** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT （)**|**afx_msg int VKeyToItem (UINT** `nKey` **，UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT （)**|**afx_msg void HScroll (UINT** `nSBCode` **，UINT** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT （)**|**afx_msg void VScroll (UINT** `nSBCode` **，UINT** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT （)**|**afx_msg void ParentNotify (UINT** `message` **，它加入 LPARAM** `lParam` **);**|

ON_NOTIFY_REFLECT 和 ON_CONTROL_REFLECT 巨集有變化，以處理特定的訊息允許多個物件 （例如控制項和其父系）。

|對應項目|函式原型|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR \***  `pNotifyStruct` **，LRESULT\***  *結果* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **（);**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>處理反映訊息： 可重複使用的控制項的範例

這個簡單的範例會建立可重複使用的控制項稱為`CYellowEdit`。 控制項運作方式完全相同的一般編輯控制項之處在於它會顯示黃色背景的黑色文字。 它很容易就能加入成員函式，讓`CYellowEdit`控制項來顯示不同的色彩。

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>若要嘗試建立可重複使用的控制項範例

1. 在現有的應用程式中建立新的對話方塊。 如需詳細資訊，請參閱[對話方塊編輯器](../windows/dialog-editor.md)主題。

     您必須擁有要開發可重複使用控制項的應用程式。 如果您不需要使用現有的應用程式，建立使用 AppWizard 對話方塊架構應用程式。

2. 載入 Visual c + + 專案，使用建立新的類別稱為 ClassWizard`CYellowEdit`根據`CEdit`。

3. 將三個成員變數加入您`CYellowEdit`類別。 將前兩個*COLORREF*變數來保存的文字色彩和背景色彩。 將第三個`CBrush`物件會保留繪製背景的筆刷。 `CBrush`物件可讓您建立一次，只是在這之後，參考它的筆刷和時自動終結筆刷`CYellowEdit`終結控制項時。

4. 初始化成員變數撰寫建構函式，如下所示：

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. 使用 ClassWizard，加入要反映的 WM_CTLCOLOR 訊息的處理常式您`CYellowEdit`類別。 請注意訊息名稱，您可以處理的訊息清單中前面的等號表示所反映的訊息。 這中所述[定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。

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

6. 取代為下列程式碼中的函式主體。 程式碼會指定文字的色彩、 文字背景色彩和其他控制項的背景色彩。

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. 建立編輯控制項在對話方塊中，然後將它附加到成員變數中，按兩下按住 control 鍵的同時編輯控制項。 在 [加入成員變數] 對話方塊中，完成的變數名稱，然後選擇 「 控制項 」 的分類，然後 「 CYellowEdit"變數的型別。 別忘了在對話方塊中設定定位順序。 此外，務必要包含的標頭檔`CYellowEdit`對話方塊的標頭檔中的控制項。

8. 建置並執行您的應用程式。 編輯控制項將會有黃色背景。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
