---
title: "TN006：訊息對應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.messages.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息對應 [C++], Windows 訊息中心"
  - "ON_COMMAND 巨集"
  - "ON_COMMAND_EX 巨集"
  - "ON_COMMAND_RANGE 巨集"
  - "ON_COMMAND_RANGE_EX 巨集"
  - "ON_CONTROL 巨集"
  - "ON_CONTROL_RANGE 巨集"
  - "ON_MESSAGE 巨集"
  - "ON_NOTIFY 訊息"
  - "ON_NOTIFY_RANGE 巨集"
  - "ON_REGISTERED_MESSAGE 巨集"
  - "ON_UPDATE_COMMAND_UI 巨集"
  - "TN006"
  - "Windows 訊息 [C++], 訊息對應"
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# TN006：訊息對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個摘要說明 MFC 訊息對應機能。  
  
## 問題  
 Microsoft Windows 實作使用它的訊息作用的視窗類別的虛擬函式。  由於包含大量的訊息，為每個視窗訊息提供不同的虛擬函式將建立超過允許大小的 vtable。  
  
 由於系統定義的視窗訊息數目隨時間變更，和因為應用程式可以定義自己的視窗訊息，訊息對應提供防止破壞現有程式碼的介面變更的間接取值。  
  
## 概觀  
 MFC 提供用於傳統 Windows 程式處理傳送到視窗的替代 switch 陳述式。  從訊息到方法中定義的對應可被定義，如此一來，當訊息由視窗接收時，適當的方法自動呼叫。  這個訊息對應機能具有類似虛擬函式的設計，但有優點無法在 C\+\+ 虛擬函式實現。  
  
## 定義訊息對應  
 [DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md) 巨集來宣告類別的三個成員。  
  
-   `AFX_MSGMAP_ENTRY` 的私用陣列輸入呼叫 `_messageEntries`。  
  
-   受保護的 `AFX_MSGMAP` 結構呼叫指向 `_messageEntries` 陣列的 `messageMap` 。  
  
-   受保護虛擬函式呼叫傳回 `messageMap`位址的 `GetMessageMap` 。  
  
 此巨集應使用訊息對應置於任何類別的宣告。  依照慣例，它是在類別宣告的結尾。  例如：  
  
```  
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
  
 這是當它們建立新的類別時 AppWizard 和 ClassWizard 產生的格式。  \/\/{{ 和 \/\/}} 括弧為 ClassWizard 是必要的。  
  
 訊息對應的資料表使用擴展訊息對應項目的一組巨集來定義。  資料表開頭為 [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 巨集呼叫，這定義由這個訊息對應處理類別，且未處理的訊息傳遞至父類別。  於尾端使用 [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) 巨集呼叫結束資料表。  
  
 在這兩個巨集呼叫之間是這個訊息對應要管理的每個訊息中的項目。  每個標準 Windows 訊息有會產生該訊息的輸入表單的形式為 ON\_WM\_*MESSAGE\_NAME* 的巨集。  
  
 一個標準函式簽章為開啟每個視窗訊息參數和提供型別安全的定義。  這些簽章可能在 [CWnd](../mfc/reference/cwnd-class.md)宣告的檔案 Afxwin.h 中找到。  每一個標記為容易識別的關鍵字 `afx_msg` 。  
  
> [!NOTE]
>  ClassWizard 需要您在訊息對應的處理常式宣告中使用 `afx_msg` 關鍵字。  
  
 這些函式使用簡單的慣例簽章衍生。  函式的名稱一定是以 `"On`開頭。  這個接著 Windows 訊息與移除「WM\_」和大寫的每個字的第一個字母。  參數的順序是 `LOWORD` 接著 `wParam` \(`lParam`\) 和 `HIWORD`\(`lParam`\)。  未使用的參數沒有傳遞。  由 MFC 類別包裝的所有控制代碼轉換為適當的 MFC 物件的指標。  下列範例顯示如何處理 `WM_PAINT` 訊息和造成 `CMyWnd::OnPaint` 函式呼叫:  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    //{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT()  
    //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 訊息對應表必須定義在任何函式或類別定義的範圍之外。  不應該將它置於外部「C」區塊。  
  
> [!NOTE]
>  ClassWizard 會修改發生在\/\/和{{\/\/}}註解方括弧中的訊息對應項目。  
  
## 使用者定義的 Windows 訊息。  
 使用 [ON\_MESSAGE](../Topic/ON_MESSAGE.md) 巨集，使用者定義的訊息可能包括在對應。  這個巨集接受訊息號碼和方法的形式:  
  
```  
    // inside the class declaration  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);  
  
    #define WM_MYMESSAGE (WM_USER + 100)  
  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 在此範例中，我們為使用者定義的訊息建立從 `WM_USER` 基底衍生的Windows 訊息 ID 的自訂訊息的處理常式。  下列範例將示範如何呼叫這個處理常式。  
  
```  
CWnd* pWnd = ...;  
pWnd->SendMessage(WM_MYMESSAGE);  
```  
  
 使用這種方法的使用者定義訊息的範圍必須介於 `WM_USER` 到 0x7fff。  
  
> [!NOTE]
>  ClassWizard 不支援從 ClassWizard 使用者介面輸入 `ON_MESSAGE` 處理常式。  您必須從 Visual C\+\+ 編輯器手動輸入。  ClassWizard 會解析這些項目並讓您瀏覽它們如同其他訊息對應項目。  
  
## 已登錄視窗訊息。  
 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) 函式用來定義在整個系統中是唯一的新的 Windows 訊息。  巨集 `ON_REGISTERED_MESSAGE` 用來處理這些訊息。  這個巨集接受包含登錄的視窗訊息 ID 的 `UINT NEAR` 變數的名稱。  例如  
  
```  
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
  
 登錄的視窗訊息 ID 變數 \(在本例中的 WM\_FIND\) 必須是 `NEAR` 變數因為 `ON_REGISTERED_MESSAGE` 實作的方式。  
  
 使用這種方法的使用者定義訊息的範圍介於 0xC000 至 0xFFFF。  
  
> [!NOTE]
>  ClassWizard 不支援從 ClassWizard 使用者介面輸入 `ON_REGISTERED_MESSAGE` 處理常式。  您必須從文字編輯器手動輸入。  ClassWizard 會解析這些項目並讓您瀏覽它們如同其他訊息對應項目。  
  
## 命令訊息  
 從功能表和快速鍵的命令訊息在以 `ON_COMMAND` 巨集對應訊息中處理。  這個巨集接受命令 ID 和方法。  只有具有與指定的命令 ID 相同的 `wParam` 特定 `WM_COMMAND` 訊息會在訊息對應項目指定的方法中處理。  命令處理常式成員函式沒有參數並傳回 `void`。  巨集的格式如下:  
  
```  
ON_COMMAND(id, memberFxn)  
```  
  
 命令更新訊息由相同機制傳遞，不過，使用 `ON_UPDATE_COMMAND_UI` 巨集。  更新命令處理常式成員函式採用單一參數、指向 [CCmdUI](../mfc/reference/ccmdui-class.md) 物件並傳回 `void`。  巨集有形式  
  
```  
ON_UPDATE_COMMAND_UI(id, memberFxn)  
```  
  
 進階使用者可以使用 `ON_COMMAND_EX` 巨集，是命令訊息訊息處理常式擴充格式。  巨集提供 `ON_COMMAND` 功能的超集。  延伸的命令處理常式成員函式採用單一參數，包含命令 ID 的 `UINT`，並傳回 `BOOL`。  傳回值應該是 `TRUE` 以表示命令已被處置。  不然傳遞會繼續執行其他命令目標物件。  
  
 這些形式的範例：  
  
-   Resource.h 內部 \(通常由 Visual C\+\+ 產生\)  
  
    ```  
    #define    ID_MYCMD      100  
    #define    ID_COMPLEX    101  
    ```  
  
-   在類別宣告中。  
  
    ```  
    afx_msg void OnMyCommand();  
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);  
    afx_msg BOOL OnComplexCommand(UINT nID);  
    ```  
  
-   在訊息對應的定義中  
  
    ```  
    ON_COMMAND(ID_MYCMD, OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)  
    ```  
  
-   在實作檔案  
  
    ```  
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
  
 進階使用者可以使用單一命令處理常式處理命令的範圍: [ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md) 或 `ON_COMMAND_RANGE_EX`。  參考產品文件以取得這些巨集的詳細資訊。  
  
> [!NOTE]
>  ClassWizard 支援建立 `ON_COMMAND` 和 `ON_UPDATE_COMMAND_UI` 處理常式，不過，它不支援建立 `ON_COMMAND_EX` 或 `ON_COMMAND_RANGE` 處理常式。  不過，類別精靈會剖析並可讓您瀏覽全部四個命令處理常式變體。  
  
## 控制項通知訊息  
 從子控制項傳送到視窗的相關額外資訊位元在他們的訊息對應項目:控制項的 ID。  只有在下列條件成立時，在訊息對應項目指定的訊息處理常式會被呼叫:  
  
-   控制項通知程式碼 \( `lParam` 的高位\)，例如 BN\_CLICKED，符合訊息對應項目指定的通知程式碼。  
  
-   控制項 ID \(`wParam`\) 符合訊息對應項目指定的控制項 ID。  
  
 自訂控制項通知訊息可以使用 [ON\_CONTROL](../Topic/ON_CONTROL.md) 巨集定義自訂通知程式碼的訊息對應項目。  這個巨集有形式  
  
```  
ON_CONTROL(wNotificationCode, id, memberFxn)  
```  
  
 針對進階使用 [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md) 可用來從控制項之範圍以一樣的處理常式處理特定控制項通知。  
  
> [!NOTE]
>  ClassWizard 不支援建立使用者介面的 `ON_CONTROL` 或 `ON_CONTROL_RANGE` 處理常式。  您必須以文字編輯器手動輸入。  ClassWizard 會解析這些項目並讓您瀏覽它們如同其他訊息對應項目。  
  
 Windows 通用控制項為複雜控制項告知使用更強大的 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)。  使用 `ON_NOTIFY` 和 `ON_NOTIFY_RANGE` 巨集， MFC 這個版本的直接支援這個新的訊息。  參考產品文件以取得這些巨集的詳細資訊。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)