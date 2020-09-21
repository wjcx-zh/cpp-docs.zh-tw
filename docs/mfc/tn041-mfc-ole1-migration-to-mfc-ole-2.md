---
title: TN041： MFC-OLE1 遷移至 MFC-OLE 2
ms.date: 10/18/2018
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
ms.openlocfilehash: 7d0381983481278b1410ae0ff11463519d4cbb34
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743148"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041：MFC/OLE1 移轉到 MFC/OLE 2

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

## <a name="general-issues-relating-to-migration"></a>與遷移相關的一般問題

在 MFC 2.5 (和) 更高版本中，OLE 2 類別的其中一個設計目標，就是要保留大部分的相同架構，以供 OLE 1.0 支援的 MFC 2.0 中放置。 如此一來，MFC 2.0 中許多相同的 OLE 類別仍會存在於此版本的 MFC (`COleDocument` 、 `COleServerDoc` 、 `COleClientItem` `COleServerItem`) 。 此外，這些類別中的許多 Api 都完全相同。 不過，OLE 2 與 OLE 1.0 截然不同，因此您可以預期部分詳細資料已變更。 如果您熟悉 MFC 2.0 的 OLE1 支援，您將可在家裡找到 MFC 的2.0 支援。

如果您正在使用現有的 MFC/OLE1 應用程式，並在其中新增 OLE 2 功能，您應該先閱讀此附注。 本附注涵蓋一些您可能會在將 OLE1 功能移植到 MFC/OLE 2 時遇到的一般問題，並討論在移植 MFC 2.0 中包含的兩個應用程式時所發現的問題： MFC OLE samples [OCLIENT](../overview/visual-cpp-samples.md) 和 [HIERSVR](../overview/visual-cpp-samples.md)。

## <a name="mfc-documentview-architecture-is-important"></a>MFC 檔/視圖架構很重要

如果您的應用程式不使用 MFC 的檔/視圖架構，而您想要將 OLE 2 支援新增至您的應用程式，現在就是移至 [檔]/[視圖] 的時間。 MFC 的 OLE 2 類別的許多優點只會在應用程式使用 MFC 的內建架構和元件之後才會實現。

在不使用 MFC 架構的情況下執行伺服器或容器是可行的，但不建議使用。

## <a name="use-mfc-implementation-instead-of-your-own"></a>使用 MFC 執行，而不是您自己的

MFC 「預先設計的實作為」類別（例如 `CToolBar` 、 `CStatusBar` 和） `CScrollView` 有內建的 OLE 2 支援的特殊案例代碼。 因此，如果您可以在應用程式中使用這些類別，您將受益于將這些類別放入這些類別，使其成為 OLE 感知。 同樣地，您可以在這裡為這些用途「自行匯總」類別，但不建議這麼做。 如果您需要執行類似的功能，MFC 原始程式碼是處理一些 OLE (的絕佳參考，特別是在就地啟用時) 。

## <a name="examine-the-mfc-sample-code"></a>檢查 MFC 範例程式碼

有一些 MFC 範例包含 OLE 功能。 這些應用程式中的每一個都是從不同的角度來實行 OLE：

- [HIERSVR](../overview/visual-cpp-samples.md) 主要是用來做為伺服器應用程式。 它是以 mfc/OLE1 應用程式的形式包含在 MFC 2.0 中，並且已移植到 MFC/OLE 2，然後擴充，使其得以在 OLE 2 中提供許多 OLE 功能。

- [OCLIENT](../overview/visual-cpp-samples.md) 這是獨立的容器應用程式，目的是要示範容器觀點的許多 OLE 功能。 它也是從 MFC 2.0 移植，然後擴充以支援許多較先進的 OLE 功能，例如自訂剪貼簿格式和內嵌專案的連結。

- [DRAWCLI](../overview/visual-cpp-samples.md) 此應用程式的執行方式與 OCLIENT 相同，不同之處在于它是在現有物件導向繪圖程式的架構內執行。 它會示範如何執行 OLE 容器支援，並將其整合到現有的應用程式中。

- [SUPERPAD](../overview/visual-cpp-samples.md) 此應用程式也是一個良好的獨立應用程式，也是 OLE 伺服器。 它所實行的伺服器支援相當極簡。 特別重要的是，它如何使用 OLE 剪貼簿服務將資料複製到剪貼簿，但使用 Windows "edit" 控制項內建的功能來執行剪貼簿貼上功能。 這會顯示傳統 Windows API 使用方式的有趣混合，以及與新的 OLE Api 的整合。

如需範例應用程式的詳細資訊，請參閱「MFC 範例說明」。

## <a name="case-study-oclient-from-mfc-20"></a>案例研究：從 MFC 2.0 OCLIENT

如前文所述， [OCLIENT](../overview/visual-cpp-samples.md) 已包含在 mfc 2.0 中，並使用 MFC/OLE1 來執行 OLE。 此應用程式最初轉換成使用 MFC/OLE 2 類別的步驟如下所述。 在完成初始埠之後加入了許多功能，以更清楚地說明 MFC/OLE 類別。 此處將不會涵蓋這些功能;如需這些 advanced 功能的詳細資訊，請參閱範例本身。

> [!NOTE]
> 編譯器錯誤和逐步執行程式是使用 Visual C++ 2.0 所建立。 特定的錯誤訊息和位置在 Visual C++ 4.0 中可能已變更，但概念資訊仍然有效。

### <a name="getting-it-up-and-running"></a>正在啟動並執行

將 OCLIENT 範例移植到 MFC/OLE 所採取的方法是先建立它，並修正將產生的明顯編譯器錯誤。 如果您採用 MFC 2.0 的 OCLIENT 範例，並在這個版本的 MFC 下進行編譯，您會發現沒有要解決的錯誤。 錯誤的發生順序如下所述。

### <a name="compile-and-fix-errors"></a>編譯和修正錯誤

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

第一個錯誤問題 `COleClientItem::Draw` 。 在 MFC/OLE1 中，它所花費的參數多於 MFC/OLE 版本所採用的參數。 額外的參數通常不是必要的，而且通常是 Null (，如下列範例所示) 。 當要繪製的 CDC 是中繼檔 DC 時，這個版本的 MFC 可以自動決定 lpWBounds 的值。 此外，您不再需要 pFormatDC 參數，因為架構會從所傳入 pDC 的「屬性 DC」建立一個參數。 為了修正此問題，您只要移除繪製呼叫的兩個額外的 Null 參數。

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

上述錯誤是因為 `COleClientItem::CreateXXXX` MFC/OLE1 中的所有函數都需要傳遞唯一的名稱來代表專案。 這是基礎 OLE API 的需求。 MFC/OLE 2 中不需要這麼做，因為 OLE 2 不使用 DDE 做為基礎通訊機制， (名稱是在 DDE 交談) 中使用。 若要修正這個問題，您可以移除函式以及 `CreateNewName` 對它的所有參考。 只要將游標放在呼叫上，然後按下 F1，就可以輕鬆地瞭解每個 MFC/OLE 函數在此版本中預期的內容。

另一個截然不同的地方是 OLE 2 剪貼簿處理。 使用 OLE1，您可以使用 Windows 剪貼簿 Api 與剪貼簿互動。 使用 OLE 2 時，會以不同的機制來完成。 MFC/OLE1 Api 會在將物件複製到剪貼簿之前，假設剪貼簿已開啟 `COleClientItem` 。 這已不再是必要的，而且會導致所有 MFC/OLE 剪貼簿作業失敗。 當您編輯程式碼以移除的相依性時 `CreateNewName` ，您也應該移除開啟和關閉 [Windows 剪貼簿] 的程式碼。

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

這些錯誤的結果是 `CMainView::OnInsertObject` 處理常式。 處理「插入新物件」命令是另一個已變更專案的地方。 在這種情況下，只需將原始的實合併為新的 OLE 容器應用程式的執行程式所提供的，是最簡單的做法。 事實上，這是您可以套用來移植其他應用程式的技術。 在 MFC/OLE1 中，您可以藉由呼叫函數來顯示 [插入物件] 對話方塊 `AfxOleInsertDialog` 。 在此版本中，您會建立 `COleInsertObject` 對話方塊物件並呼叫 `DoModal` 。 此外，新的 OLE 專案是使用 **CLSID** 而非 classname 字串所建立。 最終結果看起來應該像這樣

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
> 針對您的應用程式) 插入新的物件可能不同：

您也必須包含 \<afxodlgs.h> ，其中包含對話方塊類別的宣告，以及 `COleInsertObject` MFC 提供的其他標準對話方塊。

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

這些錯誤的原因是某些 OLE1 常數在 OLE 2 中已變更，即使概念相同也一樣。 在此案例中 `OLEVERB_PRIMARY` ，已變更為 `OLEIVERB_PRIMARY` 。 在 OLE1 和 OLE 2 中，當使用者按兩下專案時，主要動詞通常會由容器執行。

此外， `DoVerb` 現在會採用額外的參數，也就是 (* ) 的視圖指標 `CView` 。 此參數只會用來執行「視覺化編輯」 (或就地啟用) 。 現在您可以將該參數設定為 Null，因為您目前未執行這項功能。

若要確定架構永遠不會嘗試就地啟用，您應覆寫如下 `COleClientItem::CanActivate` ：

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

在 MFC/OLE1 中， `COleClientItem::GetBounds` 以及 `SetBounds` 用來查詢和操作專案的範圍 (， `left` 且 `top` 成員一律為零) 。 在 MFC/OLE 2 中，和可以直接支援這種方式 `COleClientItem::GetExtent` `SetExtent` ，也就是處理 **大小** 或 `CSize` 。

新 SetItemRectToServer 和 UpdateItemRectFromServer 呼叫的程式碼看起來像這樣：

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

在 MFC/OLE1 中，從容器到伺服器的同步 API 呼叫已 *模擬*，因為在許多情況下，OLE1 原本就是非同步。 在處理來自使用者的命令之前，必須先檢查是否有未完成的非同步呼叫正在進行中。 MFC/OLE1 提供了此 `COleClientItem::InWaitForRelease` 功能。 在 MFC/OLE 2 中，這並不是必要的，因此您可以同時移除 CMainFrame 中的 OnCommand 覆寫。

此時 OCLIENT 會進行編譯和連結。

### <a name="other-necessary-changes"></a>其他必要的變更

但是，不會有幾件事會讓 OCLIENT 維持執行狀態。 最好是立即修正這些問題，而不是稍後修正。

首先，必須初始化 OLE 程式庫。 這是藉由呼叫下列方法來完成 `AfxOleInit` `InitInstance` ：

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

檢查是否有參數清單變更的虛擬函式也是個不錯的主意。 `COleClientItem::OnChange`在每個 MFC/OLE 容器應用程式中，會覆寫其中一個這類函數。 藉由查看線上說明，您會看到已新增額外的 ' DWORD dwParam '。 新的 CRectItem：： OnChange 看起來如下：

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

在 MFC/OLE1 中，容器應用程式會從衍生檔類別 `COleClientDoc` 。 在 MFC/OLE 2 中，此類別已移除，並由 `COleDocument` (這個新的組織所取代，讓您更輕鬆地建立容器/伺服器應用程式) 。 有一個對應至的 **#define** ， `COleClientDoc` `COleDocument` 可簡化 mfc/OLE1 應用程式移植至 mfc/OLE 2 的移植，例如 OCLIENT。 提供的其中一 `COleDocument` `COleClientDoc` 項功能是標準命令訊息對應專案。 這麼做是為了讓也使用 (間接) 的伺服器應用程式 `COleDocument` 不會將這些命令處理常式的額外負荷帶到它們，除非它們是容器/伺服器應用程式。 您必須將下列專案新增至 CMainDoc 訊息對應：

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

所有這些命令的執行都是在中 `COleDocument` ，也就是檔的基類。

此時，OCLIENT 是一個功能 OLE 容器應用程式。 您可以將任何類型的專案插入 (OLE1 或 OLE 2) 。 由於啟用就地啟用的必要程式碼不會執行，因此在不同的視窗中編輯專案的方式與 OLE1 非常類似。 下一節將討論啟用就地編輯 (的必要變更，有時也稱為「視覺化編輯」 ) 。

### <a name="adding-visual-editing"></a>新增「視覺化編輯」

OLE 的其中一個最有趣的功能是就地啟用 (或「視覺化編輯」 ) 。 這項功能可讓伺服器應用程式接管容器的部分使用者介面，為使用者提供更順暢的編輯介面。 若要將就地啟用實 OCLIENT，必須新增一些特殊的資源，以及一些額外的程式碼。 這些資源和程式碼通常是由程式碼提供者所提供，事實上，這裡的大部分程式碼都是直接從全新的執行程式應用程式中，使用「容器」支援來借用。

首先，必須新增功能表資源，以便在具有就地使用中的專案時使用。 您可以複製識別碼R_OCLITYPE 資源並移除所有檔案和視窗快顯，以在 Visual C++ 中建立這個額外的功能表資源。 在 [檔案] 和 [視窗] 快顯視窗之間插入兩個分隔線，以表示分隔群組 (看起來像這樣： [檔案 &#124;&#124; 視窗) 。 如需這些分隔符號的意義，以及如何合併伺服器和容器功能表的詳細資訊，請參閱功能表 [和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

建立好這些功能表之後，您需要讓架構知道它們。 這是藉由呼叫 `CDocTemplate::SetContainerInfo` 檔範本來完成，然後再將它加入至 InitInstance 中的檔範本清單。 註冊檔範本的新程式碼看起來像這樣：

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

IDR_OLECLITYPE_INPLACE 資源是在 Visual C++ 中建立的特殊就地資源。

若要啟用就地啟用， `CView` (CMainView) 衍生類別以及 `COleClientItem` 衍生類別 (CRectItem) 中有一些需要變更的專案。 所有這些覆寫都是由應用程式提供者所提供，大部分的執行都會直接來自預設的執行程式應用程式。

在此埠的第一個步驟中，就地啟用已透過覆寫完全停用 `COleClientItem::CanActivate` 。 應移除此覆寫以允許就地啟用。 此外， `DoVerb` 也會將 Null 傳遞給 (有兩個) ，因為只有在就地啟用時才需要提供視圖。 若要完全實行就地啟用，必須在呼叫中傳遞正確的視圖 `DoVerb` 。 其中一個呼叫位於 `CMainView::OnInsertObject` ：

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

另一種是 `CMainView::OnLButtonDblClk` ：

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

必須覆寫 `COleClientItem::OnGetItemPosition` 。 這會告訴伺服器在專案啟用時，要將視窗相對於容器視窗的放置位置。 針對 OCLIENT，此實作為簡單：

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

大部分的伺服器也會執行所謂的「就地調整大小」。 如此一來，當使用者編輯專案時，伺服器視窗就會調整大小及移動。 容器必須參與這個動作，因為移動或調整視窗大小時，通常會影響容器檔案本身內的位置和大小。 OCLIENT 的執行會將 m_rect 所維護的內部矩形與新的位置和大小進行同步處理。

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

此時，有足夠的程式碼可讓專案就地啟用，以及處理調整大小，並在專案作用時進行移動，但沒有任何程式碼可讓使用者離開編輯會話。 雖然某些伺服器會藉由處理 escape 按鍵提供這項功能，但建議容器提供兩種方式來停用專案： (1) ，方法是在專案外按一下，然後按下 ESC 鍵 (2) 。

針對 ESCAPE 按鍵，新增具有 Visual C++ 的加速器，將 VK_ESCAPE 索引鍵對應至命令，ID_CANCEL_EDIT 新增至資源。 此命令的處理常式如下所示：

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

若要處理使用者在專案外部按一下的情況，請將下列程式碼加入至開頭 `CMainView::SetSelection` ：

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

當專案處於使用中狀態時，它應該會有焦點。 為了確保這是您處理 OnSetFocus 的情況，讓焦點在您的視圖收到焦點時一律會傳送至使用中的專案：

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

調整視圖大小時，您需要通知使用中的專案裁剪矩形已變更。 若要這樣做，請提供下列處理常式 `OnSize` ：

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

## <a name="case-study-hiersvr-from-mfc-20"></a>案例研究： MFC 2.0 的 HIERSVR

[HIERSVR](../overview/visual-cpp-samples.md) 也包含在 mfc 2.0 中，並使用 MFC/OLE1 來執行 OLE。 此附注簡要說明此應用程式最初轉換成使用 MFC/OLE 2 類別的步驟。 在完成初始埠之後加入了許多功能，以更清楚地說明 MFC/OLE 2 類別。 此處將不會涵蓋這些功能;如需這些 advanced 功能的詳細資訊，請參閱範例本身。

> [!NOTE]
> 編譯器錯誤和逐步執行程式是使用 Visual C++ 2.0 所建立。 特定的錯誤訊息和位置在 Visual C++ 4.0 中可能已變更，但概念資訊仍然有效。

### <a name="getting-it-up-and-running"></a>正在啟動並執行

將 HIERSVR 範例移植到 MFC/OLE 所採取的方法是先建立它，並修正將產生的明顯編譯器錯誤。 如果您採用 MFC 2.0 的 HIERSVR 範例，並在這個版本的 MFC 下進行編譯，您將會發現沒有許多錯誤可解決 (雖然 OCLIENT 範例) 。 這些錯誤的發生順序通常如下所述。

### <a name="compile-and-fix-errors"></a>編譯和修正錯誤

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

第一個錯誤指出伺服器的函數有更大的問題 `InitInstance` 。 OLE 伺服器所需的初始化可能是您必須對 MFC/OLE1 應用程式進行的最大變更之一，才能讓它執行。 最好的作法是查看程式碼段為 OLE 伺服器所建立的內容，並適當地修改您的程式碼。 以下是一些要牢記在心的重點：

您必須呼叫，以初始化 OLE 程式庫。 `AfxOleInit`

在檔範本物件上呼叫 SetServerInfo，以設定無法使用此函式設定的伺服器資源控制碼和執行時間類別資訊 `CDocTemplate` 。

如果命令列上有/Embedding，就不會顯示應用程式的主視窗。

您需要檔的 **GUID** 。 這是您檔案類型 (128 位) 的唯一識別碼。 程式碼提供者會為您建立一個：因此，如果您使用這裡所述的技術，從新的執行程式產生的伺服器應用程式複製新的程式碼，您就可以直接從該應用程式「竊取」 GUID。 如果沒有，您可以使用 BIN 目錄中的 GUIDGEN.EXE 公用程式。

您必須藉由呼叫將您的物件「連接」 `COleTemplateServer` 至檔範本 `COleTemplateServer::ConnectTemplate` 。

當您的應用程式獨立執行時，請更新系統登錄。 如此一來，如果使用者移動，EXE （您的應用程式從其新位置執行）會更新 Windows 系統註冊資料庫，以指向新位置。

根據執行程式建立的內容套用這些變更之後 `InitInstance` ， `InitInstance` 適用于 HIERSVR 的 (和相關的 GUID) 應如下所示：

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

您會發現，上述程式碼會參考新的資源識別碼，IDR_HIERSVRTYPE_SRVR_EMB。 這是編輯內嵌于另一個容器中的檔時，所要使用的功能表資源。 在 MFC/OLE1 中，編輯內嵌專案特定的功能表項目會即時修改。 在編輯內嵌專案時使用完全不同的功能表結構，而不是編輯以檔案為基礎的檔，可讓您更輕鬆地在這兩種不同的模式下提供不同的使用者介面。 您稍後會看到，在就地編輯内嵌物件時，會使用完全不同的功能表資源。

若要建立此資源，請將資源腳本載入 Visual C++，並複製現有的 IDR_HIERSVRTYPE 功能表資源。 將新的資源重新命名為 IDR_HIERSVRTYPE_SRVR_EMB (這是與程式與) 相同的命名慣例。 接下來，將「檔案儲存」變更為「檔案更新」;提供 ID_FILE_UPDATE 的命令識別碼。 也將 [另存新檔] 變更為 [另存新檔];提供 ID_FILE_SAVE_COPY_AS 的命令識別碼。 架構會提供這兩個命令的執行。

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

因為覆寫 `OnSetData` 是指 **OLESTATUS** 型別，所以會產生一些錯誤。 **OLESTATUS** 是 OLE1 傳回錯誤的方式。 雖然 MFC 通常會將**hresult**轉換成包含錯誤的，但這在 OLE 2 中已變更為**hresult** `COleException` 。 在此情況下，已不再需要的覆寫 `OnSetData` ，因此最簡單的做法是將它移除。

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

此函 `COleServerItem` 式會採用額外的 ' BOOL ' 參數。 此旗標會決定如何在物件上進行記憶體管理 `COleServerItem` 。 藉由將其設定為 TRUE，架構會處理這些物件的記憶體管理，並在不再需要時加以刪除。 HIERSVR 使用 `CServerItem` (衍生自 `COleServerItem`) 物件做為其原生資料的一部分，因此您會將此旗標設定為 FALSE。 這可讓 HIERSVR 判斷每個伺服器專案的刪除時間。

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

因為這些錯誤表示，在 CServerItem 中有一些尚未覆寫的「純虛擬」函數。 最有可能的原因是 OnDraw 的參數清單已變更。 若要修正這個錯誤，請依照下列 `CServerItem::OnDraw` (以及 svritem 中的宣告) 來變更：

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

新的參數為 ' rSize '。 這可讓您在方便的情況下填入繪圖的大小。 此大小必須在 **HIMETRIC**中。 在此情況下，在中填入此值並不方便，因此架構會呼叫 `OnGetExtent` 以取得範圍。 若要這樣做，您必須執行 `OnGetExtent` ：

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

在 CServerItem：： CalcNodeSize 函式中，專案大小會轉換成 **HIMETRIC** 並儲存在 *m_rectBounds*中。 未記載的 '*m_rectBounds*' 成員 `COleServerItem` (已部分由 *m_sizeExtent*取代，但在 OLE 2 中，此成員的使用方式與 OLE1) 中 *m_rectBounds* 的使用方式稍有不同。 您不會將 **HIMETRIC** 大小設定為這個成員變數，而是會傳回它。 這個傳回值是在中使用，並在先前實作為 `OnGetExtent` 。

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

CServerItem 也會覆寫 `COleServerItem::OnGetTextData` 。 這個函式在 MFC/OLE 中已淘汰，並由不同的機制取代。 Mfc OLE 範例 [HIERSVR](../overview/visual-cpp-samples.md) 的 mfc 3.0 版本會藉由覆寫來實作為此功能 `COleServerItem::OnRenderFileData` 。 這項功能對此基本埠而言並不重要，因此您可以移除 OnGetTextData 覆寫。

尚未處理的 svritem 中有更多的錯誤。 它們並不是「真正」的錯誤，只是先前錯誤所造成的錯誤。

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` 不再支援旗標 `bIncludeNative` 。 原生資料 (由伺服器專案的序列化函式所寫出的資料) 一律會複製，因此您移除第一個參數。 此外， `CopyToClipboard` 當發生錯誤而不是傳回 FALSE 時，將會擲回例外狀況。 變更 CServerView：： OnEditCopy 的程式碼，如下所示：

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

雖然比起相同版本的 OCLIENT，編譯 MFC 2.0 版的錯誤所產生的錯誤，但實際上的變更較少。

到目前為止，HIERSVR 會編譯並連結和運作為 OLE 伺服器，但不含就地編輯功能，接下來將會執行。

### <a name="adding-visual-editing"></a>新增「視覺化編輯」

若要在此伺服器應用程式中新增「視覺化編輯」 (或就地啟用) ，您必須注意幾件事：

- 當專案為就地使用中時，您需要使用特殊的功能表資源。

- 此應用程式有工具列，因此您只需要一個具有一般工具列子集的工具列，以符合伺服器 (符合上述) 所述功能表項目的功能表命令。

- 您需要一個衍生自的新類別 `COleIPFrameWnd` ，可提供就地使用者介面 (很像衍生自的 CMainFrame， `CMDIFrameWnd` 提供 MDI 使用者介面) 。

- 您需要告訴架構有關這些特殊資源和類別的資訊。

您可以輕鬆地建立功能表資源。 執行 Visual C++，將功能表資源識別碼R_HIERSVRTYPE 複製到名為 IDR_HIERSVRTYPE_SRVR_IP 的功能表資源。 修改功能表，只留下 [編輯] 和 [說明] 功能表的快顯視窗。 在 [編輯] 和 [說明] 功能表之間的功能表中加入兩個分隔符號 (看起來應該像這樣：編輯 &#124;&#124; 說明) 。 如需這些分隔符號的意義，以及如何合併伺服器和容器功能表的詳細資訊，請參閱功能表 [和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

您可以輕鬆地建立子集工具列的點陣圖，方法是從已核取 [伺服器] 選項的全新應用程式產生器產生的應用程式複製一個點陣圖。 然後可以將此點陣圖匯入 Visual C++。 請務必為點陣圖提供 IDR_HIERSVRTYPE_SRVR_IP 的識別碼。

從程式提供者產生的應用程式，也可以複製衍生自的類別，也 `COleIPFrameWnd` 就是伺服器支援。 複製這兩個檔案（IPFRAME）。CPP 和 IPFRAME。H 並將它們新增至專案。 請確定 `LoadBitmap` 呼叫是指 IDR_HIERSVRTYPE_SRVR_IP，也就是在上一個步驟中建立的點陣圖。

現在已建立所有的新資源和類別，請新增必要的程式碼，讓架構知道這些 (，並知道此應用程式現在支援就地編輯) 。 這是藉由在函式的呼叫中新增更多參數來完成 `SetServerInfo` `InitInstance` ：

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

現在已準備好在也支援就地啟用的任何容器中就地執行。 但是，程式碼中仍然潛伏了一個小 bug。 HIERSVR 支援內容功能表，當使用者按下滑鼠右鍵時顯示。 當 HIERSVR 已完全開啟時，此功能表便可運作，但在就地編輯內嵌時無法運作。 原因可以釘選到 CServerView：： OnRButtonDown 中的下列一行程式碼：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

請注意的參考 `AfxGetApp()->m_pMainWnd` 。 當伺服器處於啟用狀態時，它會有主視窗且 m_pMainWnd 已設定，但通常不會出現。 此外，這個視窗是指應用程式的 *主* 視窗，也就是當伺服器完全開啟或獨立執行時所顯示的 MDI 框架視窗。 它不會參考使用中的框架視窗，在就地啟用時，是從衍生的框架視窗 `COleIPFrameWnd` 。 若要取得正確的使用中視窗，即使在就地編輯時，此版本的 MFC 也會加入新的函式 `AfxGetMainWnd` 。 一般而言，您應該使用這個函數，而不是 `AfxGetApp()->m_pMainWnd` 。 此程式碼需要變更，如下所示：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

現在您已至少啟用 OLE 伺服器，可就地啟用功能。 但是 mfc/OLE 2 仍有許多功能可供 MFC/OLE1 使用。 如需您可能想要執行之功能的詳細概念，請參閱 HIERSVR 範例。 以下列出一些 HIERSVR 所實行的功能：

- 縮放，適用于容器的真實 WYSIWYG 行為。

- 拖放和自訂剪貼簿格式。

- 在選取專案變更時，將容器視窗滾動。

MFC 3.0 中的 HIERSVR 範例也會對其伺服器專案使用稍有不同的設計。 這有助於節省記憶體，並讓您的連結更有彈性。 使用2.0 版的 HIERSVR，樹狀結構中的每個節點 *都是-a* `COleServerItem` 。 `COleServerItem` 會有比每個節點嚴格需要的額外負荷，但每個使用中的 `COleServerItem` 連結都需要。 但大部分的情況下，在任何指定時間都有很少的作用中連結。 為了讓這項工作更有效率，這個版本的 MFC 中的 HIERSVR 會將節點與分開 `COleServerItem` 。 它同時具有 CServerNode 和 `CServerItem` 類別。 `CServerItem`只有在必要時 `COleServerItem` 才會建立衍生自) 的 (。 一旦容器 (或容器) 使用該特定節點的特定連結停止，就會刪除與該 CServerNode 相關聯的 CServerItem 物件。 這項設計更有效率且更有彈性。 在處理多個選取連結時，它的彈性也會隨之增加。 這兩個版本的 HIERSVR 都不支援多重選取，但是加入 (，以及支援將這類) 選項的連結與 MFC 3.0 版的 HIERSVR 分開，是因為與 `COleServerItem` 原生資料分開。

## <a name="see-also"></a>另請參閱

[依編號的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)
