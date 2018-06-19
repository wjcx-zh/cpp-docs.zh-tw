---
title: TN006： 訊息對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 160b88a7069ac9a5851c0f472f756d694e59874e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384693"
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
  
-   私用陣列的`AFX_MSGMAP_ENTRY`項目稱為`_messageEntries`。  
  
-   受保護`AFX_MSGMAP`結構稱為`messageMap`，它會指向`_messageEntries`陣列。  
  
-   受保護的虛擬函式，呼叫`GetMessageMap`所傳回的位址`messageMap`。  
  
 這個巨集都應該放在使用訊息對應任何類別的宣告。 依照慣例，它是在類別宣告的結尾。 例如:   
  
```  
class CMyWnd : public CMyParentWndClass  
{ *// my stuff...  
 
protected: *//{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();
*//}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
```  
  
 這是在建立新的類別時，AppWizard 及 ClassWizard 所產生的格式。 / / {{，/ /}} ClassWizard 需要方括號。  
  
 使用一組訊息對應項目展開的巨集已定義的訊息對應的資料表。 表格最開始先[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)巨集呼叫，定義處理此訊息對應的類別和未處理的訊息傳遞到父類別。 在資料表結尾[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)巨集呼叫。  
  
 這些兩個巨集呼叫會針對每個訊息來處理此訊息對應項目。 每個標準 Windows 訊息有巨集的表單 ON_WM_*MESSAGE_NAME*產生該訊息的項目。  
  
 已定義的標準函式簽章來解除封裝的每個 Windows 訊息的參數及提供類型安全。 這些簽章可能會找到檔 Afxwin.h 中宣告的[CWnd](../mfc/reference/cwnd-class.md)。 關鍵字會標示每個`afx_msg`為了易於識別。  
  
> [!NOTE]
>  ClassWizard 會要求您使用`afx_msg`您訊息對應處理常式宣告中的關鍵字。  
  
 使用簡單的慣例所衍生這些函式簽章。 函式的名稱永遠會以啟動`"On`"。 這被後面接著"WM_"移除與 Windows 訊息的名稱和每個字大寫的第一個字母。 參數的順序是`wParam`後面`LOWORD`(`lParam`) 然後`HIWORD`(`lParam`)。 未使用的參數不會傳遞。 任何 MFC 類別所包裝的控制代碼會轉換成適當的 MFC 物件的指標。 下列範例示範如何處理`WM_PAINT`傳送訊息以及造成`CMyWnd::OnPaint`呼叫函式：  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT() *//}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 訊息對應表格必須定義範圍以外的任何函式或類別定義。 不應在 extern"C"區塊中。  
  
> [!NOTE]
>  ClassWizard 會修改訊息對應項目之間發生的 / / {{，/ /}} 註解括號。  
  
## <a name="user-defined-windows-messages"></a>使用者定義的 Windows 訊息  
 使用者定義的訊息可能會包含在訊息對應使用[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)巨集。 這個巨集接受訊息編號和形式的方法：  
  
'' * / / 類別宣告中  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

 
 #<a name="define-wmmymessage-wmuser--100"></a>定義 WM_MYMESSAGE (WM_USER + 100)  
 
BEGIN_MESSAGE_MAP （CMyWnd、 CMyParentWndClass）  
    ON_MESSAGE （WM_MYMESSAGE、 OnMyMessage）  
END_MESSAGE_MAP()  
```  
  
 In this example, we establish a handler for a custom message that has a Windows message ID derived from the standard `WM_USER` base for user-defined messages. The following example shows how to call this handler:  
  
```  
CWnd * pWnd =...;  
pWnd]-> [SendMessage(WM_MYMESSAGE);
```  
  
 The range of user-defined messages that use this approach must be in the range `WM_USER` to 0x7fff.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the Visual C++ editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Registered Windows Messages  
 The [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) function is used to define a new window message that is guaranteed to be unique throughout the system. The macro `ON_REGISTERED_MESSAGE` is used to handle these messages. This macro accepts a name of a `UINT NEAR` variable that contains the registered windows message ID. For example  
  
```  
類別 CMyWnd： 公用 CMyParentWndClass  
{  
public:  
    CMyWnd();

 *//{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);* //}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
 
靜態 UINT 附近 WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

 
BEGIN_MESSAGE_MAP （CMyWnd、 CMyParentWndClass） *//{{AFX_MSG_MAP(CMyWnd)  
    ON_REGISTERED_MESSAGE （WM_FIND、 OnFind） * //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 The registered Windows message ID variable (WM_FIND in this example) must be a `NEAR` variable because of the way `ON_REGISTERED_MESSAGE` is implemented.  
  
 The range of user-defined messages that use this approach will be in the range 0xC000 to 0xFFFF.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_REGISTERED_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the text editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Command Messages  
 Command messages from menus and accelerators are handled in message maps with the `ON_COMMAND` macro. This macro accepts a command ID and a method. Only the specific `WM_COMMAND` message that has a `wParam` equal to the specified command ID is handled by the method specified in the message-map entry. Command handler member functions take no parameters and return `void`. The macro has the following form:  
  
```  
ON_COMMAND （識別碼、 memberFxn）  
```  
  
 Command update messages are routed through the same mechanism, but use the `ON_UPDATE_COMMAND_UI` macro instead. Command update handler member functions take a single parameter, a pointer to a [CCmdUI](../mfc/reference/ccmdui-class.md) object, and return `void`. The macro has the form  
  
```  
ON_UPDATE_COMMAND_UI （識別碼、 memberFxn）  
```  
  
 Advanced users can use the `ON_COMMAND_EX` macro, which is an extended form of command message handlers. The macro provides a superset of the `ON_COMMAND` functionality. Extended command-handler member functions take a single parameter, a `UINT` that contains the command ID, and return a `BOOL`. The return value should be `TRUE` to indicate that the command has been handled. Otherwise routing will continue to other command target objects.  
  
 Examples of these forms:  
  
-   Inside Resource.h (usually generated by Visual C++)  
  
 ```  
 #<a name="define----idmycmd------100"></a>定義 ID_MYCMD 100  
 #<a name="define----idcomplex----101"></a>定義 ID_COMPLEX 101  
 ```  
  
-   Inside the class declaration  
  
 ```  
    afx_msg void OnMyCommand();
afx_msg void OnUpdateMyCommand (CCmdUI * pCmdUI);

    afx_msg BOOL OnComplexCommand(UINT nID);

 ```  
  
-   Inside the message map definition  
  
 ```  
    ON_COMMAND(ID_MYCMD,
    OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD,
    OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD,
    OnComplexCommand)  
 ```  
  
-   In the implementation file  
  
 ```  
    void CMyClass::OnMyCommand()  
 {* / / 處理命令  
 }  
 
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
 {* / 設定與 pCmdUI 的 UI 狀態  
 }  
 
    BOOL CMyClass::OnComplexCommand(UINT nID)  
 {* / / 處理命令  
    傳回 TRUE;  
 }  
 ```  
  
 Advanced users can handle a range of commands by using a single command handler: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) or `ON_COMMAND_RANGE_EX`. See the product documentation for more information about these macros.  
  
> [!NOTE]
>  ClassWizard supports creating `ON_COMMAND` and `ON_UPDATE_COMMAND_UI` handlers, but it does not support creating `ON_COMMAND_EX` or `ON_COMMAND_RANGE` handlers. However, Class Wizard will parse and let you browse all four command handler variants.  
  
## Control Notification Messages  
 Messages that are sent from child controls to a window have an extra bit of information in their message map entry: the control's ID. The message handler specified in a message map entry is called only if the following conditions are true:  
  
-   The control notification code (high word of `lParam`), such as BN_CLICKED, matches the notification code specified in the message-map entry.  
  
-   The control ID (`wParam`) matches the control ID specified in the message-map entry.  
  
 Custom control notification messages may use the [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro to define a message map entry with a custom notification code. This macro has the form  
  
```  
ON_CONTROL （wNotificationCode、 識別碼、 memberFxn）  
```  
  
 For advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) can be used to handle a specific control notification from a range of controls with the same handler.  
  
> [!NOTE]
>  ClassWizard does not support creating an `ON_CONTROL` or `ON_CONTROL_RANGE` handler in the user interface. You must manually enter them with the text editor. ClassWizard will parse these entries and let you browse them just like any other message map entries.  
  
 The Windows Common Controls use the more powerful [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) for complex control notifications. This version of MFC has direct support for this new message by using the `ON_NOTIFY` and `ON_NOTIFY_RANGE` macros. See the product documentation for more information about these macros.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

