---
title: CDocument 類別
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: b7358c2206c15660b9ffb283802283ee71e57f03
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299071"
---
# <a name="cdocument-class"></a>CDocument 類別

提供使用者定義的文件類別的基本功能。

## <a name="syntax"></a>語法

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|建構 `CDocument` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocument::AddView](#addview)|將檢視附加至文件。|
|[CDocument::BeginReadChunks](#beginreadchunks)|初始化區塊讀取。|
|[CDocument::CanCloseFrame](#cancloseframe)|進階可覆寫;關閉框架視窗檢視這份文件之前呼叫。|
|[CDocument::ClearChunkList](#clearchunklist)|清除區塊清單。|
|[CDocument::ClearPathName](#clearpathname)|清除文件物件的路徑。|
|[CDocument::DeleteContents](#deletecontents)|呼叫以執行清除作業的文件。|
|[CDocument::FindChunk](#findchunk)|會尋找具有指定之 GUID。|
|[CDocument::GetAdapter](#getadapter)|讓指標回到物件，實作`IDocument`介面。|
|[CDocument::GetDocTemplate](#getdoctemplate)|傳回描述文件類型的文件範本的指標。|
|[CDocument::GetFile](#getfile)|讓指標回到所需`CFile`物件。|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|傳回第一個位置清單中的檢視;用來開始反覆項目。|
|[CDocument::GetNextView](#getnextview)|逐一查看的文件相關聯的檢視清單。|
|[CDocument::GetPathName](#getpathname)|傳回文件的資料檔案的路徑。|
|[CDocument::GetThumbnail](#getthumbnail)|呼叫以建立縮圖的提供者用來顯示縮圖中的點陣圖。|
|[CDocument::GetTitle](#gettitle)|傳回文件的標題。|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|呼叫以初始化搜尋內容搜尋處理常式。|
|[CDocument::IsModified](#ismodified)|表示自上次儲存後是否已經修改文件。|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|會告知是否的這個執行個體`CDocument`搜尋及組織的處理常式建立物件。|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|呼叫以從資料流載入文件資料。|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|豐富的預覽字型變更之前呼叫。|
|[CDocument::OnChangedViewList](#onchangedviewlist)|檢視加入或移除文件之後呼叫。|
|[CDocument::OnCloseDocument](#onclosedocument)|呼叫以關閉文件。|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|需要建立豐富的預覽的預覽畫面格時由架構呼叫。|
|[CDocument::OnDocumentEvent](#ondocumentevent)|由架構呼叫以回應文件事件。|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|在衍生的類別，用來繪製內容的縮圖中，這個方法會覆寫。|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|需要從資料流載入文件資料時由架構呼叫。|
|[CDocument::OnNewDocument](#onnewdocument)|呼叫以建立新的文件。|
|[CDocument::OnOpenDocument](#onopendocument)|呼叫以開啟現有文件。|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示預覽處理常式，從呼叫 GetFocus 函式傳回 HWND。|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|指示預覽處理常式來處理從預覽處理常式正在執行的程序的訊息幫浦往上傳遞的按鍵輸入。|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|豐富的預覽背景色彩已變更時呼叫。|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|豐富的預覽字型已變更時呼叫。|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|豐富的預覽網站已經變更時呼叫。|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|豐富的預覽文字色彩已變更時呼叫。|
|[CDocument::OnSaveDocument](#onsavedocument)|呼叫以將文件儲存至磁碟。|
|[CDocument::OnUnloadHandler](#onunloadhandler)|正在卸載預覽處理常式時，由架構呼叫。|
|[CDocument::PreCloseFrame](#precloseframe)|框架視窗關閉之前呼叫。|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|讀取下一個區塊的值。|
|[CDocument::ReleaseFile](#releasefile)|釋出要使其可供使用的其他應用程式的檔案。|
|[CDocument::RemoveChunk](#removechunk)|移除具有指定之 GUID。|
|[CDocument::RemoveView](#removeview)|中斷連結的文件中的檢視。|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|進階可覆寫;呼叫時開啟或儲存作業無法完成，因為發生例外狀況。|
|[CDocument::SaveModified](#savemodified)|進階可覆寫;呼叫以詢問使用者是否應該儲存文件。|
|[CDocument::SetChunkValue](#setchunkvalue)|設定區塊值。|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|設定旗標，表示自上次儲存後，您已修改的文件。|
|[CDocument::SetPathName](#setpathname)|設定文件所使用的資料檔案的路徑。|
|[CDocument::SetTitle](#settitle)|設定文件的標題。|
|[CDocument::UpdateAllViews](#updateallviews)|通知所有文件的檢視已經過修改。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|傳送郵件訊息使用附加的文件。|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|如果郵件的支援已存在，可讓傳送郵件命令。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定`CDocument`inicializace dllhost byla 的縮圖建立物件。 應該簽入`CView::OnDraw`。|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定`CDocument`物件所建立的 prevhost `Rich Preview`。 應該簽入`CView::OnDraw`。|
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定`CDocument`物件由索引子或建立其他的搜尋應用程式。|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定豐富預覽視窗的背景的色彩。 這個色彩是由主應用程式設定。|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定前景色彩的豐富預覽視窗。 這個色彩是由主應用程式設定。|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主應用程式設定。|

## <a name="remarks"></a>備註

文件表示的使用者通常隨即開啟，並開啟檔案 命令，並使用檔案儲存命令會將儲存的資料單位。

`CDocument` 支援標準的作業，例如建立文件、 載入它，並將它儲存。 架構操作使用介面所定義的文件`CDocument`。

應用程式可以支援多個類型的文件;例如，應用程式可能支援試算表和文字文件。 每一種文件有相關聯的文件範本 中;文件範本會指定要用於該類型的文件的哪些資源 （比方說，功能表、 圖示或快速鍵對應表）。 每份文件包含與其相關聯的指標`CDocTemplate`物件。

透過文件與使用者互動[CView](../../mfc/reference/cview-class.md)與其相關聯的物件。 檢視轉譯的文件框架視窗中的映像，並解譯使用者輸入為文件上的作業。 文件可以有多個與其相關聯的檢視。 當使用者開啟文件上的視窗時，架構會建立一個檢視，並將它附加至文件。 文件範本會指定何種檢視和框架視窗用來顯示每一種文件。

文件屬於架構的標準命令路由，並因此接收命令，從標準的使用者介面元件 （例如儲存檔案 功能表項目）。 文件接收轉送的現用檢視表的命令。 如果文件不會處理指定的命令，它會將轉送命令來管理它的文件範本。

文件的資料修改時，每個自己的檢視必須反映這些修改。 `CDocument` 提供[UpdateAllViews](#updateallviews)為通知的這類變更，檢視，以便檢視可以重新繪製視您的成員函式。 此架構也會提示使用者關閉之前儲存修改過的檔案。

若要實作一般的應用程式中的文件，您必須執行下列作業：

- 自`CDocument`每種類型的文件。

- 加入成員變數以儲存每個文件的資料。

- 實作成員函式來讀取和修改文件的資料。 文件的檢視是這些成員函式的最重要的使用者。

- 覆寫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)寫入和讀取文件的資料磁碟的文件類別中的成員函式。

`CDocument` 支援傳送您的文件，透過電子郵件，郵件的支援 (MAPI) 是否存在。 請參閱文章[MAPI](../../mfc/mapi.md)並[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。

如需詳細資訊`CDocument`，請參閱 <<c2> [ 序列化](../../mfc/serialization-in-mfc.md)，[文件/檢視架構主題](../../mfc/document-view-architecture.md)，和[文件/檢視建立](../../mfc/document-view-creation.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="addview"></a>  CDocument::AddView

呼叫此函式可將檢視附加至文件。

```
void AddView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
要加入的檢視點。

### <a name="remarks"></a>備註

此函式會將指定的檢視加入至文件，相關聯的檢視清單函式也會設定此文件的檢視表的文件指標。 將新建立的檢視物件附加至文件時，架構會呼叫此函式發生這種情況中回應開新檔案、 開啟檔案或新的視窗的命令或分隔器視窗分割。

只有當您以手動方式建立和附加的檢視，請呼叫此函式。 通常您會讓連接文件和檢視所定義的 framework [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別中，檢視類別和框架視窗類別建立關聯的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks

初始化區塊讀取。

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>備註

##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame

顯示文件框架視窗關閉之前由架構呼叫。

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
指向框架視窗的 附加至文件的檢視。

### <a name="return-value"></a>傳回值

安全地關閉框架視窗; 如果為非零否則為 0。

### <a name="remarks"></a>備註

預設實作會檢查是否有其他框架視窗，顯示文件。 如果指定的框架視窗會顯示文件的最後一個，函數就會提示使用者儲存文件，如果已修改。 如果您想要執行特殊處理的框架視窗關閉時，請覆寫這個函式。 這是一種進階可覆寫。

##  <a name="cdocument"></a>  CDocument::CDocument

建構 `CDocument` 物件。

```
CDocument();
```

### <a name="remarks"></a>備註

架構會處理為您建立的文件。 覆寫[OnNewDocument](#onnewdocument)成員函式來初始化對以每個文件為基礎; 這是在單一文件介面 (SDI) 應用程式中特別重要。

##  <a name="clearchunklist"></a>  CDocument::ClearChunkList

清除區塊清單。

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>備註

##  <a name="clearpathname"></a>  CDocument::ClearPathName

清除文件物件的路徑。

```
virtual void ClearPathName();
```

### <a name="remarks"></a>備註

清除 從路徑`CDocument`物件會在接下來儲存文件時，提示使用者的應用程式。 這可讓**儲存**命令的行為類似**另存新檔**命令。

##  <a name="deletecontents"></a>  CDocument::DeleteContents

由架構呼叫以刪除文件的資料，而不會終結`CDocument`物件本身。

```
virtual void DeleteContents();
```

### <a name="remarks"></a>備註

它會在文件，則會終結之前呼叫。 它也會呼叫，以確保文件是空的就會重複使用之前。 這是特別重要的 SDI 應用程式，使用只有一個文件;每當使用者建立或開啟另一個文件時，會重複使用文件。 呼叫此函式以實作 [編輯全部清除] 或類似的命令會刪除所有文件的資料。 此函式的預設實作不做任何動作。 覆寫這個函式來刪除您的文件中的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>  CDocument::FindChunk

會尋找具有指定之 GUID。

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*guid*<br/>
指定要尋找區塊的 GUID。

*pid*<br/>
指定若要尋找區塊的 PID。

### <a name="return-value"></a>傳回值

如果成功內部的區塊清單中的位置。 否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="getadapter"></a>  CDocument::GetAdapter

讓指標回到物件，實作`IDocument`介面。

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>傳回值

物件，實作的指標`IDocument`介面。

### <a name="remarks"></a>備註

##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate

呼叫此函式可取得此文件類型的指標的文件範本。

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>傳回值

文件範本，此文件類型，或如果文件未受管理的文件範本則為 NULL 指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>  CDocument::GetFile

呼叫以取得變數的指標，此成員函式`CFile`物件。

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
為所需的檔案路徑的字串。 路徑可能是相對或絕對。

*pError*<br/>
現有的檔案例外狀況物件，表示作業的完成狀態指標。

*nOpenFlags*<br/>
共用和存取模式。 指定開啟檔案時要採取的動作。 您可以結合 CFile 建構函式中所列的選項[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)使用的位元 OR (&#124;) 運算子。 一個存取權限，以及一個共用選項是必要的資訊;`modeCreate`和`modeNoInherit`是選擇性的模式。

### <a name="return-value"></a>傳回值

`CFile` 物件的指標。

##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

呼叫此函式可取得的文件相關聯的檢視清單中的第一個檢視的位置。

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用於反覆項目[GetNextView](#getnextview)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>  CDocument::GetNextView

呼叫此函式來逐一查看所有文件的檢視。

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
先前呼叫所傳回的位置值的參考`GetNextView`或是[GetFirstViewPosition](#getfirstviewposition)成員函式。 此值必須不是 NULL。

### <a name="return-value"></a>傳回值

檢視所識別的指標*rPosition*。

### <a name="remarks"></a>備註

此函數會傳回所識別的檢視*rPosition* ，然後設定*rPosition*清單中的下一步 檢視的位置值。 擷取的檢視是否在清單中，最後再*rPosition*設為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>  CDocument::GetPathName

呼叫此函式可取得的文件的磁碟檔案的完整的路徑。

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>傳回值

文件的完整的路徑。 此字串是空的如果文件尚未儲存，或沒有與它相關聯的磁碟檔案。

##  <a name="getthumbnail"></a>  CDocument::GetThumbnail

建立縮圖的提供者用來顯示縮圖中的點陣圖。

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>參數

*cx*<br/>
指定點陣圖的高度與寬度。

*phbmp*<br/>
此函數會成功傳回時，請包含點陣圖的控制代碼。

*pdwAlpha*<br/>
包含指定的 alpha 色頻值，當函式會傳回成功的 DWORD。

### <a name="return-value"></a>傳回值

已成功; 建立傳回如果縮圖的點陣圖，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="gettitle"></a>  CDocument::GetTitle

呼叫此函式可取得文件的標題，通常衍生自文件的檔案名稱。

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>傳回值

文件的標題。

##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

呼叫以初始化搜尋內容搜尋處理常式。

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>備註

在衍生類別初始化搜尋內容中的這個方法會覆寫。 內容應該要分隔的部分的字串 「; 」。 比方說，「 點;矩形;ole 項目 」。

##  <a name="ismodified"></a>  CDocument::IsModified

呼叫此函式可判斷自上次儲存後是否已經修改文件。

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>傳回值

非零值，如果自上次儲存; 已修改的文件否則為 0。

##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

會告知是否的這個執行個體`CDocument`建立搜尋及組織的處理常式。

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>傳回值

傳回 TRUE，如果這個執行個體`CDocument`建立搜尋及組織的處理常式。

### <a name="remarks"></a>備註

目前此函式會傳回 TRUE，只針對跨處理序伺服器中實作豐富的預覽處理常式。 您可以設定適當的旗標 （m_bPreviewHandlerMode、 m_bSearchMode m_bGetThumbnailMode） 在您的應用程式層級，讓此函式傳回 TRUE。

##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

呼叫以從資料流載入文件資料。

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
資料流的指標。 介面會提供這個資料流。

*dwGrfMode*<br/>
資料流的存取模式。

### <a name="return-value"></a>傳回值

如果載入作業成功，否則為錯誤碼的 HRESULT 傳回 S_OK。

### <a name="remarks"></a>備註

您可以覆寫這個方法在衍生類別來自訂如何將資料從資料流中。

##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

指定`CDocument`inicializace dllhost byla 的縮圖建立物件。 應該簽入`CView::OnDraw`。

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>備註

`TRUE` 表示文件已由 inicializace dllhost byla 的縮圖。

##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

指定`CDocument`prevhost 已建立物件的豐富預覽。 應該簽入`CView::OnDraw`。

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>備註

TRUE 表示，prevhost 已建立的文件的豐富預覽。

##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

指定`CDocument`索引子或另一個搜尋應用程式建立物件。

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>備註

`TRUE` 表示文件已建立索引子或另一個搜尋應用程式。

##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

指定豐富的預覽視窗的背景色彩。 這個色彩是由主應用程式設定。

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>備註

##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

指定豐富的預覽視窗的前景色彩。 這個色彩是由主應用程式設定。

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>備註

##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主應用程式設定。

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>備註

##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

豐富的預覽字型變更之前呼叫。

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

加入或移除文件中的檢視之後，由架構呼叫。

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>備註

此函式的預設實作會檢查是否的最後一個檢視已停用，是否是的話，會刪除文件。 如果您想要執行特殊處理的架構中加入或移除檢視時，請覆寫這個函式。 例如，如果您想要保持開啟，即使沒有附加至其檢視的文件時，覆寫這個函式。

##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument

當文件關閉時，通常作為 File Close 命令的一部分，由架構呼叫。

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>備註

此函式的預設實作會終結所有用於檢視文件框架、 關閉檢視、 清除文件的內容，然後呼叫[DeleteContents](#deletecontents)成員函式來刪除的文件資料。

如果您想要執行特殊清除處理序架構關閉文件時，請覆寫這個函式。 比方說，如果文件代表資料庫中的記錄，您可能想要覆寫這個函式來關閉資料庫。 您應該從您的覆寫來呼叫此函式的基底類別版本。

##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

需要建立豐富的預覽的預覽畫面格時由架構呼叫。

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>傳回值

傳回為 true，則會成功; 建立的框架否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

由架構呼叫以回應文件事件。

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>參數

*deEvent*<br/>
[in]列舉的資料類型，描述事件的型別。

### <a name="remarks"></a>備註

文件事件可能會影響多個類別。 這個方法會負責處理而不會影響類別的文件事件[CDocument 類別](../../mfc/reference/cdocument-class.md)。 目前，唯一必須回應文件事件的類別是[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument`類別有其他可覆寫方法負責處理效果`CDocument`。

下表列出可能的值為*deEvent*和它們對應到事件。

|值|相對應的事件|
|-----------|-------------------------|
|`onAfterNewDocument`|建立新的文件。|
|`onAfterOpenDocument`|開啟新文件。|
|`onAfterSaveDocument`|已儲存的文件。|
|`onAfterCloseDocument`|文件已關閉。|

##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

在衍生的類別，用來繪製縮圖中，這個方法會覆寫。

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>參數

*dc*<br/>
裝置內容的參考。

*lprcBounds*<br/>
指定縮圖應該要繪製之區域的周框。

### <a name="remarks"></a>備註

##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail

透過傳送訊息的內建的郵件主機 （如果有的話） 與文件做為附件。

```
void OnFileSendMail();
```

### <a name="remarks"></a>備註

`OnFileSendMail` 呼叫[OnSaveDocument](#onsavedocument)序列化 （儲存） 到暫存檔案，便會透過電子郵件的未命名和修改文件。 如果未修改的文件，就不會需要的暫存檔案;原始傳送。 `OnFileSendMail` 載入 MAPI32。如果它擁有尚未載入的 DLL。

特殊實作`OnFileSendMail`for [COleDocument](../../mfc/reference/coledocument-class.md)控制代碼正確複合檔案。

`CDocument` 支援傳送您的文件，透過電子郵件，郵件的支援 (MAPI) 是否存在。 請參閱文章[MAPI 主題](../../mfc/mapi.md)並[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。

##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

需要從資料流載入文件資料時由架構呼叫。

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
內送資料流的指標。

*grfMode*<br/>
資料流的存取模式。

### <a name="return-value"></a>傳回值

如果負載是成功則為 S_OK否則為錯誤碼。

### <a name="remarks"></a>備註

##  <a name="onnewdocument"></a>  CDocument::OnNewDocument

由架構呼叫做為新檔案 命令的一部分。

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>傳回值

非零值，如果已成功初始化文件;否則為 0。

### <a name="remarks"></a>備註

此函式的預設實作會呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的且隨後會將標示為初始狀態的新文件。 覆寫這個函式來初始化新的文件的資料結構。 您應該從您的覆寫來呼叫此函式的基底類別版本。

如果使用者選擇在 SDI 應用程式中的新檔案 命令，架構會使用此函式來重新初始化現有的文件，而不是建立一個新。 如果使用者選擇新檔案中的多個文件介面 (MDI) 應用程式，架構會每次建立新的文件，並接著會呼叫此函式可將它初始化。 您必須在新檔案 命令會在 SDI 應用程式中有效的建構函式而不是這個函式中放置初始化程式碼。

請注意，有情況`OnNewDocument`呼叫兩次。 會發生這種情況是當文件會內嵌為 ActiveX 文件伺服程式。 第一次呼叫此函式`CreateInstance`方法 (由`COleObjectFactory`-衍生的類別) 的第二次`InitNew`方法 (所公開`COleServerDoc`-衍生的類別)。

### <a name="example"></a>範例

下列範例說明初始化文件物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>  CDocument::OnOpenDocument

由架構呼叫以開啟舊檔 命令的一部分。

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
要開啟的文件的路徑點。

### <a name="return-value"></a>傳回值

非零值，如果已成功載入文件;否則為 0。

### <a name="remarks"></a>備註

此函式的預設實作會開啟指定的檔案，呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的呼叫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)讀取的檔案然後會將標示為全新的文件和內容。 如果您想要使用的封存機制或檔案機制以外的產品，請覆寫這個函式。 例如，您可以撰寫應用程式的文件位置代表資料庫，而不是個別檔案中的記錄。

如果使用者選擇 [開啟檔案] 命令在 SDI 應用程式，則架構會使用此函式來重新初始化現有`CDocument`物件，而不是建立一個新資源。 如果使用者選擇開啟檔案的 MDI 應用程式中，建構新的 framework`CDocument`物件每次，然後呼叫此函式可將它初始化。 您必須開啟檔案 命令會在 SDI 應用程式中有效的建構函式而不是這個函式中放置初始化程式碼。

### <a name="example"></a>範例

下列範例說明初始化文件物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

指示預覽處理常式，以傳回 HWND 擷取自呼叫`GetFocus`函式。

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>參數

*phwnd*<br/>
[out]當這個方法傳回時，包含 HWND 從呼叫傳回的指標`GetFocus`從預覽處理常式的幕前執行緒的函式。

### <a name="return-value"></a>傳回值

傳回 S_OK，如果登錄成功。否則為錯誤值。

### <a name="remarks"></a>備註

##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

指示預覽處理常式來處理從預覽處理常式正在執行的程序的訊息幫浦往上傳遞的按鍵輸入。

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>參數

*pmsg*<br/>
[in]視窗訊息指標。

### <a name="return-value"></a>傳回值

如果可以由預覽處理常式處理按鍵訊息，處理常式會處理它，並傳回 S_OK。 如果預覽處理常式無法處理的按鍵輸入訊息，它會建議它透過主機`IPreviewHandlerFrame::TranslateAccelerator`。 如果主應用程式處理訊息時，這個方法會傳回 S_OK。 如果主應用程式不會處理訊息，則這個方法會傳回 S_FALSE。

### <a name="remarks"></a>備註

##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

豐富的預覽背景色彩已變更時呼叫。

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

豐富的預覽字型已變更時呼叫。

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

豐富預覽網站已經變更時呼叫。

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

豐富的預覽文字色彩已變更時呼叫。

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>備註

##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument

由架構呼叫以儲存檔案 或 另存新檔 命令的一部分。

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向檔案應該儲存的完整路徑。

### <a name="return-value"></a>傳回值

非零值，如果已成功儲存文件;否則為 0。

### <a name="remarks"></a>備註

此函式的預設實作會開啟指定的檔案，呼叫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)將文件的資料寫入至檔案，然後標記文件標記為清除。 如果您想要執行特殊處理的架構來儲存文件時，請覆寫這個函式。 例如，您可以撰寫應用程式的文件位置代表資料庫，而不是個別檔案中的記錄。

##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

卸載預覽處理常式時，由架構呼叫。

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>備註

##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

如果郵件的支援 (MAPI) 存在，可讓 ID_FILE_SEND_MAIL 命令。

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指標[CCmdUI](../../mfc/reference/ccmdui-class.md) ID_FILE_SEND_MAIL 命令相關聯的物件。

### <a name="remarks"></a>備註

否則函式會移除 ID_FILE_SEND_MAIL 命令，從功能表中，包括分隔符號的上方或下方適當的功能表項目。 如果啟用 MAPI MAPI32。DLL 則會出現在路徑中，以及獲得 [Mail] 區段中。INI 檔案，MAPI = 1。 大部分的應用程式會將此命令放在 [檔案] 功能表上。

`CDocument` 支援傳送您的文件，透過電子郵件，郵件的支援 (MAPI) 是否存在。 請參閱文章[MAPI 主題](../../mfc/mapi.md)並[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。

##  <a name="precloseframe"></a>  CDocument::PreCloseFrame

終結框架視窗之前，此成員函式是由架構呼叫。

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
指標[CFrameWnd](../../mfc/reference/cframewnd-class.md)存有相關聯`CDocument`物件。

### <a name="remarks"></a>備註

它可以是覆寫，以提供自訂的清除，但請務必呼叫基底類別。

預設值是`PreCloseFrame`沒有任何作用`CDocument`。 `CDocument`-衍生的類別[COleDocument](../../mfc/reference/coledocument-class.md)並[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此成員函式。

##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

讀取的下一個區塊的值。

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>參數

*ppValue*<br/>
[out]此函式會傳回*ppValue*包含已讀取的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

##  <a name="releasefile"></a>  CDocument::ReleaseFile

此成員函式是由發行檔案，因此可以使用其他應用程式的架構所呼叫。

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>參數

*pFile*<br/>
若要釋出 CFile 物件的指標。

*bAbort*<br/>
指定檔案是否要使用其中一種會釋放`CFile::Close`或`CFile::Abort`。 如果檔案是使用發行，則為 FALSE。 [CFile::Close](../../mfc/reference/cfile-class.md#close);如果檔案是使用發行，則為 TRUE [cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。

### <a name="remarks"></a>備註

如果*bAbort*為 TRUE 時，`ReleaseFile`呼叫`CFile::Abort`，且放開檔案。 `CFile::Abort` 不會擲回例外狀況。

如果*bAbort*為 FALSE 時，`ReleaseFile`呼叫`CFile::Close`和發行檔案。

覆寫此成員函式，以釋放檔案之前，需要使用者動作。

##  <a name="removechunk"></a>  CDocument::RemoveChunk

移除具有指定之 GUID 的區塊。

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*Guid*<br/>
指定要移除區塊的 GUID。

*pid*<br/>
指定要移除區塊的 PID。

### <a name="remarks"></a>備註

##  <a name="removeview"></a>  CDocument::RemoveView

呼叫此函式可卸離文件中的檢視。

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
要移除的檢視點。

### <a name="remarks"></a>備註

此函式的文件，相關聯的檢視清單中移除指定的檢視它也會設定為 NULL 的檢視表的文件指標。 框架視窗已關閉或窗格的分隔器視窗關閉時，此函式是由架構呼叫。

只有當您手動卸離的檢視，請呼叫此函式。 通常您會讓卸離文件和檢視定義的 framework [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別中，檢視類別和框架視窗類別建立關聯的物件。

在範例，請參閱[AddView](#addview)如需範例實作。

##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

如果發生例外狀況時呼叫 (通常[CFileException](../../mfc/reference/cfileexception-class.md)或是[CArchiveException](../../mfc/reference/carchiveexception-class.md)) 儲存或載入文件時。

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
在的文件的名稱會指向儲存或載入。

*e*<br/>
已擲回的例外狀況的點。 可以是 NULL。

*bSaving*<br/>
旗標，指出哪一個作業正在進行;如果文件儲存，0 如果文件載入為非零。

*nIDPDefault*<br/>
如果函式未指定更特定的顯示錯誤訊息的識別碼。

### <a name="remarks"></a>備註

預設實作會檢查例外狀況物件，並尋找特別說明原因的錯誤訊息。 如果找不到特定的訊息，或如果*電子*是 NULL，由指定的一般訊息*nIDPDefault*參數使用。 此函式接著會顯示包含錯誤訊息的訊息方塊。 如果您想要提供額外的自訂的失敗訊息，請覆寫這個函式。 這是一種進階可覆寫。

##  <a name="savemodified"></a>  CDocument::SaveModified

修改過的文件關閉之前由架構呼叫。

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>傳回值

放心地繼續並關閉文件; 如果為非零0，表示不應該關閉文件。

### <a name="remarks"></a>備註

此函式的預設實作會顯示訊息方塊，詢問使用者是否要將變更儲存至文件中，如果任何已進行。 如果您的程式需要不同的提示程序，請覆寫這個函式。 這是一種進階可覆寫。

##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue

設定區塊值。

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指定要設定區塊值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

您已在文件的任何修改之後，請呼叫此函式。

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
旗標指出是否已修改的文件。

### <a name="remarks"></a>備註

以一致的方式呼叫此函式，可確保此架構會提示使用者關閉文件之前先儲存變更。 通常您應該使用預設值為 TRUE *bModified*參數。 若要標記乾淨的文件 （未修改），呼叫此函式值是 FALSE。

##  <a name="setpathname"></a>  CDocument::SetPathName

呼叫此函式以指定的文件的磁碟檔案的完整的路徑。

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向要作為文件路徑的字串。

*bAddToMRU*<br/>
決定是否檔案名稱加入至最近使用過的 (MRU) 檔案清單。 如果為 TRUE，會加入檔案名稱;如果為 FALSE，它不會加入。

### <a name="remarks"></a>備註

值而定*bAddToMRU*新增，或未加入至應用程式所維護的 MRU 清單的路徑。 請注意，某些文件不相關聯的磁碟檔案。 只有當您正在覆寫開啟，並儲存檔案架構所使用的預設實作，請呼叫此函式。

##  <a name="settitle"></a>  CDocument::SetTitle

呼叫此函式來指定文件的標題 （框架視窗的標題列中顯示的字串）。

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
指向要做為文件的標題字串。

### <a name="remarks"></a>備註

呼叫此函式會更新所有顯示文件的框架視窗的標題。

##  <a name="updateallviews"></a>  CDocument::UpdateAllViews

在修改文件之後，請呼叫此函式。

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改文件中，檢視或更新所有的檢視是否為 NULL。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
指向儲存修改的相關資訊的物件。

### <a name="remarks"></a>備註

您應該呼叫此函式之後您呼叫, [SetModifiedFlag](#setmodifiedflag)成員函式。 此函式會通知附加於文件，除了所指定的檢視每個檢視*pSender*，已修改過的文件。 一般都會呼叫此函式從您的檢視類別之後，使用者已變更透過檢視文件。

此函式會呼叫[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)除了傳送的文件的檢視表的每個成員函式檢視，請傳遞*pHint*並*lHint*。 您可以使用這些參數，將資訊傳遞至相關的文件進行的修改檢視。 您可以使用資訊來編碼*lHint*及 （或) 您可以定義[CObject](../../mfc/reference/cobject-class.md)-衍生類別，以儲存修改的相關資訊，並傳遞的物件，該類別使用的*pHint*. 覆寫`CView::OnUpdate`成員函式，在您[CView](../../mfc/reference/cview-class.md)-衍生類別，以最佳化更新檢視的顯示，根據傳遞的資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../visual-cpp-samples.md)<br/>
[MFC 範例 NPP](../../visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
