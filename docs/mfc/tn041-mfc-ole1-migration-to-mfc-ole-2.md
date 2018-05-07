---
title: 'TN041: MFC OLE1 移轉到 MFC OLE 2 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78faa19263ff0ea03aac891c9be3a6114f7f9a48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041：MFC/OLE1 移轉到 MFC/OLE 2
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
## <a name="general-issues-relating-to-migration"></a>與移轉相關的一般問題  
 OLE 2 類別在 MFC 2.5 （和更新版本） 的設計目標之一就是保留大部分 OLE 1.0 支援 MFC 2.0 各就各位相同架構。 如此一來，許多相同的 OLE 類別，MFC 2.0 仍存在於此版本的 MFC (`COleDocument`， `COleServerDoc`， `COleClientItem`， `COleServerItem`)。 此外，許多這些類別中的 Api 都完全相同。 不過，OLE 2 是從 OLE 1.0 大幅不同，因此，您可以預期某些詳細資料已變更。 如果您熟悉 MFC 2.0 OLE1 支援，您會覺得在家使用 MFC 的 2.0 的支援。  
  
 如果您是採用現有的 MFC/OLE1 應用程式，而且加入 OLE 2 功能，您應該先閱讀這個附註。 此提示涵蓋您移植到 MFC/OLE 2 您 OLE1 功能時可能會遇到並接著討論移植 MFC 2.0 中包含的兩個應用程式時發現問題的一般問題： MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)和[HIERSVR](../visual-cpp-samples.md)。  
  
## <a name="mfc-documentview-architecture-is-important"></a>MFC 文件/檢視架構非常重要  
 如果您的應用程式不使用 MFC 的文件/檢視架構，而且您想要將 OLE 2 支援加入至您的應用程式，現在是將移至文件/檢視的時間。 許多的 MFC 的 OLE 2 類別的優點只實現一旦應用程式使用的內建架構和 MFC 的元件。  
  
 不使用 MFC 架構中實作的伺服器或容器是可行的但不是建議使用。  
  
## <a name="use-mfc-implementation-instead-of-your-own"></a>使用而非您自己的 MFC 實作  
 MFC"canned 實作 」 的類別，例如`CToolBar`， `CStatusBar`，和`CScrollView`有內建特殊案例的程式碼如 OLE 2 的支援。 因此，如果您可以在應用程式中使用這些類別會受益放入它們的工作，讓它們 OLE 知道。 同樣地，它可以到這裡 「 向前復原-您-擁有 「 類別針對這些用途，但不是建議。 如果您需要實作類似的功能，MFC 原始程式碼是 OLE 的絕佳部分進行更細微點處理 （特別是 OLE 的當就地啟用）。  
  
## <a name="examine-the-mfc-sample-code"></a>檢查 MFC 範例程式碼  
 有多個包含 OLE 功能的 MFC 範例。 每一個這些應用程式會實作 OLE 從不同角度：  
  
- [HIERSVR](../visual-cpp-samples.md)主要是用來做為伺服器應用程式。 它包含在 MFC 2.0 為 MFC/OLE1 應用程式中，而且具有已移植到 MFC/OLE 2，然後延伸，它會實作 OLE 2 提供的許多 OLE 功能。  
  
- [OCLIENT](../visual-cpp-samples.md)這是獨立的容器應用程式，用來從容器的觀點來示範許多 OLE 功能。 它太移植而從 MFC 2.0，然後延伸以支援許多更進階的 OLE 功能，例如自訂剪貼簿格式和內嵌項目的連結。  
  
- [DRAWCLI](../visual-cpp-samples.md)此應用程式會實作 OLE 容器支援更 OCLIENT 類似，不同之處在於它會以在現有的物件導向繪圖程式架構內。 它會顯示如何實作 OLE 容器支援並將其整合到現有的應用程式。  
  
- [SUPERPAD](../visual-cpp-samples.md)此應用程式，以及細緻的獨立應用程式，也是 OLE 伺服器。 它所實作的伺服器支援是很冗長的最簡單。 特別值得注意的是如何使用 OLE 剪貼簿服務將資料複製到剪貼簿，但使用的 Windows"edit"控制項內建功能來實作剪貼簿貼上功能。 這會顯示有趣混合的傳統 Windows API 使用方式，以及整合新 OLE api。  
  
 如需範例應用程式的詳細資訊，請參閱 「 MFC 範例說明 」。  
  
## <a name="case-study-oclient-from-mfc-20"></a>從 MFC 2.0 案例研究： OCLIENT  
 如上所述， [OCLIENT](../visual-cpp-samples.md)包含 MFC 2.0 中，並實作 OLE 的 MFC/OLE1。 以下將詳述的步驟，此應用程式一開始轉換使用 MFC/OLE 2 類別。 為了更清楚說明 MFC/OLE 類別完成的初始連接埠後，已加入了多種功能。 這些功能不會涵蓋。請參閱範例本身如需有關這些進階功能。  
  
> [!NOTE]
>  編譯器錯誤和逐步程序是以 Visual c + + 2.0 建立的。 特定的錯誤訊息和位置可能已變更 Visual c + + 4.0，但概念的資訊就持續有效。  
  
## <a name="getting-it-up-and-running"></a>快速安裝和執行  
 移植到 MFC/OLE OCLIENT 範例採用的方法是從開始建置它，並修正會產生明顯的編譯器錯誤。 如果您從 MFC 2.0 進行 OCLIENT 取樣，並編譯這個版本的 MFC 下，您會看到不會有那麼多的錯誤，以解決。 以下將說明其發生的順序中的錯誤。  
  
## <a name="compile-and-fix-errors"></a>編譯和修正錯誤  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 第一個錯誤考量`COleClientItem::Draw`。 在 MFC/OLE1 花費更多非 MFC/OLE 版本會接受的參數。 所需，且通常是 NULL （如此範例所示），通常沒有額外的參數。 這個版本的 MFC CDC 所要繪製中繼檔 DC 時，可以自動判斷 lpWBounds 的值。 此外，pFormatDC 參數不再需要因為架構會建立從 「 屬性 DC 」 的傳入 pDC。 因此，若要修正此問題，您只要移除兩個額外的繪製呼叫的參數為 NULL。  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 上面的 naïve 結果錯誤，所有的**COleClientItem::CreateXXXX** MFC/OLE1 中的函式所需的唯一名稱可將傳遞至代表項目。 這是基礎 OLE API 的需求。 這是不必要的 MFC/OLE 2，因為 OLE 2 不會使用 DDE 做為基礎的通訊機制 （DDE 交談中使用的名稱）。 若要修正此問題，您可以移除**CreateNewName**以及它的所有參考函式。 所以可以輕鬆地找出每個 MFC/OLE 函數會預期在此版本中只要將游標放在呼叫，然後按下 f1 鍵。  
  
 另一個區域非常不同的是 OLE 2 剪貼簿處理。 使用 OLE1，您可以使用 Windows 剪貼簿應用程式開發介面互動與剪貼簿。 OLE 2 做法是使用不同的機制。 MFC/OLE1 Api 假設剪貼簿複製之前已開啟`COleClientItem`到剪貼簿的物件。 這已不再需要，會導致所有 MFC/OLE 剪貼簿作業失敗。 當您編輯上移除相依性的程式碼時**CreateNewName**，您也應該移除的程式碼，開啟和關閉 Windows 剪貼簿。  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 這些錯誤會造成從**CMainView::OnInsertObject**處理常式。 處理 「 插入新物件 」 命令是另一個項目已稍微變更。 在此情況下，很簡單，只要合併的原始實作與 appwizard 提供新的 OLE 容器應用程式。 事實上，這是一種技術，您可以套用到移植其他應用程式。 在 MFC/OLE1，您必須顯示 「 插入的物件 」 對話方塊藉由呼叫**AfxOleInsertDialog**函式。 在此版本中建構**COleInsertObject**對話方塊物件並呼叫`DoModal`。 此外，與建立新的 OLE 項目**CLSID**而不是類別名稱字串。 最終結果看起來應該像這樣  
  
```  
COleInsertDialog dlg;  
if (dlg.DoModal() != IDOK)  
    return; 
 
BeginWaitCursor();

 
CRectItem* pItem = NULL;  
TRY  
{ *// First create the C++ object  
    pItem = GetDocument()->CreateItem();
ASSERT_VALID(pItem);

 *// Initialize the item from the dialog data.  
    if (!dlg.CreateItem(pItem))  
    AfxThrowMemoryException();
*// any exception will do  
    ASSERT_VALID(pItem);

 *// run the object if appropriate  
    if (dlg.GetSelectionType() == 
    COleInsertDialog::createNewItem) 
    pItem->DoVerb(OLEIVERB_SHOW,
    this);

 *// update right away  
    pItem->UpdateLink();
pItem->UpdateItemRectFromServer();

 *// set selection to newly inserted item  
    SetSelection(pItem);

 pItem->Invalidate();

}  
CATCH (CException,
    e)  
{ *// clean up item  
    if (pItem != NULL)  
    GetDocument()->DeleteItem(pItem);

 
    AfxMessageBox(IDP_FAILED_TO_CREATE);

} 
END_CATCH  
 
EndWaitCursor();
```  
  
> [!NOTE]
>  插入新的物件可能會不同應用程式）：  
  
 它也是必要包含\<afxodlgs.h >，其中包含的宣告**COleInsertObject**對話方塊類別，以及其他 MFC 提供的標準對話方塊。  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 這些錯誤被因某些 OLE1 常數已變更為 OLE 2 的事實，即使它們是相同的概念。 在此情況下**OLEVERB_PRIMARY**已變更為`OLEIVERB_PRIMARY`。 在 OLE1 和 OLE 2 中，主要的動詞命令通常執行容器當使用者按兩下項目上。  
  
 此外，`DoVerb`現在採用額外的參數，以檢視的指標 (`CView`*)。 這個參數只用於實作 「 視覺化編輯 」 （或就地啟用）。 現在您設定該參數為 NULL，因為您在此階段不實作這項功能。  
  
 若要確定，架構永遠不會嘗試在就地啟用，您應該覆寫`COleClientItem::CanActivate`，如下所示：  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
 
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC/OLE1， **COleClientItem::GetBounds**和**SetBounds**用來查詢與管理的項目範圍 (**左**和**頂端**成員永遠是零)。 MFC/OLE 2 中支援這種更直接`COleClientItem::GetExtent`和`SetExtent`，其處理**大小**或`CSize`改為。  
  
 您的新 SetItemRectToServer 的程式碼和 UpdateItemRectFromServer 呼叫看起來像這樣：  
  
```  
BOOL CRectItem::UpdateItemRectFromServer()  
{  
    ASSERT(m_bTrackServerSize);

 CSize size;  
    if (!GetExtent(&size))  
    return FALSE;    // blank  
 *// map from HIMETRIC to screen coordinates  
 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.LPtoDP(&size);

 } *// just set the item size  
    if (m_rect.Size() != size)  
 { *// invalidate the old size/position  
    Invalidate();
m_rect.right = m_rect.left + size.cx;  
    m_rect.bottom = m_rect.top + size.cy; *// as well as the new size/position  
    Invalidate();

 }  
    return TRUE;  
}  
 
BOOL CRectItem::SetItemRectToServer()  
{ *// set the official bounds for the embedded item  
    CSize size = m_rect.Size();

 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.DPtoLP(&size);

 }  
    TRY 
 {  
    SetExtent(size);
*// may do a wait  
 }  
    CATCH(CException, e)  
 {  
    return FALSE;  // links will not allow SetBounds  
 }  
    END_CATCH 
    return TRUE;  
}  
 
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC/OLE1 同步 API 是從容器呼叫伺服器*模擬*，因為 OLE1 已在許多情況下原本就是非同步。 它是為了處理來自使用者的命令之前，先檢查進行中的未處理的非同步呼叫。 提供的 MFC/OLE1 **COleClientItem::InWaitForRelease**函式，這麼做。 在 MFC/OLE 2 這並非必要，這樣您就可以一起 CMainFrame 中移除的 OnCommand 覆寫。  
  
 此時 OCLIENT 會編譯及連結。  
  
## <a name="other-necessary-changes"></a>其他必要的變更  
 有幾個項目，不會進行要保持 OCLIENT 執行，不過。 最好是修正這些問題，現在而不是更新版本。  
  
 首先，它不需要初始化 OLE 程式庫。 這是藉由呼叫**AfxOleInit**從`InitInstance`:  
  
```  
if (!AfxOleInit())  
{  
    AfxMessageBox("Failed to initialize OLE libraries");

    return FALSE;  
}  
```  
  
 它也是建議您檢查有虛擬函式參數清單的變更。 一個這類函式是`COleClientItem::OnChange`、 覆寫每個 MFC/OLE 容器應用程式中。 藉由查看線上說明，您會看到已加入額外 'DWORD dwParam'。 新 CRectItem::OnChange 看起來如下：  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
    if (m_bTrackServerSize&& 
 !UpdateItemRectFromServer())  
 { *// Blank object  
    if (wNotification == OLE_CLOSED)  
 { *// no data received for the object - destroy it  
    ASSERT(!IsVisible());

 GetDocument()->DeleteItem(this);

    return; // no update (item is gone now)  
 }  
 }  
    if (wNotification != OLE_CLOSED)  
    Dirty();
Invalidate();
*// any change will cause a redraw  
}  
```  
  
 在 MFC/OLE1，容器應用程式的衍生來源的文件類別**COleClientDoc**。 在 MFC/OLE 2 這個類別已被移除並取代`COleDocument`（這個新的組織可讓您更輕鬆地建立容器/伺服器應用程式）。 沒有`#define`對應**COleClientDoc**至`COleDocument`簡化移植到 MFC/OLE 2 例如 OCLIENT MFC/OLE1 應用程式。 未提供的功能之一`COleDocument`所提供的**COleClientDoc**是標準命令訊息對應項目。 這完成該伺服器應用程式，也使用`COleDocument`（間接），不會包含與它們的這些命令處理常式的額外負荷除非容器/伺服器應用程式。 您需要下列項目新增至 CMainDoc 訊息對應：  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE,
    OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK,
    OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS,
    OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS,
    COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST,
    OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT,
    OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT,
    OnEditConvert)  
```  
  
 所有這些命令的實作是採用`COleDocument`，這是您的文件的基底類別。  
  
 此時，OCLIENT 是功能的 OLE 容器應用程式。 它是可以插入 （OLE1 或 OLE 2） 的任何類型的項目。 未實作必要的程式碼，以便在就地啟用，因為在類似 OLE1 與另一個視窗中編輯項目。 下一節討論必要的變更，以啟用就地編輯 （有時稱為 「 視覺化編輯"）。  
  
## <a name="adding-visual-editing"></a>新增 「 視覺化編輯"  
 OLE 的最有趣的功能之一是就地啟用 （或 「 視覺化編輯"）。 這項功能可讓伺服器應用程式，以便透過容器的使用者介面的部分使用者提供更順暢的編輯介面。 若要實作以 OCLIENT 就地啟用，某些特殊的資源需要新增，以及某些其他程式碼。 這些資源和程式碼通常提供 appwizard — 事實上，大部分的程式碼取自直接與 「 容器 」 支援的全新 AppWizard 應用程式。  
  
 首先，就必須加入功能表資源，也就是就地啟用作用中的項目時使用。 您可以建立 Visual c + + 中的這項額外的功能表資源複製 IDR_OCLITYPE 資源，並移除檔案和視窗的快顯視窗以外的所有節點。 指出群組的分隔的檔案和視窗快顯之間會插入兩個分隔線 (看起來應該像： 檔案&#124;&#124;視窗)。 如需這些分隔符號所代表的意義和伺服器和容器的功能表要如何合併的詳細資訊請參閱 「 功能表和資源:: 功能表合併 」，在*OLE 2 類別*。  
  
 建立這些功能表之後，您需要讓架構知道它們。 這是藉由呼叫`CDocTemplate::SetContainerInfo`才能將它加入文件範本清單： updateregistryall 的文件範本。 新的程式碼，以註冊文件範本看起來像這樣：  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE, 
    RUNTIME_CLASS(CMainDoc), 
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame  
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```   
  
 IDR_OLECLITYPE_INPLACE 資源是在 Visual c + + 中建立的特殊就地資源。  
  
 若要啟用就地啟用，有幾個步驟，需要變更在`CView`(CMainView) 衍生的類別，以及`COleClientItem`衍生類別 (CRectItem)。 所有這些覆寫由提供 AppWizard，大部分的實作會直接從預設 AppWizard 應用程式。  
  
 在此通訊埠的第一個步驟中，就地啟用已停用網路完全覆寫`COleClientItem::CanActivate`。 若要允許就地啟用，就應該移除此覆寫。 此外，傳遞 NULL 給所有呼叫`DoVerb`（有其中兩個） 因為提供的檢視時才需要進行就地啟用。 若要完全實作就地啟用，是為了傳遞正確的檢視中`DoVerb`呼叫。 這些呼叫的其中一個是**CMainView::OnInsertObject**:  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);
```  
  
 另一個是在**CMainView::OnLButtonDblClk**:  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```  
  
 必須覆寫`COleClientItem::OnGetItemPosition`。 這會要求伺服器要放置它的視窗相對於容器的視窗，項目時就地啟動。 OCLIENT，實作是 trivial:  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 大部分的伺服器也會實作稱為 「 就地調整大小。 」 這可讓伺服器視窗大小及移動時使用者編輯項目。 容器必須參與此動作，因為移動或調整視窗通常會影響的位置和大小，在容器文件本身。 OCLIENT 的實作會同步處理內部維護的 m_rect 使用新的位置和大小的矩形。  
  
```  
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)  
{  
    ASSERT_VALID(this);

 
    if (!COleClientItem::OnChangeItemPosition(rectPos))  
    return FALSE;  
 
    Invalidate();
m_rect = rectPos;  
    Invalidate();
GetDocument()->SetModifiedFlag();

 
    return TRUE;  
}  
```  
  
 此時，沒有足夠的程式碼，以允許的項目就地啟動以及處理調整大小和移動項目時作用中，但沒有程式碼可讓使用者在編輯工作階段的結束。 雖然某些伺服器可提供這項功能自行處理 esc 鍵，但建議容器提供兩種方式可以停用項目: （1） 按一下外部項目，或 （2） 藉由按下 ESC 鍵。  
  
 逸出索引鍵，新增將 VK_ESCAPE 鍵對應至命令的 Visual c + + 加速器，則 ID_CANCEL_EDIT 加入至資源。 此命令的處理常式會遵循：  
  
```  
// The following command handler provides the standard  
// keyboard user interface to cancel an in-place  
// editing session.void CMainView::OnCancelEdit()  
{ *// Close any in-place active item on this view.  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->Close();
ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);

}  
```  
  
 若要處理的情況，以便使用者按一下項目之外，您必須加入下列程式碼的開頭**CMainView::SetSelection**:  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& pActiveItem != pNewSel)  
    pActiveItem->Close();

} 
 
```  
  
 就地啟用作用中的項目時，應該有焦點。 若要確保此情況下您會處理 OnSetFocus，讓您檢視取得焦點時一律焦點轉移到作用中的項目：  
  
```  
// Special handling of OnSetFocus and OnSize are required   
// when an object is being edited in-place.  
void CMainView::OnSetFocus(CWnd* pOldWnd)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& 
    pActiveItem->GetItemState() == COleClientItem::activeUIState)  
 { *// need to set focus to this item if it is same view  
    CWnd* pWnd = pActiveItem->GetInPlaceWindow();
if (pWnd != NULL)  
 {  
    pWnd->SetFocus();
*// don't call the base class  
    return; 
 }  
 }  
 
    CView::OnSetFocus(pOldWnd);

} 
```  
  
 當檢視調整大小時，您需要通知已變更的裁剪方框現用項目。 若要這樣做您提供的處理常式`OnSize`:  
  
```  
void CMainView::OnSize(UINT nType,
    int cx,
    int cy)  
{  
    CView::OnSize(nType,
    cx,
    cy);

    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->SetItemRects();

} 
```  
  
## <a name="case-study-hiersvr-from-mfc-20"></a>從 MFC 2.0 案例研究： HIERSVR  
 [HIERSVR](../visual-cpp-samples.md)也包含在 MFC 2.0 中，並實作 OLE 的 MFC/OLE1。 這個附註將簡短描述，此應用程式一開始轉換使用 MFC/OLE 2 類別的步驟。 為了更清楚說明 MFC/OLE 2 類別完成的初始連接埠後，已加入了多種功能。 這些功能不會涵蓋。請參閱範例本身如需有關這些進階功能。  
  
> [!NOTE]
>  編譯器錯誤和逐步程序是以 Visual c + + 2.0 建立的。 特定的錯誤訊息和位置可能已變更 Visual c + + 4.0，但概念的資訊就持續有效。  
  
## <a name="getting-it-up-and-running"></a>快速安裝和執行  
 移植到 MFC/OLE HIERSVR 範例採用的方法是從開始建置它，並修正會產生明顯的編譯器錯誤。 如果您從 MFC 2.0 中接受 HIERSVR 範例，並編譯這個版本的 MFC 下，您會看到不會有多錯誤，無法解析 （雖然有多個具有 OCLIENT 範例）。 如下所述的順序，通常發生的錯誤。  
  
## <a name="compile-and-fix-errors"></a>編譯和修正錯誤  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 此第一個錯誤指出大問題與`InitInstance`函式的伺服器。 OLE 伺服器所需的初始化可能是其中一個最大的變更，您必須對您的 MFC/OLE1 應用程式，並執行。 最佳做法是查看 AppWizard 建立的 OLE 伺服器，並修改為適當的程式碼。 以下是一些重點，請記住以下幾點：  
  
 必須初始化 OLE 程式庫，藉由呼叫**AfxOleInit**  
  
 在 設定伺服器的資源控制代碼，您無法使用設定的執行階段類別資訊的文件範本物件上呼叫 SetServerInfo`CDocTemplate`建構函式。  
  
 如果命令列上存在 /Embedding，則不顯示您的應用程式的主視窗。  
  
 您將需要**GUID**文件。 這是您的文件類型 （128 位元） 的唯一識別碼。 AppWizard 將您建立一個，因此如果您使用此處所描述的技術的新 AppWizard 產生伺服器應用程式中複製新的程式碼，您可以只是"竊取 」 來自該應用程式的 GUID。 如果沒有，您可以使用 GUIDGEN。EXE 公用程式的 BIN 目錄中。  
  
 需要 「 連接 」 您`COleTemplateServer`物件至文件範本，藉由呼叫`COleTemplateServer::ConnectTemplate`。  
  
 當單獨執行您的應用程式時，請更新系統登錄。 如此一來，如果使用者移。EXE 應用程式，執行從其新位置，將會更新 Windows 系統註冊資料庫，以指向新位置。  
  
 在套用所有的基礎 AppWizard 建立的這些變更後`InitInstance`、 `InitInstance` （及相關的 GUID） HIERSVR 應該讀取，如下所示：  
  
```  
// this is the GUID for HIERSVR documents  
static const GUID BASED_CODE clsid = 
 { 0xA0A16360L,
    0xC19B,
    0x101A, { 0x8C,
    0xE5,
    0x00,
    0xDD,
    0x01,
    0x11,
    0x3F,
    0x12 } };  
 
/////////////////////////////////////////////////////////////////////////////  
// COLEServerApp initialization  
 
BOOL COLEServerApp::InitInstance()  
{ *// OLE 2 initialization  
    if (!AfxOleInit())  
 {  
    AfxMessageBox("Initialization of the OLE failed!");

    return FALSE;  
 }  
 *// Standard initialization  
    LoadStdProfileSettings();

// Load standard INI file options   
 *// Register document templates  
    CDocTemplate* pDocTemplate;  
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,  
    RUNTIME_CLASS(CServerDoc), 
    RUNTIME_CLASS(CMDIChildWnd), 
    RUNTIME_CLASS(CServerView));

 pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);

    AddDocTemplate(pDocTemplate);

 *// create main MDI Frame window  
    CMainFrame* pMainFrame = new CMainFrame;  
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))  
    return FALSE;  
    m_pMainWnd = pMainFrame;  
 
    SetDialogBkColor();
*// gray look  
 *// enable file manager drag/drop and DDE Execute open  
    m_pMainWnd->DragAcceptFiles();
EnableShellOpen();

 
    m_server.ConnectTemplate(clsid,
    pDocTemplate,
    FALSE);

    COleTemplateServer::RegisterAll();

 *// try to launch as an OLE server  
    if (RunEmbedded())  
 { *// "short-circuit" initialization -- run as server!  
    return TRUE;  
 }  
    m_server.UpdateRegistry();
RegisterShellFileTypes();

 *// not run as OLE server,
    so show the main window  
    if (m_lpCmdLine[0] == '\0')  
 { *// create a new (empty) document  
    OnFileNew();

 }  
    else 
 { *// open an existing document  
    OpenDocumentFile(m_lpCmdLine);

 }  
 
    pMainFrame->ShowWindow(m_nCmdShow);

 pMainFrame->UpdateWindow();

 
    return TRUE;  
}  
```  
  
 您會注意到，新的資源 ID、 IDR_HIERSVRTYPE_SRVR_EMB 是指上述程式碼。 這是要在編輯內嵌於其他容器文件時使用的功能表資源。 在 MFC/OLE1 特定編輯內嵌項目的功能表項目已修改即時。 使用完全不同的功能表結構，編輯內嵌項目，而不是編輯以檔案為基礎的文件時，可更輕鬆地提供這兩種不同的模式不同的使用者介面。 您稍後將會看到時編輯內嵌的物件就地, 使用完全不同的功能表資源。  
  
 若要建立此資源，載入 Visual c + + 中的資源指令碼並將複製現有的 IDR_HIERSVRTYPE 功能表資源。 將新的資源重新命名為 IDR_HIERSVRTYPE_SRVR_EMB （這是 AppWizard 使用的相同命名慣例）。 接下來將變更 「 儲存的檔案 」 為 「 檔案更新; 」命令 ID 提供給它**ID_FILE_UPDATE**。 也會將變更 「 檔案另存新檔 」"複本存新檔 」。命令 ID 提供給它**ID_FILE_SAVE_COPY_AS**。 架構會提供這兩種命令的實作。  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 有數個錯誤所產生的覆寫`OnSetData`，因為它參考**OLESTATUS**型別。 **OLESTATUS**已 OLE1 傳回錯誤的方式。 這已變更為`HRESULT`在 OLE 2 中，雖然 MFC 通常會將轉換`HRESULT`到`COleException`包含錯誤。 在此特定情況下，覆寫`OnSetData`不再需要，因此最簡單的做法是將它移除。  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 `COleServerItem`建構函式會採用額外 'BOOL' 參數。 這個旗標決定記憶體管理會對`COleServerItem`物件。 設定為 TRUE，架構會處理這些物件的記憶體管理，就不再需要時加以刪除。 HIERSVR 使用**CServerItem** (衍生自`COleServerItem`) 做為其原生資料，因此您會將此旗標設為 FALSE 的一部分的物件。 這可讓 HIERSVR 判斷當刪除每個伺服器項目時。  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 這些錯誤表示，如有擁有尚未被覆寫 CServerItem 中某些 '純虛擬' 函式。 最有可能被原因 OnDraw 的參數清單已變更的事實。 若要修正這個錯誤，變更**cserveritem:: Ondraw** ，如下所示 （以及 svritem.h 中的宣告）：  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC,
    CSize& rSize)  
{ *// request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT);

// always in pixels  
    return DoDraw(pDC,
    CPoint(0,
    0),
    FALSE);

}  
```  
  
 新的參數是 'rsize 則'。 這可讓您以填滿的繪圖，大小如果方便。 這個大小必須在**HIMETRIC**。 在此情況下，並不方便填入此值，所以架構會呼叫`OnGetExtent`擷取範圍。 為此工作，您必須實作`OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect,
    CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
    return COleServerItem::OnGetExtent(dwDrawAspect,
    rSize);

 
    rSize = CalcNodeSize();
return TRUE;  
}  
 
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 CServerItem::CalcNodeSize 函式中的項目大小轉換成**HIMETRIC**而且儲存在**m_rectBounds**。 未記載 '**m_rectBounds**' 的成員`COleServerItem`不存在 (它已經由部分取代`m_sizeExtent`，但為 OLE 2 這個成員已稍微不同的使用方式比**m_rectBounds**OLE1 中)。 而不是設定**HIMETRIC**大小到此成員變數，您會將它傳回。 這個傳回值用於`OnGetExtent`的先前實作。  
  
```  
CSize CServerItem::CalcNodeSize()  
{  
    CClientDC dcScreen(NULL);

 
    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,  
    m_strDescription.GetLength());

 m_sizeNode += CSize(CX_INSET* 2,
    CY_INSET* 2);

 *// set suggested HIMETRIC size  
    CSize size(m_sizeNode.cx,
    m_sizeNode.cy);

    dcScreen.SetMapMode(MM_HIMETRIC);

 dcScreen.DPtoLP(&size);

    return size;  
}  
```  
  
 CServerItem 也會覆寫**COleServerItem::OnGetTextData**。 此函式 MFC/OLE 中已過時，並取代為不同的機制。 MFC OLE 範例 MFC 3.0 版[HIERSVR](../visual-cpp-samples.md)實作這項功能，藉由覆寫`COleServerItem::OnRenderFileData`。 這項功能並不重要這個基本的連接埠，所以您可以移除 OnGetTextData 覆寫。  
  
 有許多詳細錯誤 svritem.cpp 中的並未提及。 它們不是 「 實際 」 錯誤，只是先前的錯誤所造成的錯誤。  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard` 不再支援 'bIncludeNative' 旗標。 永遠複製原生資料 （資料寫出的伺服器項目的序列化函式），讓您移除第一個參數。 此外，`CopyToClipboard`而不是傳回 FALSE 就會發生錯誤時將會擲回例外狀況。 變更程式碼的 CServerView::OnEditCopy，如下所示：  
  
```  
void CServerView::OnEditCopy()  
{  
    if (m_pSelectedNode == NULL)  
    AfxThrowNotSupportedException();

 
    TRY 
 {  
    m_pSelectedNode->CopyToClipboard(TRUE);

 }  
    CATCH_ALL(e) 
 {  
    AfxMessageBox("Copy to clipboard failed");

 }  
    END_CATCH_ALL 
}  
```  
  
 雖然沒有比沒有相同版本的 OCLIENT HIERSVR MFC 2.0 版的編譯所產生的多個錯誤，但沒有實際更少的變更。  
  
 此時 HIERSVR 會編譯和連結並為 OLE 伺服器，但不會就地編輯功能，接下來將會實作函式。  
  
## <a name="adding-visual-editing"></a>新增 「 視覺化編輯"  
 若要加入至此伺服器應用程式"視覺化編輯 」 （或就地啟用），有只有幾件事您必須負責：  
  
-   您需要的項目是就地啟用作用中時所要使用特殊功能表資源。  
  
-   此應用程式有工具列，因此您將需要一般的工具列，以符合功能表命令來自伺服器的可用 （符合上面所述的功能表資源） 的子集包含的工具列。  
  
-   您需要新的類別衍生自`COleIPFrameWnd`提供就地使用者介面 (就像是 CMainFrame，衍生自`CMDIFrameWnd`，提供的 MDI 使用者介面)。  
  
-   您必須向架構指出有關這些特殊的資源和類別。  
  
 功能表資源很容易建立。 執行 Visual c + +，複製功能表資源 IDR_HIERSVRTYPE 呼叫 IDR_HIERSVRTYPE_SRVR_IP 功能表資源。 修改  功能表，讓只有 編輯後說明功能表快顯會保留。 編輯 與 說明功能表之間的功能表中加入兩個分隔符號 (看起來應該像： 編輯&#124;&#124;協助)。 如需有關這些分隔符號所代表的意義和伺服器和容器的功能表要如何合併的詳細資訊，請參閱 「 功能表和資源:: 功能表合併 」 *OLE 2 類別*。  
  
 藉由使用 「 伺服器 」 選項，檢查複製從全新的 AppWizard 產生應用程式的一個可以輕鬆地建立子集工具列的點陣圖。 此點陣圖然後匯入到 Visual c + +。 請務必提供點陣圖 IDR_HIERSVRTYPE_SRVR_IP 識別碼。  
  
 類別衍生自`COleIPFrameWnd`可以從 AppWizard 產生應用程式與伺服器的支援，以及複製。 將這兩個檔案，IPFRAME 複製。CPP 和 IPFRAME。H 並將其新增至專案。 請確定`LoadBitmap`呼叫是指 IDR_HIERSVRTYPE_SRVR_IP，先前步驟中建立的點陣圖。  
  
 現在，會建立所有新的資源和類別，加入必要的程式碼，讓架構知道這些 （並知道此應用程式現在支援就地編輯）。 這由加入一些其他參數以`SetServerInfo`呼叫中`InitInstance`函式：  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```  
  
 現在已就緒可執行就地也支援就地啟用任何容器中。 但是，有一個次要錯誤是在程式碼仍然潛藏。 HIERSVR 支援內容功能表上，當使用者按下滑鼠按鈕時顯示。 HIERSVR 是完全開啟，但無法運作時編輯內嵌就地適用於此功能表。 原因可以向下釘選到這個單行 CServerView::OnRButtonDown 中的程式碼：  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```  
  
 請注意參考**AfxGetApp()]-> [m_pMainWnd**。 就地啟用的伺服器時，它必須主視窗和設定 m_pMainWnd，但卻通常是不可見。 此外，此視窗是指*主要*應用程式視窗，MDI 框架視窗出現時的伺服器是完全開啟或執行獨立。 它並不是指使用中框架視窗，其中就地啟動時，框架視窗衍生自`COleIPFrameWnd`。 若要取得正確的使用中視窗，就地編輯，此版本的 MFC 將加入新的函式，即使`AfxGetMainWnd`。 一般而言，您應該使用此函式，而不是**AfxGetApp()]-> [m_pMainWnd**。 此程式碼需要變更，如下所示：  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetMainWnd());
```  
  
 現在您可以使用最低限度啟用以供功能就地啟動 OLE 伺服器。 但仍有許多功能適用於 MFC/OLE1 中所沒有的 MFC/OLE 2。 您可能想要實作的功能，請參閱 HIERSVR 範例如需詳細資訊。 以下列出一些 HIERSVR 實作的功能：  
  
-   縮放為容器而言，則為 true，所得行為。  
  
-   卸除 / 拖曳到和自訂剪貼簿格式。  
  
-   已變更為選取範圍容器視窗捲動。  
  
 MFC 3.0 HIERSVR 範例也會使用其伺服器項目稍有不同的設計。 這有助於節省記憶體，並使您的連結更有彈性。 HIERSVR 2.0 版與每個節點在樹狀目錄中*是 a* `COleServerItem`。 `COleServerItem` 會更多的負擔，而不是絕對必要，每個這些節點，但`COleServerItem`需要為每個作用中的連結。 但大部分的情況下，有極少數的作用中連結在任何指定時間。 若要進行更有效率，在這個版本的 MFC HIERSVR 分隔節點從`COleServerItem`。 它有兩個 CServerNode 和**CServerItem**類別。 **CServerItem** (衍生自`COleServerItem`)，才會建立在必要時。 一旦容器 （或） 容器停止使用該特定連結至該特定節點，會刪除相關聯 CServerNode CServerItem 物件。 這項設計會更有效率且更有彈性。 當處理多個選取項目連結的成為它的彈性。 HIERSVR 下列兩個版本都不支援多重選取，但它會更輕鬆地新增 （並以支援這類的選取項目連結） 與 HIERSVR，MFC 3.0 版因為`COleServerItem`分開原生資料。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

