---
title: 'TN024: MFC 定義的訊息和資源 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a21ae615a3f4c644f6f0aa7c8f1306378a00ae5c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957181"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024：MFC 定義的訊息和資源
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示描述 MFC 使用的格式建置資源與內部 Windows 訊息。 此資訊會說明架構的實作，並將協助您偵錯您的應用程式。 市區，即使這項資訊是正式不受支援，您可以使用這項資訊的某些進階的實作。  
  
 此提示會包含 MFC 私用實作詳細資料;所有內容可能都會在未來變更。 MFC 私人 Windows 訊息的一個應用程式範圍中具有意義，但會在未來變更為包含全系統訊息。  
  
 範圍的 MFC 私人 Windows 訊息和資源類型會保留 「 系統 」 範圍中安排受到 Microsoft Windows。 使用目前並非所有的數字的範圍中，並在未來，可能使用新的數字，範圍中。 目前使用的數字可能會變更。  
  
 MFC 私人 Windows 訊息是在範圍內 0x360]-> [0x37F。  
  
 MFC 私人資源類型是在範圍內 0xF0]-> [0xFF。  
  
 **MFC 私人 Windows 訊息**  
  
 這些 Windows 訊息用來取代 c + + 虛擬函式相當鬆散偶合需要的地方之間視窗物件和 c + + 虛擬函式，就不適合。  
  
 在 MFC private 標頭中宣告這些私用的 Windows 訊息和相關聯的參數結構 ' AFXPRIV。H'。 會收到警告，任何包含此標頭的程式碼可能必須倚賴未記載的行為，就會斷開在未來版本的 MFC。  
  
 在極少數的需要來處理這些訊息的其中一個案例中，您應該使用 ON_MESSAGE 訊息對應巨集，並處理一般 LRESULT/WPARAM/LPARAM 格式中的訊息。  
  
 **WM_QUERYAFXWNDPROC**  
  
 此訊息會傳送至所建立的視窗。 判斷是否為 WndProc 方法非常早期中建立程序傳送**AfxWndProc。AfxWndProc**傳回 1。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|未使用|  
|傳回|1，表示處理**AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 這個訊息由傳送框架視窗至其直屬子系調整大小期間 (`CFrameWnd::OnSize`呼叫`CFrameWnd::RecalcLayout`哪些呼叫`CWnd::RepositionBars`) 來重新調整位置周圍框架的側邊的控制列。 AFX_SIZEPARENTPARAMS 結構用來呼叫包含父系和 HDWP （這可能是 NULL） 的目前可用的用戶端矩形`DeferWindowPos`降到最低重新繪製。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|AFX_SIZEPARENTPARAMS 結構的位址|  
|傳回|不使用 (0)|  
  
 忽略訊息，指出視窗不會參與配置。  
  
 **WM_SETMESSAGESTRING**  
  
 框架視窗傳送此郵件，詢問其更新狀態列中的訊息列。 字串 ID 或 LPCSTR 可以指定 （但非兩者皆是）。  
  
|||  
|-|-|  
|wParam|字串 ID （或零）|  
|lParam|LPCSTR 字串 （或 NULL）|  
|傳回|不使用 (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 若要實作更新命令 UI 處理常式的閒置時間更新，此訊息會傳送閒置時間。 如果視窗 （通常是一種控制列） 會處理訊息，它會建立`CCmdUI`物件 （或衍生類別的物件），並呼叫`CCmdUI::DoUpdate`每個 「 項目 」 視窗中。 這會接著檢查 ON_UPDATE_COMMAND_UI 處理常式的命令處理常式鏈結中的物件。  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|不使用 (0)|  
|傳回|不使用 (0)|  
  
 *bDisableIfNoHandler*為非零值以停用 UI 物件，如果沒有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 處理常式。  
  
 **WM_EXITHELPMODE**  
  
 此訊息張貼至`CFrameWnd`，結束即時線上說明模式。 接收此訊息會終止由啟動強制回應迴圈`CFrameWnd::OnContextHelp`。  
  
|||  
|-|-|  
|wParam|不使用 (0)|  
|lParam|不使用 (0)|  
|傳回|未使用|  
  
 **WM_INITIALUPDATE**  
  
 此訊息傳送的文件範本到框架視窗的所有下階時，才能執行其初始更新安全。 它會對應至呼叫`CView::OnInitialUpdate`但可用來在其他`CWnd`-衍生其他單次更新的類別。  
  
|||  
|-|-|  
|wParam|不使用 (0)|  
|lParam|不使用 (0)|  
|傳回|不使用 (0)|  
  
 **WM_RECALCPARENT**  
  
 這個訊息由檢視傳送給其父視窗 (透過取得`GetParent`) 若要強制配置重新計算 (通常會呼叫父`RecalcLayout`)。 這用在 OLE 伺服器應用程式則需要大小成長，因為檢視表的總大小會逐漸增加的框架。  
  
 如果父視窗會處理此訊息應該傳回 TRUE，並填滿傳入 lParam 工作區的新大小的矩形。 這用於`CScrollView`可正確處理捲軸 （然後在加入時加以視窗外的位置） 的伺服器物件時就地啟動。  
  
|||  
|-|-|  
|wParam|不使用 (0)|  
|lParam|LPRECT rectClient 可能是 NULL|  
|傳回|則為 TRUE，如果是新的用戶端矩形傳回，FALSE 否則|  
  
 **WM_SIZECHILD**  
  
 這個訊息由傳送`COleResizeBar`至其擁有者視窗 (透過`GetOwner`) 當使用者調整的大小調整列，以調整大小控點。 `COleIPFrameWnd` 藉由嘗試調整框架視窗的位置，因為使用者已要求，以回應這個訊息。  
  
 新的矩形中，指定用戶端座標中相對於框架視窗，其中包含 [調整] 列中，指向由 lParam。  
  
|||  
|-|-|  
|wParam|不使用 (0)|  
|lParam|LPRECT rectNew|  
|傳回|不使用 (0)|  
  
 **WM_DISABLEMODAL**  
  
 此訊息會傳送給正在停用的框架視窗所擁有的所有快顯視窗。 框架視窗會使用結果來決定要停用快顯視窗。  
  
 您可以使用此框架進入強制回應狀態時，您的快顯視窗中執行特殊處理，或取得停用時，防止某些快顯視窗。 工具提示會終結本身，框架視窗會進入強制回應狀態，例如當使用這個訊息。  
  
|||  
|-|-|  
|wParam|不使用 (0)|  
|lParam|不使用 (0)|  
|傳回|非零到**不**停用視窗中，0 表示視窗將會停用|  
  
 **WM_FLOATSTATUS**  
  
 此訊息會傳送給框架啟用或停用另一個最上層框架視窗時，框架視窗所擁有的所有快顯視窗。 會使用這個方法的實作中 MFS_SYNCACTIVE `CMiniFrameWnd`，而這些快顯視窗的啟動與保持同步的上層框架視窗啟用。  
  
|||  
|-|-|  
|wParam|是下列值之一：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|  
|lParam|不使用 (0)|  
  
 傳回的值應為非零是否 FS_SYNCACTIVE 集然後視窗將其啟動與父框架。 `CMiniFrameWnd` 樣式設定為 MFS_SYNCACTIVE 時傳回非零。  
  
 如需詳細資訊，請參閱的實作`CMiniFrameWnd`。  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 當視窗在其 「 最上層群組 」 中的啟用或停用時，此訊息會傳送至最上層視窗。 如果它是最上層視窗 （沒有父系或擁有者），或隸屬於這種視窗，視窗會是最上層群組的一部分。 這個訊息是使用類似於 WM_ACTIVATEAPP，但是 （通常在 OLE 應用程式） 的單一視窗階層架構中混用 windows 屬於不同的程序的情況下的運作方式。  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP，WM_HELPHITTEST，WM_EXITHELPMODE  
 即時線上說明的實作中，會使用這些訊息。 請參閱[技術附註 28](../mfc/tn028-context-sensitive-help-support.md)如需詳細資訊。  
  
## <a name="mfc-private-resource-formats"></a>MFC 私用的格式建置資源  
 目前，MFC 會定義兩個私用的資源格式： RT_TOOLBAR 和 RT_DLGINIT。  
  
## <a name="rttoolbar-resource-format"></a>RT_TOOLBAR 資源格式  
 AppWizard 所提供的預設工具列根據 RT_TOOLBAR 」 自訂資源，MFC 4.0 中引進。 您可以編輯這個資源，使用工具列編輯器。  
  
## <a name="rtdlginit-resource-format"></a>RT_DLGINIT 資源格式  
 MFC 私人資源格式用來儲存額外的對話方塊的初始化資訊。 這包括儲存在下拉式方塊中的初始字串。 此資源的格式不是以手動方式編輯，但是由 Visual c + +。  
  
 Visual c + + 和此 RT_DLGINIT 資源都不需要使用 MFC 的相關的功能，因為有使用中資源的資訊的 API 替代方案。 使用 Visual c + + 讓您更能更輕鬆地撰寫、 維護和轉換您的應用程式中。  
  
 RT_DLGINIT 資源的基本結構如下所示：  
  
```  
+---------------+    \  
| Control ID    |   UINT             |  
+---------------+    |  
| Message #     |   UINT             |  
+---------------+    |  
|length of data |   DWORD            |  
+---------------+    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+    /  
|     0         |   BYTE  
+---------------+  
```  
  
 重複的區段包含的控制項識別碼來傳送訊息，訊息 # 來傳送 （標準 Windows 訊息） 和可變長度的資料。 Windows 訊息會傳送表單中：  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 這是非常廣泛的格式，可讓任何 Windows 訊息和資料內容。 Visual c + + 資源編輯器和 MFC 僅支援 Windows 訊息的有限的子集： CB_ADDSTRING 的初始清單的選項 （資料是文字字串） 的下拉式方塊。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

