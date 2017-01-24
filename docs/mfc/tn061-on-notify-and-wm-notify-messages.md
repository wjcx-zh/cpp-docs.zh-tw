---
title: "TN061：ON_NOTIFY 和 WM_NOTIFY 訊息 | Microsoft Docs"
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
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通知訊息"
  - "ON_NOTIFY 訊息"
  - "ON_NOTIFY_EX 訊息"
  - "ON_NOTIFY_EX_RANGE 訊息"
  - "ON_NOTIFY_RANGE 訊息"
  - "TN061"
  - "WM_NOTIFY 訊息"
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN061：ON_NOTIFY 和 WM_NOTIFY 訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示在新 **WM\_NOTIFY** 訊息在 MFC 應用程式提供背景資訊和描述處理 **WM\_NOTIFY** 訊息建議的 \(和最常見的方式\)。  
  
 **在 Windows 3.x 的通知訊息**  
  
 在 Windows 3.x，控制項會透過傳送訊息通知事件其父代 \(例如滑鼠點選、變更在內容上和選取和控制項背景繪製至父代。  簡單的通知傳送為特殊 **WM\_COMMAND** 訊息，以通知程式碼 \(例如 **BN\_CLICKED**\) 和控制項 ID 封裝至 `wParam` 以及 `lParam`中的控制項。  請注意從 `wParam` 和 `lParam` 都是完整的，因此無法透過任何其他資料—這些訊息可以只是簡單的通知。  例如，在 **BN\_CLICKED** 通知，無法傳送有關滑鼠資料指標位置的相關資訊，以及按下按鈕。  
  
 在 Windows 3.x 的控制項需要傳送包含其他資料的通知訊息時，會使用各種私用訊息，包括 `WM_CTLCOLOR`， `WM_VSCROLL`， `WM_HSCROLL`， `WM_DRAWITEM`， `WM_MEASUREITEM`， `WM_COMPAREITEM`， `WM_DELETEITEM`， `WM_CHARTOITEM`， `WM_VKEYTOITEM`，依此類推。  這些訊息可以反映回其告知的控制項。  如需詳細資訊，請參閱 [TN062:視窗的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)。  
  
 **在 Win32 的通知訊息**  
  
 若要在 Windows 3.1 中，控制項的大部分 Win32 API 使用用於 Windows 3.x. 通知訊息。  不過， Win32 也將多個複雜，複雜控制項加入至 Windows 支援的那些 3.x。  通常，這些控制項需要傳送與其告知訊息的其他資訊。  而不是將需要額外資料的每個新的通知的新 **WM\_\*** 訊息， Win32 API 中的設計工具選取加入訊息， **WM\_NOTIFY**，可以將任何數目的其他資料的標準化方式。  
  
 **WM\_NOTIFY** 訊息包含在 `wParam` 傳送訊息和指標的控制項 ID 為結構所在 `lParam`。  這個結構是 **NMHDR** 結構或具有 **NMHDR** 結構做為它的第一個成員的一些更大的結構。  請注意，因為 **NMHDR** 成員的呼叫，此結構的指標可以用來做為 **NMHDR** 的指標或做為較大的結構指標視您如何將它轉換成。  
  
 在大部分情況下，指標會指向較大的結構，而且您將必須轉換為，當您使用它。  在少數通知，例如通用名稱開頭為 **NM\_**\) 的告知 \(和工具提示控制項 **TTN\_SHOW** 和 **TTN\_POP** 通知，就是實際使用的 **NMHDR** 結構。  
  
 這個 **NMHDR** 結構或最初成員包含傳送訊息和通知程式碼之控制項的控制代碼和 ID \(例如 **TTN\_SHOW**\)。  **NMHDR** 結構的格式如下所示：  
  
```  
typedef struct tagNMHDR {  
    HWND hwndFrom;  
    UINT idFrom;  
    UINT code;  
} NMHDR;  
```  
  
 對於 **TTN\_SHOW** 訊息， **code** 成員會設為 **TTN\_SHOW**。  
  
 大部分通知傳遞指標包含 **NMHDR** 結構做為它的第一個成員的較大的結構。  例如，請考慮結構使用清單檢視控制項 **LVN\_KEYDOWN** 通知訊息，傳送，元素為焦點且按下清單檢視控制項時。  對 **LV\_KEYDOWN** 結構的指標，定義如下所示：  
  
```  
typedef struct tagLV_KEYDOWN {  
    NMHDR hdr;     
    WORD wVKey;    
    UINT flags;    
} LV_KEYDOWN;  
```  
  
 請注意，因為 **NMHDR** 成員是第一個結構，您在通知訊息傳遞指標可轉換成對 **NMHDR** 的指標或對 **LV\_KEYDOWN**的指標。  
  
 **告知通用於所有新視窗控制項**  
  
 有些告知對所有通用的新視窗控制項。  這些通知傳遞指標 **NMHDR** 結構。  
  
|通知程式碼。|傳送，因為|  
|------------|-----------|  
|**NM\_CLICK**|使用者在控制項的按下滑鼠左鍵|  
|**NM\_DBLCLK**|使用者在控制項的按兩下滑鼠左鍵|  
|**NM\_RCLICK**|使用者在控制項的按下滑鼠右鍵|  
|**NM\_RDBLCLK**|使用者在控制項的按兩下滑鼠右鍵|  
|**NM\_RETURN**|當控制項擁有輸入焦點時，使用者按下 ENTER 鍵|  
|**NM\_SETFOCUS**|控制項已指定輸入焦點|  
|**NM\_KILLFOCUS**|控制項失去輸入焦點|  
|**NM\_OUTOFMEMORY**|因為沒有足夠的記憶體可用，則控制項無法完成作業。|  
  
##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON\_NOTIFY：在 MFC 應用程式中處理 WM\_NOTIFY 訊息  
 函式 `CWnd::OnNotify` 控制代碼通知訊息。  它的預設實作會檢查訊息對應通知處理常式呼叫。  一般而言，您不會覆寫 `OnNotify`。  相反地，您的處理常式函式並將該處理常式的訊息對應項目加入至主控視窗的類別訊息對應。  
  
 ClassWizard，透過 ClassWizard 屬性工作表，可以建立 `ON_NOTIFY` 訊息對應項目和提供您以基本架構處理常式函式。  如需使用 ClassWizard 的更多資訊讓這項工作更容易，請參閱 [out 此函式之對應訊息](../mfc/reference/mapping-messages-to-functions.md)。  
  
 `ON_NOTIFY` 訊息對應巨集具有下列語法：  
  
```  
  
ON_NOTIFY( wNotifyCode, id, memberFxn )  
```  
  
 其中斜體參數替換成：  
  
 `wNotifyCode`  
 通知訊息的程式碼要處理，例如 **LVN\_KEYDOWN**。  
  
 `id`  
 通知傳送子控制項的識別項。  
  
 `memberFxn`  
 當傳送通知，就會呼叫成員函式。  
  
 您的成員函式必須宣告下列原型：  
  
```  
  
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 備註  
 其中斜體參數：  
  
 `pNotifyStruct`  
 通知結構的指標，如前面章節所述。  
  
 *result*  
 對您要設定的結果程式碼的指標，在返回之前。  
  
## 範例  
 若要指定您想要成員函式 `OnKeydownList1` 處理來自 ID 為 `IDC_LIST1`之 `CListCtrl` 的 **LVN\_KEYDOWN** 訊息，您會使用 ClassWizard 加入下列程式碼加入訊息對應：  
  
```  
ON_NOTIFY( LVN_KEYDOWN, IDC_LIST1, OnKeydownList1 )  
```  
  
 在上面的範例中， ClassWizard 提供的功能如下：  
  
```  
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)  
{  
   LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;  
   // TODO: Add your control notification handler  
   //       code here  
  
   *pResult = 0;  
}  
```  
  
 請注意 ClassWizard 會自動提供適當型別的指標。  您可以透過 `pNMHDR` 或 `pLVKeyDow`存取通知結構。  
  
##  <a name="_mfcnotes_on_notify_range"></a> ON\_NOTIFY\_RANGE  
 如果您需要處理一組相同 **WM\_NOTIFY** 訊息控制，您可以使用 **ON\_NOTIFY\_RANGE** 而不是 `ON_NOTIFY`。  例如，您可能會想要執行某個通知訊息的相同動作的一組按鈕。  
  
 當您使用 **ON\_NOTIFY\_RANGE**時，您指定的子識別項的連續範圍可以指定範圍的開頭及結尾子識別項處理通知訊息。  
  
 ClassWizard 不處理 **ON\_NOTIFY\_RANGE**；若要使用它，您必須編輯您的訊息對應。  
  
 **ON\_NOTIFY\_RANGE** 的訊息對應項目和函式原型如下：  
  
```  
  
ON_NOTIFY_RANGE(   
wNotifyCode  
,   
id  
,   
idLast  
,   
memberFxn  
 )  
  
```  
  
 其中斜體參數替換成：  
  
 `wNotifyCode`  
 通知訊息的程式碼要處理，例如 **LVN\_KEYDOWN**。  
  
 `id`  
 在識別項的連續範圍的第一個識別項。  
  
 `idLast`  
 在識別項的連續範圍的最後一個識別項。  
  
 `memberFxn`  
 當傳送通知，就會呼叫成員函式。  
  
 您的成員函式必須宣告下列原型：  
  
```  
  
afx_msg void memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 備註  
 其中斜體參數：  
  
 `id`  
 傳送通知控制項子識別項。  
  
 `pNotifyStruct`  
 通知結構的指標，如上所述。  
  
 *result*  
 對您要設定的結果程式碼的指標，在返回之前。  
  
##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON\_NOTIFY\_EX， ON\_NOTIFY\_EX\_RANGE  
 如果您要多個通知路由的物件處理訊息，您可以使用 **ON\_NOTIFY\_EX** \( **ON\_NOTIFY\_EX\_RANGE**\) 而不是 `ON_NOTIFY` \( **ON\_NOTIFY\_RANGE**\)。  在 **EX** 版本和規則版本之間的唯一差異是 **EX** 版本呼叫成員函式傳回的 **BOOL** 表示訊息處理是否應繼續。  傳回從這個函式的 **FALSE** 允許您在多個物件的相同的訊息。  
  
 ClassWizard 不處理 **ON\_NOTIFY\_EX** 和 **ON\_NOTIFY\_EX\_RANGE**;如果您要使用之一，就需要編輯您的訊息對應。  
  
 **ON\_NOTIFY\_EX** 的訊息對應項目和函式原型和 **ON\_NOTIFY\_EX\_RANGE** 如下。  參數的意義與相同非**EX** 版本的。  
  
```  
  
ON_NOTIFY_EX( nCode, id, memberFxn ) ON_NOTIFY_EX_RANGE( wNotifyCode, id, idLast, memberFxn )  
```  
  
 兩個的原型上是相同的：  
  
```  
  
afx_msg BOOL memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 備註  
 在這兩種情況下， `id` 物件所傳送通知控制項子識別項。  
  
 您的函式必須傳回 **TRUE** ，如果通知訊息已完全處理或 **FALSE** ，如果在命令路由的其他物件應該有機會處理訊息。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)