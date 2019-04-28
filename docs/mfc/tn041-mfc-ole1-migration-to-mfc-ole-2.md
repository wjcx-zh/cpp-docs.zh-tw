---
title: TN041:-OLE1 移轉到 MFC-OLE 2
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
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
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305446"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041:MFC/OLE1 移轉到 MFC/OLE 2

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

## <a name="general-issues-relating-to-migration"></a>與移轉相關的一般問題

OLE 2 類別在 MFC 2.5 （和更新版本） 的設計目標之一是要保留許多 OLE 1.0 支援的 MFC 2.0 中的適當加諸的相同架構。 如此一來，許多相同的 OLE 類別，MFC 2.0 仍存在於這個 MFC 版本 (`COleDocument`， `COleServerDoc`， `COleClientItem`， `COleServerItem`)。 此外，許多這些類別中的 api 都是完全相同。 不過，OLE 2 與 OLE 1.0 大幅不同，因此，您可以預期某些詳細資料已變更。 如果您是熟悉 MFC 2.0 OLE1 支援，您會感到自在使用 MFC 的 2.0 支援。

如果您是採用現有的 MFC/OLE1 應用程式，並加入 OLE 2 的功能，您應該先閱讀本附註。 此提示涵蓋一些您移植到 MFC/OLE 2 您 OLE1 功能時可能會碰到並接著討論移植 MFC 2.0 中包含的兩個應用程式時所發現的問題的一般問題： MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)。

## <a name="mfc-documentview-architecture-is-important"></a>MFC 文件/檢視架構很重要，

如果您的應用程式不會使用 MFC 的文件/檢視架構，而且您想要將 OLE 2 支援新增至您的應用程式，現在正是移至文件/檢視。 一旦應用程式所使用的內建的架構和 MFC 元件的許多 MFC 的 OLE 2 類別的優點是只實現的。

實作伺服器或容器，而不使用 MFC 架構是可行的但不是建議使用。

## <a name="use-mfc-implementation-instead-of-your-own"></a>使用而非您自己的 MFC 實作

「 定義實作 「 MFC 類別，例如`CToolBar`， `CStatusBar`，和`CScrollView`有內建特殊案例的程式碼 OLE 2 支援。 因此，如果您可以在您的應用程式中使用這些類別會受益放入其中的工作，讓他們 OLE 知道。 同樣地，就可以 「 向前復原自己 「 類別以下針對這些用途，但不是建議。 如果您需要實作類似的功能，MFC 原始碼 （尤其是就地啟用），就會是絕佳的參考，來處理一些重點 OLE。

## <a name="examine-the-mfc-sample-code"></a>檢查 MFC 範例程式碼

有多個包含 OLE 功能的 MFC 範例。 每個應用程式會實作 OLE 從不同的角度：

- [HIERSVR](../overview/visual-cpp-samples.md)大部分用於做為伺服器應用程式。 已包含在 MFC 2.0 為 MFC/OLE1 應用程式和先前已經移植到 MFC/OLE 2，然後擴充，它會實作 OLE 2 中提供的許多 OLE 功能。

- [OCLIENT](../overview/visual-cpp-samples.md)這是獨立的容器應用程式，用來從容器的觀點來看示範許多 OLE 功能。 它也移植從 MFC 2.0，然後延伸以支援許多更進階的 OLE 功能，例如自訂剪貼簿格式以及內嵌項目連結。

- [DRAWCLI](../overview/visual-cpp-samples.md)此應用程式會實作 OLE 容器支援更像 OCLIENT 一樣，不同之處在於它會在現有的物件導向繪圖程式架構內。 它會顯示如何實作 OLE 容器支援和它整合至現有的應用程式。

- [SUPERPAD](../overview/visual-cpp-samples.md)此應用程式，以及細緻的獨立應用程式，也是 OLE 伺服器。 它會實作的伺服器支援是相當的極簡。 特別值得注意的是如何將資料複製到剪貼簿，使用 OLE 剪貼簿 服務，但會使用內建在 Windows 編輯 控制項的功能，來實作剪貼簿貼上功能。 這會顯示有趣混合傳統的 Windows API 使用方式，以及與新 OLE Api 整合。

如需有關範例應用程式的詳細資訊，請參閱 「 MFC 範例說明 」。

## <a name="case-study-oclient-from-mfc-20"></a>案例研究：從 MFC 2.0 OCLIENT

與上述[OCLIENT](../overview/visual-cpp-samples.md) MFC 2.0 中所包含而且實作與 MFC/OLE1 OLE。 如下所述的步驟，供此應用程式一開始已轉換成使用 MFC/OLE 2 類別。 為了更清楚說明 MFC/OLE 類別完成的初始連接埠後，已新增許多功能。 這些功能將不說明如需有關這些進階功能本身的範例，請參閱。

> [!NOTE]
> 編譯器錯誤和逐步程序已建立具有視覺效果C++2.0。 特定的錯誤訊息和位置，可能具有視覺效果中已變更C++4.0 中，但提供的概念性資訊仍然有效。

## <a name="getting-it-up-and-running"></a>快速安裝和執行

移植到 MFC/OLE OCLIENT 範例採用的方法是從開始建置它，並修正會造成明顯的編譯器錯誤。 如果您需要 OCLIENT 範例 MFC 2.0，並編譯這個版本的 MFC 下，您會發現，並不會顯示那麼多的錯誤，以解決。 如下所述以其發生順序錯誤。

## <a name="compile-and-fix-errors"></a>編譯與修正錯誤

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

第一個錯誤考量`COleClientItem::Draw`。 MFC/OLE1 花費比 MFC/OLE 版本需要更多的參數。 額外的參數則通常不必要的而且通常為 NULL （如此範例所示）。 這個 MFC 版本中繼檔 DC 所要繪製的 CDC 時，可以自動判斷 lpWBounds 的值。 颾魤 ㄛ pFormatDC 參數不再需要因為架構會建立一個從 「 屬性 DC 」 的傳入 pDC。 因此若要修正此問題，您只要移除這兩個額外的繪製呼叫的參數為 NULL。

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

上述結果的錯誤，所有`COleClientItem::CreateXXXX`MFC/OLE1 中的函式所需的唯一名稱會傳遞至代表項目。 這是基礎 OLE API 的需求。 這是不必要的 MFC/OLE 2，因為 OLE 2 不會使用 DDE 做為基礎的通訊機制 （名稱 DDE 交談中所使用）。 若要修正此問題，您可以移除`CreateNewName`函式以及它的所有參考。 它很容易了解每個 MFC/OLE 函數需要的內容在這個版本中只要將游標放在呼叫，然後按下 f1 鍵。

另一個完全不同的區域是 OLE 2 剪貼簿處理。 OLE1，取代為您使用 Windows 剪貼簿 Api 互動使用剪貼簿。 OLE 2 做法是使用不同的機制。 MFC/OLE1 Api 假設剪貼簿複製之前已開啟`COleClientItem`到剪貼簿的物件。 這已不再需要，並會導致所有 MFC/OLE 剪貼簿作業失敗。 當您編輯程式碼以移除相依性上`CreateNewName`，您也應該移除的程式碼，開啟及關閉 Windows 剪貼簿。

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

這些錯誤會造成從`CMainView::OnInsertObject`處理常式。 處理 「 插入新物件 」 命令是另一個項目已稍微變更。 在此情況下，它是最簡單的方式只需使用新的 OLE 容器應用程式提供 appwizard 合併的原始實作。 事實上，這是一種技術，您可以套用至移植其他應用程式。 您可以在 MFC/OLE1，顯示 「 插入的物件 」 對話方塊來藉由呼叫`AfxOleInsertDialog`函式。 在您建構在此版本`COleInsertObject`對話方塊中的物件，然後呼叫`DoModal`。 此外，與建立新的 OLE 項目**CLSID**而不是類別名稱的字串。 最後的結果應該看起來像這樣

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> 插入新的物件可能會不同應用程式）：

就也必須包含\<afxodlgs.h >，其中包含的宣告`COleInsertObject`對話方塊類別，以及其他 MFC 提供的標準對話方塊。

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

這些錯誤會引起某些 OLE1 常數已變更為 OLE 2 中，即使它們是相同的概念。 在此情況下`OLEVERB_PRIMARY`已變更為`OLEIVERB_PRIMARY`。 在 OLE1 和 OLE 2 中，主要的動詞命令通常執行容器當使用者按兩下項目上。

颾魤 ㄛ`DoVerb`現在採用額外的參數 — 檢視的指標 (`CView`*)。 此參數只用來實作 「 視覺化編輯 」 （或就地啟用）。 現在因為您不會實作這項功能，這一次 」，該參數設為 NULL。

若要確定，framework 永遠不會嘗試進行就地啟用，您應該覆寫`COleClientItem::CanActivate`，如下所示：

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

在 MFC/OLE1，`COleClientItem::GetBounds`並`SetBounds`用來查詢及操作的項目範圍 (`left`和`top`成員永遠是零)。 在 MFC/OLE 2 這更直接支援`COleClientItem::GetExtent`並`SetExtent`，其中應付**大小**或`CSize`改為。

您的新 SetItemRectToServer 的程式碼和 UpdateItemRectFromServer 呼叫看起來像這樣：

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

MFC/OLE1 同步 API 中所呼叫的伺服器從容器*模擬*，因為 OLE1 已在許多情況下本質上是非同步。 必須處理來自使用者的命令之前，先檢查進行中的未處理的非同步呼叫動作。 提供的 MFC/OLE1`COleClientItem::InWaitForRelease`這樣的函式。 在 MFC/OLE 2 這不需要，讓您可以一起 CMainFrame 中移除的 OnCommand 覆寫。

此時 OCLIENT 會編譯及連結。

## <a name="other-necessary-changes"></a>其他必要的變更

有幾件事，不會完成，會保留 OCLIENT 執行，不過。 最好是修正這些問題，現在而不是更新版本。

首先，就必須初始化 OLE 程式庫。 這是藉由呼叫`AfxOleInit`從`InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

它也是個不錯的主意，若要檢查有虛擬函式的參數清單的變更。 一個這類函式是`COleClientItem::OnChange`、 覆寫每個 MFC/OLE 容器應用程式中。 藉由查看線上說明，您會看到已新增額外 'DWORD dwParam'。 新的 CRectItem::OnChange 如下所示：

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

在 MFC/OLE1，容器應用程式的衍生來源的文件類別`COleClientDoc`。 MFC/OLE 2 中這個類別已移除，並取代`COleDocument`（這個新的組織更輕鬆地建置容器/伺服器應用程式）。 沒有 **#define**存取子可對應`COleClientDoc`到`COleDocument`簡化移植到 MFC/OLE 2，例如 OCLIENT 的 MFC/OLE1 應用程式。 未提供的功能之一`COleDocument`藉由提供`COleClientDoc`是標準命令訊息對應項目。 這會完成該伺服器應用程式，也使用`COleDocument`（間接），不含與他們這些命令處理常式的額外負荷除非它們是容器/伺服器應用程式。 您需要下列項目新增至 CMainDoc 訊息對應：

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

所有這些命令的實作是採用`COleDocument`，這是您的文件的基底類別。

此時，OCLIENT 是功能的 OLE 容器應用程式。 可以插入 （OLE1 或 OLE 2） 的任何類型的項目。 因為未實作必要的程式碼，以便在就地啟用，在類似 OLE1 與另一個視窗中編輯項目。 下節會討論必要的變更，以啟用就地編輯 （有時稱為 「 視覺化編輯 」）。

## <a name="adding-visual-editing"></a>新增 「 視覺化編輯 」

OLE 的最有趣的功能之一是就地啟用 （或 「 視覺化編輯 」）。 這項功能可讓伺服器應用程式，以便透過部分容器的使用者介面來為使用者提供更順暢的編輯介面。 若要實作 OCLIENT 就地啟用，一些特殊的資源需要新增，以及一些額外的程式碼。 這些資源和程式碼通常由 AppWizard 所提供，事實上，大部分的程式碼取自直接透過 「 容器 」 支援的全新 AppWizard 應用程式。

首先，就必須新增功能表資源，也就是就地啟用作用中的項目時使用。 您可以在視覺效果中的這項額外的功能表資源C++複製 IDR_OCLITYPE 資源，並移除以外的所有檔案和視窗快顯視窗。 表示群組的分隔的檔案和視窗快顯之間插入兩個分隔線 (看起來應該像：檔案&#124;&#124;視窗中)。 如需有關這些分隔符號所代表的意義，以及如何合併伺服器和容器的功能表看到[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

建立這些功能表之後，您需要讓架構知道它們。 這是藉由呼叫`CDocTemplate::SetContainerInfo`才能將它加入文件範本清單中您的設定加入 InitInstance 中的文件範本。 新的程式碼，以註冊文件範本看起來像這樣：

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

IDR_OLECLITYPE_INPLACE 資源是建立視覺效果中的特殊就地資源C++。

若要啟用在就地啟用，有幾個步驟，需要在兩者中變更`CView`(CMainView) 衍生的類別，以及`COleClientItem`衍生類別 (CRectItem)。 所有這些覆寫由 AppWizard 提供，其中大部分的實作都是直接來自預設 AppWizard 應用程式。

在此連接埠的第一個步驟中，就地啟用已停用完全是藉由覆寫`COleClientItem::CanActivate`。 應移除此覆寫，以允許就地啟用。 此外，所有呼叫傳遞 NULL `DoVerb` （有兩個） 因為提供的檢視時才需要進行就地啟用。 若要完全實作就地啟用，就必須將正確的檢視中`DoVerb`呼叫。 這些呼叫的其中一個是`CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

另一個範例是`CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

必須覆寫`COleClientItem::OnGetItemPosition`。 這會告訴伺服器要放置它的視窗相對於容器的視窗，項目時就地啟用。 OCLIENT，實作便微不足道的：

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

大部分的伺服器也會實作稱為 「 就地調整大小。 」 這可讓伺服器視窗調整大小並移動時使用者編輯的項目。 容器必須參與此動作，因為移動或調整視窗大小通常會影響在容器文件本身的大小與位置。 OCLIENT 實作同步處理內部維護 m_rect 以新的位置和大小的矩形。

```cpp
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

到目前為止，沒有足夠的程式碼，以允許的項目，即可就地啟用，並處理調整大小和移動項目處於作用中狀態，但沒有程式碼可讓使用者編輯的工作階段的結束。 雖然某些伺服器將會提供這項功能自行處理 esc 鍵，它被建議的容器會提供兩種方式可停用項目：（1） 所按一下的項目之外和 （2） 藉由按下 ESC 鍵。

逸出索引鍵，加入 視覺效果加速器C++命令對應 VK_ESCAPE 鍵，ID_CANCEL_EDIT 會新增至資源。 此命令的處理常式如下：

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

若要處理的情況，以便使用者按一下項目之外，您必須新增下列程式碼的開頭`CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

就地啟用作用中的項目時，應該有焦點。 若要確保此情況下您會處理 OnSetFocus，讓您檢視取得焦點時一律焦點轉移到作用中的項目：

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

當檢視調整大小時，您需要通知的作用中的項目已變更的裁剪方框。 若要這樣做您提供的處理常式`OnSize`:

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>案例研究：從 MFC 2.0 HIERSVR

[HIERSVR](../overview/visual-cpp-samples.md)也包含在 MFC 2.0 和實作使用 MFC/OLE1 OLE。 本附註簡要說明的步驟，供此應用程式一開始已轉換成使用 MFC/OLE 2 類別。 為了更清楚說明 MFC/OLE 2 類別完成的初始連接埠後，已新增許多功能。 這些功能將不說明如需有關這些進階功能本身的範例，請參閱。

> [!NOTE]
> 編譯器錯誤和逐步程序已建立具有視覺效果C++2.0。 特定的錯誤訊息和位置，可能具有視覺效果中已變更C++4.0 中，但提供的概念性資訊仍然有效。

## <a name="getting-it-up-and-running"></a>快速安裝和執行

移植到 MFC/OLE HIERSVR 範例採用的方法是從開始建置它，並修正會造成明顯的編譯器錯誤。 如果您需要 HIERSVR 範例 MFC 2.0，並編譯這個版本的 MFC 下，您會發現，並不會顯示多錯誤，無法解析 （雖然有多個與 OCLIENT 範例）。 其通常出現的順序中的錯誤如下所述。

## <a name="compile-and-fix-errors"></a>編譯與修正錯誤

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

此第一個錯誤指出是什麼大問題與`InitInstance`函式的伺服器。 OLE 伺服器所需的初始化可能是其中一個最大的變更，您必須對您的 MFC/OLE1 應用程式開始執行。 最佳做法是查看 AppWizard 建立的 OLE 伺服器，並修改為適當的程式碼。 以下是一些要牢記在心的事項：

就必須呼叫以初始化 OLE 程式庫 `AfxOleInit`

設定伺服器資源控制代碼，您無法使用設定的執行階段類別資訊的文件範本物件上呼叫 SetServerInfo`CDocTemplate`建構函式。

如果命令列上存在 /Embedding，則不會顯示您的應用程式的主視窗。

您將需要**GUID**文件。 這是您的文件類型 （128 位元） 的唯一識別碼。 AppWizard 將會為您建立一個，因此如果您使用這裡所描述的技術將新的程式碼複製新產生的 AppWizard 伺服器應用程式，您可以只是 「 竊取 」 從該應用程式的 GUID。 如果沒有，您可以使用 GUIDGEN。EXE 公用程式的 BIN 目錄中。

需要 「 連線 」 您`COleTemplateServer`物件至文件範本，藉由呼叫`COleTemplateServer::ConnectTemplate`。

當單獨執行您的應用程式時，請更新系統登錄。 如此一來，如果使用者移。EXE 應用程式，從其新位置執行將會更新為 Windows 系統註冊資料庫，以指向新的位置。

在套用所有根據 AppWizard 建立的這些變更後`InitInstance`，則`InitInstance`（及相關的 GUID） HIERSVR 應該讀取，如下所示：

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

您會發現，上述程式碼指的是新的資源 ID、 IDR_HIERSVRTYPE_SRVR_EMB。 這是編輯內嵌在另一個容器中的文件時要使用的功能表資源。 在 MFC/OLE1 編輯內嵌項目特定的功能表項目已修改即時。 編輯內嵌項目，而不是編輯檔案為基礎的文件時，使用完全不同的功能表結構讓您更容易地提供這兩種不同模式的不同的使用者介面。 如稍後所見，編輯內嵌的物件就地時，就會會使用完全不同的功能表資源。

若要建立此資源，請載入資源指令碼視覺效果C++並複製現有的 IDR_HIERSVRTYPE 功能表資源。 將新的資源重新命名的 IDR_HIERSVRTYPE_SRVR_EMB （這是 AppWizard 使用相同的命名慣例）。 接下來將變更 [儲存檔案] [更新檔案];提供識別碼 ID_FILE_UPDATE 命令。 也變更 」 檔案另存新檔 」 到 「 複本存新檔 」;提供識別碼 ID_FILE_SAVE_COPY_AS 命令。 架構會提供這兩種命令的實作。

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

有數個錯誤所產生的覆寫`OnSetData`，因為它指**OLESTATUS**型別。 **OLESTATUS**已 OLE1 傳回錯誤的方式。 這已變更為**HRESULT**在 OLE 2 中，雖然通常將 MFC **HRESULT**到`COleException`包含錯誤。 在這個特定的情況下，用來覆寫`OnSetData`不再需要，因此最簡單的做法是將它移除。

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem`建構函式會採用額外的 'BOOL' 參數。 這個旗標決定記憶體管理會對`COleServerItem`物件。 藉由將它設定為 TRUE，架構會處理這些物件的記憶體管理，就不再需要時，請刪除它們。 使用 HIERSVR `CServerItem` (衍生自`COleServerItem`) 做為其原生資料，因此您會設定這個旗標設為 FALSE 的一部分的物件。 這可讓 HIERSVR 判斷每個伺服器項目刪除時。

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

依照這些錯誤提示，有一些擁有尚未被覆寫 CServerItem 中的 '純虛擬的' 函式。 很可能這種情形因 OnDraw 的參數清單已變更的事實。 若要修正這個錯誤，變更`CServerItem::OnDraw`，如下所示 （以及 svritem.h 中的宣告）：

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

新的參數是 'rsize 則'。 這可讓您填入的繪圖，大小如果方便。 此大小必須是**HIMETRIC**。 在此情況下，並不方便以填滿此值，因此，架構會呼叫`OnGetExtent`来擷取之範圍內。 為此工作，您必須實作`OnGetExtent`:

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

CServerItem::CalcNodeSize 函式中的項目大小會轉換成**HIMETRIC**並儲存在*m_rectBounds*。 未記載 '*m_rectBounds*' 的成員`COleServerItem`不存在 (已部分取代成所*m_sizeExtent*，但為 OLE 2 這個成員已經稍有不同的使用方式比*m_rectBounds* OLE1 中)。 而不是設定**HIMETRIC**大小到此成員變數中，您會將它傳回。 這個傳回值會在`OnGetExtent`先前實作。

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem 也會覆寫`COleServerItem::OnGetTextData`。 此函式 MFC/OLE 中已過時，並由不同的機制來取代。 MFC OLE 範例 MFC 3.0 版[HIERSVR](../overview/visual-cpp-samples.md)實作這項功能，藉由覆寫`COleServerItem::OnRenderFileData`。 讓您可以移除 OnGetTextData 覆寫，並不重要的這個基本的連接埠，這項功能。

有更多的錯誤 svritem.cpp 中，尚未處理。 它們不是 「 真實 」 的錯誤 — 只要先前的錯誤所造成的錯誤。

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` 不再支援`bIncludeNative`旗標。 一律複製原生資料 （資料寫出的伺服器項目的序列化函式），讓您移除第一個參數。 颾魤 ㄛ`CopyToClipboard`而不是傳回 FALSE，發生錯誤時將會擲回例外狀況。 變更程式碼的 CServerView::OnEditCopy 如下所示：

```cpp
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

雖然沒有比有個相同版本的 OCLIENT HIERSVR MFC 2.0 版的編譯所產生的多個錯誤，但沒有實際更少的變更。

此時 HIERSVR 會編譯和連結和函式為 OLE 伺服器，但未在就地編輯功能，接下來將會實作。

## <a name="adding-visual-editing"></a>新增 「 視覺化編輯 」

若要加入此伺服器應用程式的 「 視覺編輯 」 （或就地啟用），有只有幾件事您必須負責：

- 您需要的項目是就地啟用作用中時所要使用特殊功能表資源。

- 此應用程式會有工具列上，因此您必須具有只是一般的工具列，以符合的功能表命令可從伺服器 （符合先前所述的功能表資源） 的子集的工具列。

- 您需要新的類別衍生自`COleIPFrameWnd`提供就地使用者介面 (就像是 CMainFrame，衍生自`CMDIFrameWnd`，提供的 MDI 使用者介面)。

- 您需要告訴這些特殊的資源和類別的架構。

功能表資源很容易建立。 執行視覺效果C++，將 IDR_HIERSVRTYPE 功能表資源複製到名為 IDR_HIERSVRTYPE_SRVR_IP 的功能表資源。 修改 [] 功能表中，以便只編輯和說明功能表快顯視窗會保留。 編輯 和 說明功能表之間的功能表中加入兩個分隔符號 (看起來應該像：編輯&#124;&#124;協助)。 如需有關這些分隔符號所代表的意義，以及如何合併伺服器和容器的功能表的詳細資訊，請參閱[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

藉由勾選 [伺服器] 選項複製其中一個全新的 AppWizard 產生應用程式，可以輕鬆建立子集工具列的點陣圖。 此點陣圖可以再匯入到視覺效果C++。 請務必提供點陣圖 IDR_HIERSVRTYPE_SRVR_IP 識別碼。

類別衍生自`COleIPFrameWnd`可以從 AppWizard 產生應用程式與伺服器的支援，以及複製。 複製這兩個檔案，IPFRAME。CPP 和 IPFRAME。H 並將其新增至專案。 請確定`LoadBitmap`呼叫是指 IDR_HIERSVRTYPE_SRVR_IP，在上一個步驟中建立的點陣圖。

現在會建立所有新的資源和類別，新增必要的程式碼，讓架構知道這些 （並知道此應用程式現在支援就地編輯）。 這是藉由加入一些更多的參數，以`SetServerInfo`呼叫中`InitInstance`函式：

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

現在已經準備好執行就地也支援就地啟用任何容器中。 但是，沒有仍然內部程式碼中的一個重大錯誤。 HIERSVR 支援操作功能表中，當使用者按下滑鼠右按鈕時顯示。 HIERSVR 完全開啟，但編輯內嵌就地時無法運作時，適用於此功能表。 原因可以向下釘選到這一行 CServerView::OnRButtonDown 中的程式碼：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

請注意參考`AfxGetApp()->m_pMainWnd`。 就地啟用的伺服器時，會有主視窗和設定 m_pMainWnd，但它是通常是不可見。 此外，此視窗是指*主要* 視窗中的應用程式，MDI 框架視窗所顯示的伺服器時完全開啟或執行獨立。 它不是指使用中框架視窗，其中就地啟動時，框架視窗衍生自`COleIPFrameWnd`。 若要取得正確的使用中視窗，就地編輯，此版本的 MFC 將加入新的函式，即使`AfxGetMainWnd`。 一般而言，您應該使用此函式，而不是`AfxGetApp()->m_pMainWnd`。 此程式碼需要變更，如下所示：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

現在您已至少啟用以供功能就地啟動 OLE 伺服器。 但仍有許多功能，適用於無法使用 MFC/OLE1 的 MFC/OLE 2。 您可能想要實作的功能，請參閱更多想法 HIERSVR 範例。 以下列出一些 HIERSVR 實作的功能：

- 縮放的容器而言，則為 true WYSIWYG 行為。

- 拖放及自訂剪貼簿格式。

- 捲動與選取範圍的 [容器] 視窗會變更。

HIERSVR 中的範例 MFC 3.0 也會使用其伺服器項目稍有不同的設計。 這有助於節省記憶體，並讓您的連結更有彈性。 HIERSVR 2.0 版在樹狀目錄中的每個節點*是* `COleServerItem`。 `COleServerItem` 會帶來更多的額外負荷比是絕對必要，每個這些節點，但`COleServerItem`需要為每個作用中的連結。 但大部分的情況下，有極少數的作用中連結在任何指定時間。 若要使這個更有效率，在這個版本的 MFC HIERSVR 分隔節點從`COleServerItem`。 它有兩個 CServerNode 和`CServerItem`類別。 `CServerItem` (衍生自`COleServerItem`) 才會建立為必要。 一旦容器 （或容器） 停止使用該特定連結到該特定節點，會刪除 CServerNode 相關聯的 CServerItem 物件。 這項設計會更有效率且更有彈性。 它的彈性有多個選取項目連結處理時。 HIERSVR 下列兩個版本都不支援多個選取的項目，但它會更容易新增 （及支援這類的選取項目連結） HIERSVR，MFC 3.0 版因為`COleServerItem`分開的原生的資料。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
