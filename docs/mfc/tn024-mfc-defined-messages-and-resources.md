---
title: "TN024：MFC 定義的訊息和資源 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息 [C++], MFC"
  - "資源 [MFC]"
  - "TN024"
  - "Windows 訊息 [C++], MFC 定義的"
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN024：MFC 定義的訊息和資源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個附註說明 MFC 和資源格式使用的\) 內部視窗訊息。  這項資訊說明架構的實作和協助您偵錯的應用程式。  對風險，，即使這些資訊正式不受支援，您可以為進階實作使用這些資訊。  
  
 這個標記包含 MFC 私用實作詳細資料;所有內容在未來可能會變更。  MFC 私用視窗訊息只有意義之應用程式的範圍內，但在未來變更包含全系統訊息。  
  
 MFC 私用 Windows 訊息的範圍和資源型別在 Microsoft Windows 中剩下的保留「System」範圍。  目前不是在範圍中的數字，而且可能，未來使用，在這個範圍的新數目。  可能會變更目前使用的數字。  
  
 MFC 私用視窗訊息在範圍 0x360\-0x37F\>。  
  
 MFC 私用資源型別在範圍 0xF0\-0xFF\>。  
  
 **MFC 私用視窗訊息**  
  
 這些視窗訊息在相對鬆散結合需要在視窗物件之間的 C\+\+ 虛擬函式位置，並使用 C \+\+. 虛擬函式不會是適當的位置。  
  
 這些私用 Windows 訊息和相關參數結構在 MFC 私用標題「AFXPRIV.H」宣告。  請將警告任何程式碼包含這個標頭將 MFC 未來版本可能相依於未記載的行為，而且可能會中斷。  
  
 在極少數的必要之時處理這些訊息之一，您在泛型 LRESULT\/WPARAM\/LPARAM 格式應該使用 `ON_MESSAGE` 訊息對應巨集和處理訊息。  
  
 **WM\_QUERYAFXWNDPROC**  
  
 這個資訊傳送到建立的視窗。  這非常之前建立處理序傳送做為方法判斷 WndProc 是否 **AfxWndProc. AfxWndProc** 傳回 1。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|未使用|  
|傳回|1，如果處理 **AfxWndProc**|  
  
 **WM\_SIZEPARENT**  
  
 此資訊由框架視窗傳送至階層架構中 \(**CFrameWnd::OnSize** 呼叫 `CWnd::RepositionBars`\) 的 `CFrameWnd::RecalcLayout` 變更位置時控制列的調整在框架周圍的邊界。  **AFX\_SIZEPARENTPARAMS** 結構包含可能是 NULL\) 呼叫 `DeferWindowPos` 最小化重新繪製目前可用的用戶端矩形父代和 HDWP \(。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|**AFX\_SIZEPARENTPARAMS** 結構的位址|  
|傳回|不適用 \(0\)。|  
  
 忽略訊息指出視窗在配置不參與。  
  
 **WM\_SETMESSAGESTRING**  
  
 這個訊息會傳送至框架視窗提出要求時更新狀態列訊息行。  字串 ID 或 LPCSTR \(可以指定，而不是兩個\)。  
  
|||  
|-|-|  
|wParam|字串 ID \(或零\)|  
|lParam|字串 \(或 null\) LPCSTR|  
|傳回|不適用 \(0\)。|  
  
 **WM\_IDLEUPDATECMDUI**  
  
 這個資訊提示閒置時間實作更新命令 UI 處理常式閒置時間更新傳送。  如果視窗 \(通常是控制列\) 處理訊息，則會建立 `CCmdUI` 物件 \(或衍生類別的每個物件\) 和呼叫 **CCmdUI::DoUpdate** 「Item」在視窗。  這個接著會檢查物件的 `ON_UPDATE_COMMAND_UI` 處理常式在命令處理常式鏈結。  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|不適用 \(0\)。|  
|傳回|不適用 \(0\)。|  
  
 *bDisableIfNoHandler* 非零停用 UI 物件是否有 `ON_UPDATE_COMMAND_UI` 和 `ON_COMMAND` 處理常式。  
  
 **WM\_EXITHELPMODE**  
  
 這個訊息會向關閉即時線上說明模式的 `CFrameWnd` 。  這個訊息的收據終止 **CFrameWnd::OnContextHelp.**開始強制回應迴圈  
  
|||  
|-|-|  
|wParam|不適用 \(0\)。|  
|lParam|不適用 \(0\)。|  
|傳回|未使用|  
  
 **WM\_INITIALUPDATE**  
  
 在最初的更新時，它們是安全的此資訊由文件樣板傳送至框架視窗的所有子代。  對應至呼叫 `CView::OnInitialUpdate` ，但可用於其他 `CWnd`\-其他一次更新的衍生類別。  
  
|||  
|-|-|  
|wParam|不適用 \(0\)。|  
|lParam|不適用 \(0\)。|  
|傳回|不適用 \(0\)。|  
  
 **WM\_RECALCPARENT**  
  
 此資訊由檢視傳送給其父視窗 \(可透過 `GetParent`\) 會強制執行配置重新計算 \(通常，父代會呼叫 `RecalcLayout`\)。  這個大小增加的 OLE 伺服器應用程式框架是必要的，因為檢視的總大小成長。  
  
 如果父視窗處理此訊息應該傳回 true，並以新會填滿 lParam 傳遞的 RECT 調整工作區。  用於 `CScrollView` 適當地處理捲軸 \(位元然後視窗的，並且加入\) 時，就地啟動時的伺服器物件。  
  
|||  
|-|-|  
|wParam|不適用 \(0\)。|  
|lParam|rectClient 的 LPRECT，可能是空的|  
|傳回|為 true，否則傳回矩形的新用戶端，否則為 false。|  
  
 **WM\_SIZECHILD**  
  
 此資訊由 `COleResizeBar` 傳送至其主控視窗 \(透過 `GetOwner`\)，當使用者調整大小的調整大小控點時的調整大小列。  `COleIPFrameWnd` 回應訊息傳遞嘗試重新定位框架視窗，使用者要求。  
  
 新矩形將用戶端座標相對於包含調整資料列的框架視窗，會在 lParam。  
  
|||  
|-|-|  
|wParam|不適用 \(0\)。|  
|lParam|LPRECT rectNew|  
|傳回|不適用 \(0\)。|  
  
 **WM\_DISABLEMODAL**  
  
 這個資訊傳送到停用的框架視窗所擁有的任何快顯視窗。  框架視窗是否使用結果判斷停用快顯視窗。  
  
 您在快顯視窗可以使用此執行特殊處理，在框架進入強制回應狀態時或防止失效的某些快顯視窗。  工具提示使用此訊息自我終結，在框架視窗進入強制回應狀態時，例如。  
  
|||  
|-|-|  
|wParam|不適用 \(0\)。|  
|lParam|不適用 \(0\)。|  
|傳回|非零的 **NOT** 停用視窗， 0 表示視窗將停用|  
  
 **WM\_FLOATSTATUS**  
  
 在啟動或另一個最上層框架視窗時，停用這個框架傳送到框架視窗所擁有的任何快顯視窗。  這個由 **MFS\_SYNCACTIVE** 的實作會使用 `CMiniFrameWnd`，保留這些快顯視窗的啟用與最上層框架視窗的啟用同步處理。  
  
|||  
|-|-|  
|wParam|是下列其中一個值:<br /><br /> **FS\_SHOW**<br /><br /> **FS\_HIDE**<br /><br /> **FS\_ACTIVATE**<br /><br /> **FS\_DEACTIVATE**<br /><br /> **FS\_ENABLEFS\_DISABLE**<br /><br /> **FS\_SYNCACTIVE**|  
|lParam|不適用 \(0\)。|  
  
 傳回值應該為非零，如果 **FS\_SYNCACTIVE** 集合，且視窗會同步處理其與父框架的啟動。  當樣式設定為 **MFS\_SYNCACTIVE.**時，`CMiniFrameWnd` 會傳回非零  
  
 如需詳細資訊，請參閱 `CMiniFrameWnd`的實作。  
  
## WM\_ACTIVATETOPLEVEL  
 當一個視窗在其父群組」啟動或停用時，此訊息會傳送至最上層視窗。  視窗是最上層群組的一部分，則它是最上層視窗 \(沒有父代或擁有人\)，或者由這類視窗所擁有。  這個訊息類似於使用中屬於不同的處理序的視窗在單一視窗階層架構的情況下 **WM\_ACTIVATEAPP,** ，但是工作 \(OLE 應用程式的共用混合\)。  
  
## WM\_COMMANDHELP， WM\_HELPHITTEST， WM\_EXITHELPMODE  
 這些訊息會使用即時線上說明的實作。  如需 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md) 的詳細資訊。  
  
## MFC 私用資源格式  
 目前， MFC 會定義兩個私用資源格式: **RT\_TOOLBAR** 和 **RT\_DLGINIT**。  
  
## RT\_TOOLBAR 資源格式  
 AppWizard 提供的預設工具列根據 **RT\_TOOLBAR** 自訂資源，在 MFC 4.0 中引入。  使用工具列編輯器，您可以編輯這個資源。  
  
## RT\_DLGINIT 資源格式  
 建立 MFC 私用資源格式是用來儲存額外對話初始化資訊。  這包括在下拉式方塊中的初始字串。  這個資源格式並非設計經過手動編輯，，而是由 Visual C\+\+ 處理。  
  
 因為有 API 替代使用資訊在資源，所以 Visual C\+\+ 和這個 **RT\_DLGINIT** 資源使用 MFC 相關功能。  使用 Visual C\+\+ 比較容易撰寫，維護及長度從遠端查看翻譯應用程式。  
  
 **RT\_DLGINIT** 資源的基礎結構如下:  
  
```  
+---------------+                    \  
| Control ID    |   UINT             |  
+---------------+                    |  
| Message #     |   UINT             |  
+---------------+                    |  
|length of data |   DWORD            |  
+---------------+                    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+                    /  
|     0         |   BYTE  
+---------------+  
```  
  
 一個迴圈中包含控制項 ID 傳送訊息至佇列，訊息 \# 傳送 \(一般視窗訊息\) 和可變長度的資料。  傳送 Windows 訊息的格式:  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);  
```  
  
 這是非常一般格式，讓所有 Windows 訊息和資料內容。  Visual C\+\+ 資源編輯器和 MFC 只支援 Windows 訊息的受限制的子集:初始清單選取 CB\_ADDSTRING 下拉式方塊 \(資料是文字字串\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)