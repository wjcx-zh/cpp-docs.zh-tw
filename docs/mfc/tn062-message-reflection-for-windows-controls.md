---
title: "TN062：Windows 控制項的訊息反映 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息反映"
  - "通知訊息"
  - "ON_CONTROL_REFLECT 巨集"
  - "ON_CONTROL_REFLECT_EX 巨集"
  - "ON_NOTIFY 訊息"
  - "ON_NOTIFY_REFLECT 訊息"
  - "ON_NOTIFY_REFLECT_EX 訊息"
  - "ON_UPDATE_COMMAND_UI_REFLECT 巨集"
  - "ON_WM_CHARTOITEM_REFLECT 巨集"
  - "ON_WM_COMPAREITEM_REFLECT 巨集"
  - "ON_WM_CTLCOLOR_REFLECT 巨集"
  - "ON_WM_DELETEITEM_REFLECT 巨集"
  - "ON_WM_DRAWITEM_REFLECT 巨集"
  - "ON_WM_HSCROLL_REFLECT 巨集"
  - "ON_WM_MEASUREITEM_REFLECT 巨集"
  - "ON_WM_PARENTNOTIFY_REFLECT 巨集"
  - "ON_WM_VKEYTOITEM_REFLECT 巨集"
  - "ON_WM_VSCROLL_REFLECT 巨集"
  - "TN062"
  - "WM_COMMAND"
  - "WM_CTLCOLOR 訊息"
  - "WM_NOTIFY 訊息"
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN062：Windows 控制項的訊息反映
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示描述訊息反映，為 MFC 4.0 的新功能。  它也包含用於建立使用訊息反映的簡單的可重複使用的控制項。  
  
 這個技術提示不討論訊息反映，當它適用於 ActiveX 控制項 \(先前稱為 OLE automation 控制項\)。  請參閱本文件的 [ActiveX 控制項:的子類別化視窗控制項](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
 **您的訊息反映是什麼？**  
  
 視窗控制項經常傳送通知訊息至其父視窗。  例如，許多控制項傳送控制色彩告知訊息 \(其變數`WM_CTLCOLOR` 或其中一個\) 至其父允許父提供繪製控制項背景的筆刷。  
  
 在視窗以及 4.0 版之前的 MFC，父視窗，通常對話方塊中，巡覽至處理這些訊息負責。  這表示訊息需要父視窗類別的處理的程式碼，並在需要處理該訊息的每個類別必須重複。  以上述情況，每個對話方塊與自訂控制項所要的控制項必須處理控制項的通知訊息。  重複使用程式碼更容易，如果處理其背景色彩的控制項類別可能會覆寫。  
  
 在 MFC 4.0 中，舊機制仍—父視窗可以處理通知訊息。  此外，然而， MFC 4.0 提升重複使用藉由提供稱為在子控制項視窗或父視窗允許這些通知訊息被處理的訊息反映的功能，或是在兩個。  在控制項背景色彩範例中，您現在可以撰寫的處理反映的 `WM_CTLCOLOR` 訊息將其背景色彩—全部不依賴父控制項的類別。\(請注意，因為訊息反映由 MFC 實作，而不是由視窗，必須從已反映訊息的 `CWnd` 取得運作之父視窗類別  
  
 MFC 舊版所做的事類似訊息反映藉由提供虛擬函式為一些訊息，例如主控描繪清單方塊 \(`WM_DRAWITEM`訊息，依此類推\)。  新的訊息反映機制是推斷和一致。  
  
 訊息反映與為 MFC 版本撰寫的程式碼回溯相容於 4.0 之前。  
  
 如果您提供了處理常式特定訊息的，或訊息的範圍中，在您的父視窗的類別，它將覆寫相同訊息的反映訊息處理常式提供了您不呼叫您的處理常式的基底類別處理函式。  例如，在中，如果您在您的對話方塊類別的 `WM_CTLCOLOR` ，處理常式會覆寫任何反映訊息處理常式。  
  
 如果，在父視窗類別，可以提供特定 **WM\_NOTIFY** 訊息或 **WM\_NOTIFY** 訊息範圍的處理常式，處理常式會呼叫時，才會傳送這些訊息的子控制項並透過 **ON\_NOTIFY\_REFLECT\(\)**具有反映訊息處理常式。  如果您在訊息對應使用 **ON\_NOTIFY\_REFLECT\_EX\(\)** ，您的訊息處理常式不一定可讓父視窗處理訊息。  如果處理常式傳回 **FALSE**，訊息會受父管理，，而傳回 **TRUE** 的呼叫不允許父處理它。  請注意反映訊息告知訊息之前被處理。  
  
 當 **WM\_NOTIFY** 傳送訊息時，提供控制項第一個有機會處理它。  如果其他反映訊息已傳送，父視窗是第一個有機會處理它，而且控制項會反映訊息。  為了計算長度，它在控制項的類別訊息對應需要處理函式和適當的項目。  
  
 反映訊息的訊息對應巨集為規則通知有些不同:它有 **\_REFLECT** 附加至它的一般名稱。  例如，若要處理在父代的 **WM\_NOTIFY** 訊息，您在父的訊息對應使用巨集 `ON_NOTIFY` 。  若要處理在子控制項的反映訊息，請使用 **ON\_NOTIFY\_REFLECT** 巨集在子控制項的訊息對應。  在某些情況下，參數不同，。  請注意 ClassWizard 通常可以增加您的訊息對應項目和提供最基本的函式實作以正確的參數。  
  
 如需新 **WM\_NOTIFY** 訊息的詳細資訊，請參閱 [TN061:ON\_NOTIFY 和 WM\_NOTIFY 訊息](../mfc/tn061-on-notify-and-wm-notify-messages.md) 。  
  
 **訊息對應項目和處理函式原型反映訊息的**  
  
 若要處理反映的控制項告知訊息，使用訊息對應巨集和函式原型下表中列出。  
  
 ClassWizard 通常可以將這些訊息對應項目和提供最基本的函式實作。  如需如何定義反映訊息的處理常式，請參閱 [定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) 。  
  
 從訊息名稱要轉換成反映的巨集名稱，請在前面加上 **ON\_** 和 **\_REFLECT**附加。  例如， `WM_CTLCOLOR` 會變成 **ON\_WM\_CTLCOLOR\_REFLECT**。\(看哪些訊息可以反映，請使用巨集輸入的反向轉換在下表中\)。  
  
 對上述規則的三個例外狀況如下:  
  
-   **WM\_COMMAND** 通知的巨集是 **ON\_CONTROL\_REFLECT**。  
  
-   **WM\_NOTIFY** 反映的巨集是 **ON\_NOTIFY\_REFLECT**。  
  
-   `ON_UPDATE_COMMAND_UI` 反映的巨集是 **ON\_UPDATE\_COMMAND\_UI\_REFLECT**。  
  
 在每一個以上的特殊狀況，您必須指定處理常式的成員函式名稱。  在其他情況下，您必須針對處理函式使用標準名稱。  
  
 函式的參數和傳回值的意義記錄在或函式名稱下或與 **On** 的函式名稱加在前面。  例如，在 **CtlColor** `OnCtlColor`文件。  數個反映訊息處理常式在父視窗比相似的處理常式需要較少的參數。  請相符名稱在下表中的型式參數名稱在文件中。  
  
|對應項目|函式原型|  
|----------|----------|  
|**ON\_CONTROL\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg void**  `memberFxn`  **\( \);**|  
|**ON\_NOTIFY\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg void**  `memberFxn`  **\( NMHDR \***  `pNotifyStruct` **, LRESULT\***  *result*  **\);**|  
|**ON\_UPDATE\_COMMAND\_UI\_REFLECT\(**  `memberFxn`  **\)**|**afx\_msg void**  `memberFxn`  **\( CCmdUI\***  `pCmdUI`  **\);**|  
|**ON\_WM\_CTLCOLOR\_REFLECT \(\)**|**afx\_msg HBRUSH CtlColor \( CDC\***  `pDC` **, UINT**  `nCtlColor`  **\);**|  
|**ON\_WM\_DRAWITEM\_REFLECT \(\)**|**afx\_msg void DrawItem \( LPDRAWITEMSTRUCT**  `lpDrawItemStruct`  **\);**|  
|**ON\_WM\_MEASUREITEM\_REFLECT\( \)**|**afx\_msg void MeasureItem \( LPMEASUREITEMSTRUCT**  `lpMeasureItemStruct`  **\);**|  
|**ON\_WM\_DELETEITEM\_REFLECT\( \)**|**afx\_msg void DeleteItem \( LPDELETEITEMSTRUCT**  `lpDeleteItemStruct`  **\);**|  
|**ON\_WM\_COMPAREITEM\_REFLECT\( \)**|**afx\_msg int CompareItem \( LPCOMPAREITEMSTRUCT**  `lpCompareItemStruct`  **\);**|  
|**ON\_WM\_CHARTOITEM\_REFLECT\( \)**|**afx\_msg int CharToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_VKEYTOITEM\_REFLECT\( \)**|**afx\_msg int VKeyToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_HSCROLL\_REFLECT\( \)**|**afx\_msg void HScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_VSCROLL\_REFLECT\( \)**|**afx\_msg void VScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_PARENTNOTIFY\_REFLECT\( \)**|**afx\_msg void ParentNotify \( UINT**  `message` **, LPARAM**  `lParam`  **\);**|  
  
 **ON\_NOTIFY\_REFLECT** 和 **ON\_CONTROL\_REFLECT** 巨集不允許多個物件的變數 \(例如控制項和其父代\) 處理給定的訊息。  
  
|對應項目|函式原型|  
|----------|----------|  
|**ON\_NOTIFY\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg BOOL**  `memberFxn`  **\( NMHDR \***  `pNotifyStruct` **, LRESULT\***  *result*  **\);**|  
|**ON\_CONTROL\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg BOOL**  `memberFxn`  **\( \);**|  
  
## 處理反映訊息:可重複使用的控制項範例  
 這個簡單範例建立名為 `CYellowEdit`的可重複使用的控制項。  控制項運作方式與一般編輯控制項相同，但是它會以黃色背景上文字。  加入可讓 `CYellowEdit` 控制項中顯示不同的色彩的成員函式非常容易。  
  
#### 嘗試建立可重複使用的控制項範例  
  
1.  若要在現有的應用程式建立新的對話方塊。  如需詳細資訊，請參閱 [對話框編輯器](../mfc/dialog-editor.md) 主題。  
  
     您必須具有開發可重複使用的控制項的應用程式。  如果您不需要使用一個現有的應用程式，使用 AppWizard，建立對話方塊架構的應用程式。  
  
2.  在您的專案載入 Visual C\+\+，請使用 ClassWizard 會根據 `CEdit`傳回 `CYellowEdit` 的新類別。  
  
3.  將三 \+ 成成員變數加入至 `CYellowEdit` 類別。  前兩個會保留文字色彩和背景色彩的 **COLORREF** 變數。  將三個是將物件所繪製的背景筆刷的 `CBrush` 物件。  在終結時， `CBrush` 物件可讓您一次建立筆刷，只是參考它之後和自動終結這個筆刷用於在 `CYellowEdit` 控制項。  
  
4.  藉由撰寫建構函式初始化成員變數:  
  
    ```  
    CYellowEdit::CYellowEdit()  
    {  
       m_clrText = RGB( 0, 0, 0 );  
       m_clrBkgnd = RGB( 255, 255, 0 );  
       m_brBkgnd.CreateSolidBrush( m_clrBkgnd );  
    }  
    ```  
  
5.  使用 ClassWizard，加入反射的 `WM_CTLCOLOR` 訊息的處理常式加入至 `CYellowEdit` 類別。  請注意在訊息名稱前面的等號在訊息清單可以處理指示訊息反映。  這會在 [定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)中說明。  
  
     ClassWizard 加入下列訊息對應巨集和最基本的函式中:  
  
    ```  
    ON_WM_CTLCOLOR_REFLECT()  
  
    // Note: other code will be in between....  
  
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
    {  
       // TODO: Change any attributes of the DC here  
  
       // TODO: Return a non-NULL brush if the  
       //   parent's handler should not be called  
       return NULL;  
    }  
    ```  
  
6.  以下面程式碼取代函式中的程式碼：  程式碼為控制項的其餘部分指定文字色彩、文字背景色彩和背景色彩。  
  
    ```  
    pDC->SetTextColor( m_clrText );   // text  
    pDC->SetBkColor( m_clrBkgnd );   // text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
    ```  
  
7.  建立在對話方塊中的編輯控制項，然後將它附加至成員變數以按兩下編輯控制項時，使控制項向下鍵時。  在加入成員變數的對話方塊，請完成這個變數名稱並選取了控制項」類別的「，然後 CYellowEdit」變數的型別。  不要忘記設定對話方塊中的定位順序。  因此，請務必包含 `CYellowEdit` 控制項的標頭檔在對話方塊的標頭檔。  
  
8.  建置並執行您的應用程式。  編輯控制項將會以黃色背景。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)