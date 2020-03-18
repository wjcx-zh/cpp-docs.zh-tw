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
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418696"
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
|[CDocument：： CDocument](#cdocument)|建構 `CDocument` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocument：： AddView](#addview)|將視圖附加至檔。|
|[CDocument：： BeginReadChunks](#beginreadchunks)|初始化區塊讀取。|
|[CDocument：： CanCloseFrame](#cancloseframe)|Advanced 可覆寫;在關閉流覽此檔的框架視窗之前呼叫。|
|[CDocument：： ClearChunkList](#clearchunklist)|清除區塊清單。|
|[CDocument：： ClearPathName](#clearpathname)|清除檔物件的路徑。|
|[CDocument：:D eleteContents](#deletecontents)|呼叫以執行檔的清除。|
|[CDocument：： FindChunk](#findchunk)|尋找具有指定 GUID 的區塊。|
|[CDocument：： GetAdapter](#getadapter)|傳回物件的指標，以執行 `IDocument` 介面。|
|[CDocument：： GetDocTemplate](#getdoctemplate)|傳回描述檔案類型之檔範本的指標。|
|[CDocument：： GetFile](#getfile)|傳回所需 `CFile` 物件的指標。|
|[CDocument：： GetFirstViewPosition](#getfirstviewposition)|傳回視圖清單中第一個的位置;用來開始反復專案。|
|[CDocument：： GetNextView](#getnextview)|逐一查看與檔相關聯的視圖清單。|
|[CDocument：： GetPathName](#getpathname)|傳回檔資料檔的路徑。|
|[CDocument：： GetThumbnail](#getthumbnail)|呼叫以建立可供縮圖提供者用來顯示縮圖的點陣圖。|
|[CDocument：： GetTitle](#gettitle)|傳回檔的標題。|
|[CDocument：： InitializeSearchContent](#initializesearchcontent)|呼叫以初始化搜尋處理常式的搜尋內容。|
|[CDocument：： IsModified](#ismodified)|指出檔自從上次儲存後是否已修改。|
|[CDocument：： IsSearchAndOrganizeHandler](#issearchandorganizehandler)|指出是否已針對搜尋 & 組織處理常式建立 `CDocument` 物件的這個實例。|
|[CDocument：： LoadDocumentFromStream](#loaddocumentfromstream)|呼叫以從資料流程載入檔資料。|
|[CDocument：： OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|在 Rich Preview 字型變更之前呼叫。|
|[CDocument：： OnChangedViewList](#onchangedviewlist)|在檔中加入或移除視圖之後呼叫。|
|[CDocument：： OnCloseDocument](#onclosedocument)|呼叫以關閉檔。|
|[CDocument：： OnCreatePreviewFrame](#oncreatepreviewframe)|當架構需要建立用於豐富預覽的預覽畫面格時呼叫。|
|[CDocument：： OnDocumentEvent](#ondocumentevent)|由架構呼叫以回應檔事件。|
|[CDocument：： OnDrawThumbnail](#ondrawthumbnail)|覆寫衍生類別中的這個方法，以繪製縮圖的內容。|
|[CDocument：： OnLoadDocumentFromStream](#onloaddocumentfromstream)|需要從資料流程載入檔資料時，由架構呼叫。|
|[CDocument：： OnNewDocument](#onnewdocument)|呼叫以建立新檔。|
|[CDocument：： OnOpenDocument](#onopendocument)|呼叫以開啟現有的檔。|
|[CDocument：： OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示預覽處理常式傳回 HWND，使其無法呼叫 GetFocus 函數。|
|[CDocument：： OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|引導預覽處理常式處理從預覽處理常式執行所在進程的訊息提取傳遞的按鍵。|
|[CDocument：： OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|當豐富的預覽背景色彩已變更時呼叫。|
|[CDocument：： OnRichPreviewFontChanged](#onrichpreviewfontchanged)|當 Rich Preview 字型變更時呼叫。|
|[CDocument：： OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|當豐富的預覽網站已變更時呼叫。|
|[CDocument：： OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|當豐富的預覽文字色彩已變更時呼叫。|
|[CDocument：： OnSaveDocument](#onsavedocument)|呼叫以將檔儲存至磁片。|
|[CDocument：： OnUnloadHandler](#onunloadhandler)|在卸載預覽處理常式時，由架構呼叫。|
|[CDocument：:P reCloseFrame](#precloseframe)|在框架視窗關閉之前呼叫。|
|[CDocument：： ReadNextChunkValue](#readnextchunkvalue)|讀取下一個區塊值。|
|[CDocument：： ReleaseFile](#releasefile)|釋放檔案，使其可供其他應用程式使用。|
|[CDocument：： RemoveChunk](#removechunk)|移除具有指定之 GUID 的區塊。|
|[CDocument：： RemoveView](#removeview)|從檔卸離視圖。|
|[CDocument：： ReportSaveLoadException](#reportsaveloadexception)|Advanced 可覆寫;當開啟或儲存作業因例外狀況而無法完成時呼叫。|
|[CDocument：： SaveModified](#savemodified)|Advanced 可覆寫;呼叫以詢問使用者是否應儲存檔。|
|[CDocument：： SetChunkValue](#setchunkvalue)|設定區塊值。|
|[CDocument：： SetModifiedFlag](#setmodifiedflag)|設定旗標，表示您自上次儲存後已修改過檔。|
|[CDocument：： SetPathName](#setpathname)|設定檔所使用之資料檔的路徑。|
|[CDocument：： SetTitle](#settitle)|設定檔的標題。|
|[CDocument：： UpdateAllViews](#updateallviews)|通知所有已修改檔的視圖。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[CDocument：： OnFileSendMail](#onfilesendmail)|傳送附有附加檔的郵件訊息。|
|[CDocument：： OnUpdateFileSendMail](#onupdatefilesendmail)|如果有郵件支援，則啟用 [傳送郵件] 命令。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDocument：： m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定 dllhost.exe 為縮圖建立的 `CDocument` 物件。 應該簽入 `CView::OnDraw`。|
|[CDocument：： m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定由 prevhost.exe 為 `Rich Preview`建立 `CDocument` 物件。 應該簽入 `CView::OnDraw`。|
|[CDocument：： m_bSearchMode](#m_bsearchmode)|指定索引子或其他搜尋應用程式所建立的 `CDocument` 物件。|
|[CDocument：： m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定豐富預覽視窗的背景色彩。 此色彩是由主機設定。|
|[CDocument：： m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定豐富預覽視窗的前景色彩。 此色彩是由主機設定。|
|[CDocument：： m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定豐富預覽視窗的文字字型。 此字型資訊是由主機設定。|

## <a name="remarks"></a>備註

檔代表使用者通常會使用 [開啟檔案] 命令開啟的資料單位，並使用 [File Save] 命令來儲存。

`CDocument` 支援標準作業，例如建立檔、加以載入和儲存。 架構會使用 `CDocument`所定義的介面來操控檔。

應用程式可以支援一種以上的檔案類型;例如，應用程式可能同時支援試算表和文字檔。 每一種檔案類型都有相關聯的檔範本。檔範本會指定該檔案類型所使用的資源（例如，功能表、圖示或快速鍵對應表）。 每份檔都包含其相關聯 `CDocTemplate` 物件的指標。

使用者透過與其相關聯的[CView](../../mfc/reference/cview-class.md)物件與檔互動。 View 會在框架視窗中轉譯檔的影像，並將使用者輸入解讀為檔上的作業。 檔可以有多個相關聯的視圖。 當使用者在檔上開啟視窗時，架構會建立一個視圖，並將其附加至檔。 檔範本會指定要使用何種類型的視圖和框架視窗來顯示每一種檔案類型。

檔是架構標準命令路由的一部分，因此會從標準使用者介面元件（例如 [檔案] [儲存] 功能表項目）接收命令。 檔會接收由使用中視圖轉送的命令。 如果檔未處理指定的命令，它會將命令轉送至管理它的檔範本。

修改檔的資料時，每個視圖都必須反映這些修改。 `CDocument` 提供[UpdateAllViews](#updateallviews)成員函式，讓您通知這些變更的視圖，讓視圖可以視需要重新繪製。 此架構也會在關閉修改過的檔案之前，提示使用者加以儲存。

若要在一般應用程式中執行檔，您必須執行下列動作：

- 從 `CDocument` 針對每一種檔案類型衍生類別。

- 新增成員變數以儲存每份檔的資料。

- 執行用來讀取和修改檔資料的成員函式。 檔的 views 是這些成員函式中最重要的使用者。

- 在您的檔類別中覆寫[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)成員函式，以在磁片中寫入和讀取檔的資料。

`CDocument` 支援透過 mail 傳送您的檔（若有郵件支援（MAPI））。 請參閱 MFC 中的[mapi](../../mfc/mapi.md)和[mapi 支援](../../mfc/mapi-support-in-mfc.md)文章。

如需 `CDocument`的詳細資訊，請參閱[序列化](../../mfc/serialization-in-mfc.md)、[檔/視圖架構主題](../../mfc/document-view-architecture.md)和[檔/視圖建立](../../mfc/document-view-creation.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="addview"></a>CDocument：： AddView

呼叫此函式可將視圖附加至檔。

```
void AddView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
指向要加入的視圖。

### <a name="remarks"></a>備註

此函式會將指定的 view 新增至與檔相關聯的視圖清單;函式也會設定此檔的視圖檔指標。 將新建立的 view 物件附加到檔時，架構會呼叫這個函式;這會發生在回應 [新增]、[開啟檔案] 或 [新視窗] 命令，或分割分隔視窗時。

只有在您手動建立和附加視圖時，才呼叫此函式。 通常您會藉由定義[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來關聯檔類別、視圖類別和框架視窗類別，讓架構連接檔和視圖。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>CDocument：： BeginReadChunks

初始化區塊讀取。

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>備註

##  <a name="cancloseframe"></a>CDocument：： CanCloseFrame

在顯示檔的框架視窗關閉之前，由架構呼叫。

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
指向附加至檔之視圖的框架視窗。

### <a name="return-value"></a>傳回值

如果可以安全地關閉框架視窗，則為非零值;否則為0。

### <a name="remarks"></a>備註

預設的執行會檢查是否有其他框架視窗顯示檔。 如果指定的框架視窗是顯示檔的最後一個視窗，則函式會提示使用者儲存檔（如果已修改）。 如果您想要在框架視窗關閉時執行特殊處理，請覆寫這個函數。 這是一個先進的可覆寫。

##  <a name="cdocument"></a>CDocument：： CDocument

建構 `CDocument` 物件。

```
CDocument();
```

### <a name="remarks"></a>備註

架構會為您處理檔的建立。 覆寫[OnNewDocument](#onnewdocument)成員函式，以針對每個檔執行初始化;這在單一檔介面（SDI）應用程式中特別重要。

##  <a name="clearchunklist"></a>CDocument：： ClearChunkList

清除區塊清單。

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>備註

##  <a name="clearpathname"></a>CDocument：： ClearPathName

清除檔物件的路徑。

```
virtual void ClearPathName();
```

### <a name="remarks"></a>備註

清除 `CDocument` 物件的路徑會導致應用程式在下一次儲存檔時提示使用者。 這會讓**save**命令的行為如同 [**另存**新檔] 命令。

##  <a name="deletecontents"></a>CDocument：:D eleteContents

由架構呼叫以刪除檔的資料，而不會摧毀 `CDocument` 物件本身。

```
virtual void DeleteContents();
```

### <a name="remarks"></a>備註

它會在檔被終結之前呼叫。 也會呼叫它，以確保檔在重複使用之前是空的。 對於只使用一份檔的 SDI 應用程式而言，這一點特別重要。每當使用者建立或開啟另一份檔時，就會重複使用此檔。 呼叫此函式可執行 [全部編輯] 或類似的命令，以刪除所有檔的資料。 此函式的預設實作不做任何動作。 覆寫此函數以刪除檔中的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>CDocument：： FindChunk

尋找具有指定之 GUID 的區塊。

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*guid*<br/>
指定要尋找之區塊的 GUID。

*pid*<br/>
指定要尋找之區塊的 PID。

### <a name="return-value"></a>傳回值

如果成功，則為內部區塊清單中的位置。 否則為 Null。

### <a name="remarks"></a>備註

##  <a name="getadapter"></a>CDocument：： GetAdapter

傳回執行 `IDocument` 介面之物件的指標。

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>傳回值

執行 `IDocument` 介面之物件的指標。

### <a name="remarks"></a>備註

##  <a name="getdoctemplate"></a>CDocument：： GetDocTemplate

呼叫此函式可取得此檔案類型之檔範本的指標。

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>傳回值

此檔案類型之檔範本的指標，如果檔不是由檔範本管理，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>CDocument：： GetFile

呼叫這個成員函式以取得 `CFile` 物件的指標。

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
字串，這是所需檔案的路徑。 路徑可以是相對或絕對。

*pError*<br/>
現有檔案例外狀況物件的指標，指出作業的完成狀態。

*nOpenFlags*<br/>
共用和存取模式。 指定開啟檔案時要採取的動作。 您可以使用位 OR （&#124;）運算子，結合 CFile 函數[CFile：： CFile](../../mfc/reference/cfile-class.md#cfile)中列出的選項。 需要一個存取權限和一個共用選項;`modeCreate` 和 `modeNoInherit` 模式是選擇性的。

### <a name="return-value"></a>傳回值

`CFile` 物件的指標。

##  <a name="getfirstviewposition"></a>CDocument：： GetFirstViewPosition

呼叫此函式可取得與檔相關聯的視圖清單中第一個視圖的位置。

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反復專案與[GetNextView](#getnextview)成員函式的位置值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>CDocument：： GetNextView

呼叫此函式可逐一查看所有檔的視圖。

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
先前呼叫 `GetNextView` 或[GetFirstViewPosition](#getfirstviewposition)成員函式所傳回之位置值的參考。 此值不得為 Null。

### <a name="return-value"></a>傳回值

*RPosition*所識別之視圖的指標。

### <a name="remarks"></a>備註

函式會傳回*rPosition*所識別的視圖，然後將*rPosition*設定為清單中下一個視圖的位置值。 如果抓取的視圖是清單中的最後一個，則*rPosition*會設定為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>CDocument：： GetPathName

呼叫此函式可取得檔磁片檔案的完整路徑。

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>傳回值

檔的完整路徑。 如果檔尚未儲存或沒有相關聯的磁片檔案，這個字串會是空的。

##  <a name="getthumbnail"></a>CDocument：： GetThumbnail

建立要由縮圖提供者用來顯示縮圖的點陣圖。

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>參數

*cx*<br/>
指定點陣圖的寬度和高度。

*phbmp*<br/>
當函式傳回成功時，包含點陣圖的控制碼。

*pdwAlpha*<br/>
包含指定 Alpha 色板值的 DWORD （當函式傳回成功時）。

### <a name="return-value"></a>傳回值

如果已成功建立縮圖的點陣圖，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="gettitle"></a>CDocument：： GetTitle

呼叫此函式可取得檔的標題，這通常是從檔的檔案名衍生而來。

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>傳回值

檔的標題。

##  <a name="initializesearchcontent"></a>CDocument：： InitializeSearchContent

呼叫以初始化搜尋處理常式的搜尋內容。

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>備註

覆寫衍生類別中的這個方法，以初始化搜尋內容。 內容應該是包含以 ";" 分隔之元件的字串。 例如，"point;矩形ole 專案」。

##  <a name="ismodified"></a>CDocument：： IsModified

呼叫此函式，以判斷檔自從上次儲存後是否已修改。

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>傳回值

如果檔在上次儲存之後已經修改過，則為非零值;否則為0。

##  <a name="issearchandorganizehandler"></a>CDocument：： IsSearchAndOrganizeHandler

指出是否已針對搜尋 & 組織處理常式建立此 `CDocument` 的實例。

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>傳回值

如果 `CDocument` 的這個實例是針對搜尋 & 組織處理常式所建立，則傳回 TRUE。

### <a name="remarks"></a>備註

目前，此函式只會針對在進程外伺服器中執行的豐富預覽處理常式傳回 TRUE。 您可以在應用層級設定適當的旗標（m_bPreviewHandlerMode、m_bSearchMode、m_bGetThumbnailMode），讓此函式傳回 TRUE。

##  <a name="loaddocumentfromstream"></a>CDocument：： LoadDocumentFromStream

呼叫以從資料流程載入檔資料。

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
資料流程的指標。 這個資料流程是由 Shell 提供。

*dwGrfMode*<br/>
資料流程的存取模式。

### <a name="return-value"></a>傳回值

S_OK，如果載入作業成功，則為，否則為 HRESULT 並出現錯誤代碼。

### <a name="remarks"></a>備註

您可以在衍生類別中覆寫這個方法，以自訂從資料流程載入資料的方式。

##  <a name="m_bgetthumbnailmode"></a>CDocument：： m_bGetThumbnailMode

指定 `CDocument` 物件是由縮圖的 dllhost.exe 所建立。 應該簽入 `CView::OnDraw`。

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>備註

`TRUE` 表示檔是由 dllhost.exe 所建立的縮圖。

##  <a name="m_bpreviewhandlermode"></a>CDocument：： m_bPreviewHandlerMode

指定 prevhost.exe 針對 Rich Preview 所建立的 `CDocument` 物件。 應該簽入 `CView::OnDraw`。

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>備註

TRUE 表示檔是由 prevhost.exe 針對 Rich Preview 所建立。

##  <a name="m_bsearchmode"></a>CDocument：： m_bSearchMode

指定 `CDocument` 物件是由索引子或另一個搜尋應用程式所建立。

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>備註

`TRUE` 表示檔是由索引子或其他搜尋應用程式所建立。

##  <a name="m_clrrichpreviewbackcolor"></a>CDocument：： m_clrRichPreviewBackColor

指定豐富預覽視窗的背景色彩。 此色彩是由主機設定。

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>備註

##  <a name="m_clrrichpreviewtextcolor"></a>CDocument：： m_clrRichPreviewTextColor

指定豐富預覽視窗的前景色彩。 此色彩是由主機設定。

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>備註

##  <a name="m_lfrichpreviewfont"></a>CDocument：： m_lfRichPreviewFont

指定豐富預覽視窗的文字字型。 此字型資訊是由主機設定。

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>備註

##  <a name="onbeforerichpreviewfontchanged"></a>CDocument：： OnBeforeRichPreviewFontChanged

在 Rich Preview 字型變更之前呼叫。

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

##  <a name="onchangedviewlist"></a>CDocument：： OnChangedViewList

在檔中加入或移除視圖之後，由架構呼叫。

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>備註

此函式的預設執行會檢查是否已移除最後一個視圖，如果是的話，則會刪除檔。 如果您想要在架構新增或移除視圖時執行特殊處理，請覆寫此函式。 例如，如果您想要讓檔保持開啟，即使未附加任何視圖，也會覆寫此函式。

##  <a name="onclosedocument"></a>CDocument：： OnCloseDocument

當檔關閉時由架構呼叫，通常是檔案關閉命令的一部分。

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>備註

此函式的預設執行會終結用於查看檔的所有框架、關閉視圖、清除檔的內容，然後呼叫[DeleteContents](#deletecontents)成員函式來刪除檔的資料。

如果您想要在架構關閉檔時執行特殊清除處理，請覆寫此函數。 例如，如果檔代表資料庫中的記錄，您可能會想要覆寫此函數來關閉資料庫。 您應該從您的覆寫呼叫此函式的基類版本。

##  <a name="oncreatepreviewframe"></a>CDocument：： OnCreatePreviewFrame

當架構需要建立用於豐富預覽的預覽畫面格時呼叫。

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>傳回值

如果成功建立框架，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ondocumentevent"></a>CDocument：： OnDocumentEvent

由架構呼叫以回應檔事件。

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>參數

*deEvent*<br/>
在描述事件種類的列舉資料類型。

### <a name="remarks"></a>備註

檔事件可能會影響多個類別。 這個方法負責處理會影響[CDocument 類別](../../mfc/reference/cdocument-class.md)以外之類別的檔事件。 目前，唯一必須回應檔事件的類別是[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument` 類別具有其他覆寫方法，負責處理 `CDocument`的效果。

下表列出*deEvent*的可能值及其對應的事件。

|值|對應的事件|
|-----------|-------------------------|
|`onAfterNewDocument`|已建立新檔。|
|`onAfterOpenDocument`|新檔已開啟。|
|`onAfterSaveDocument`|檔已儲存。|
|`onAfterCloseDocument`|檔已關閉。|

##  <a name="ondrawthumbnail"></a>CDocument：： OnDrawThumbnail

覆寫衍生類別中的這個方法，以繪製縮圖。

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>參數

*dc*<br/>
裝置內容的參考。

*lprcBounds*<br/>
指定應該繪製縮圖之區域的周框。

### <a name="remarks"></a>備註

##  <a name="onfilesendmail"></a>CDocument：： OnFileSendMail

透過常駐郵件主機（如果有的話）以附加檔的方式傳送訊息。

```
void OnFileSendMail();
```

### <a name="remarks"></a>備註

`OnFileSendMail` 會呼叫[OnSaveDocument](#onsavedocument) ，將未命名和修改過的檔序列化（儲存）至暫存檔，然後透過電子郵件傳送該檔案。 如果檔尚未修改，則不需要暫存檔案;會傳送原始的。 `OnFileSendMail` 載入 MAPI32.DLL。DLL （如果尚未載入的話）。

`OnFileSendMail` 的特殊實[COleDocument](../../mfc/reference/coledocument-class.md)會正確地處理複合檔案。

`CDocument` 支援透過 mail 傳送您的檔（若有郵件支援（MAPI））。 請參閱 MFC 中的[Mapi 主題](../../mfc/mapi.md)和[mapi 支援](../../mfc/mapi-support-in-mfc.md)文章。

##  <a name="onloaddocumentfromstream"></a>CDocument：： OnLoadDocumentFromStream

需要從資料流程載入檔資料時，由架構呼叫。

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
連入資料流程的指標。

*grfMode*<br/>
資料流程的存取模式。

### <a name="return-value"></a>傳回值

如果載入成功，則 S_OK;否則為錯誤碼。

### <a name="remarks"></a>備註

##  <a name="onnewdocument"></a>CDocument：： OnNewDocument

由架構呼叫，做為 [檔案] [新增] 命令的一部分。

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>傳回值

如果成功初始化檔，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式的預設執行會呼叫[DeleteContents](#deletecontents)成員函式，以確保檔是空的，然後將新檔標記為清除。 覆寫此函式，以初始化新檔的資料結構。 您應該從您的覆寫呼叫此函式的基類版本。

如果使用者在 SDI 應用程式中選擇 [檔案] [新增] 命令，此架構會使用這個函數來重新初始化現有的檔，而不是建立新的檔。 如果使用者在多重文件介面（MDI）應用程式中選擇 [新增檔案]，則架構會每次建立新的檔，然後呼叫此函式將它初始化。 您必須將初始化程式碼放在此函式中，而不是在 [檔案] [新增] 命令的函式中，以便在 SDI 應用程式中生效。

請注意，在某些情況下，會呼叫 `OnNewDocument` 兩次。 當檔內嵌為 ActiveX 檔案伺服器時，就會發生這種情況。 函式會先由 `CreateInstance` 方法（由 `COleObjectFactory`衍生類別所公開）和第二次由 `InitNew` 方法（由 `COleServerDoc`衍生類別公開）所呼叫。

### <a name="example"></a>範例

下列範例說明初始化檔物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>CDocument：： OnOpenDocument

由架構呼叫，做為 File Open 命令的一部分。

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向要開啟之檔的路徑。

### <a name="return-value"></a>傳回值

如果檔載入成功，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式的預設實作用會開啟指定的檔案，呼叫[DeleteContents](#deletecontents)成員函式以確保檔是空的，呼叫[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)以讀取檔案的內容，然後將檔標示為清除。 如果您想要使用封存機制以外的其他專案或檔案機制，請覆寫此函數。 例如，您可以撰寫應用程式，其中檔代表資料庫中的記錄，而不是個別的檔案。

如果使用者在 SDI 應用程式中選擇 [檔案] [開啟] 命令，此架構會使用此函式重新初始化現有的 `CDocument` 物件，而不是建立新的物件。 如果使用者選擇在 MDI 應用程式中開啟檔案，架構會每次都建立一個新的 `CDocument` 物件，然後呼叫此函式將它初始化。 您必須將初始化程式碼放在此函式中，而不是在函數的函式中，以便在 SDI 應用程式中生效。

### <a name="example"></a>範例

下列範例說明初始化檔物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>CDocument：： OnPreviewHandlerQueryFocus

指示預覽處理常式傳回從呼叫 `GetFocus` 函式所抓取的 HWND。

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>參數

*phwnd*<br/>
脫銷當這個方法傳回時，會包含從預覽處理常式的前景執行緒呼叫 `GetFocus` 函式所傳回 HWND 的指標。

### <a name="return-value"></a>傳回值

如果成功，則傳回 S_OK;或錯誤值，否則為。

### <a name="remarks"></a>備註

##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument：： OnPreviewHandlerTranslateAccelerator

引導預覽處理常式處理從預覽處理常式執行所在進程的訊息提取傳遞的按鍵。

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>參數

*pmsg*<br/>
在視窗訊息的指標。

### <a name="return-value"></a>傳回值

如果可由預覽處理常式處理按鍵訊息，則處理常式會處理它，並傳回 S_OK。 如果預覽處理常式無法處理按鍵訊息，它會透過 `IPreviewHandlerFrame::TranslateAccelerator`將其提供給主機。 如果主機處理訊息，這個方法會傳回 S_OK。 如果主機未處理訊息，這個方法會傳回 S_FALSE。

### <a name="remarks"></a>備註

##  <a name="onrichpreviewbackcolorchanged"></a>CDocument：： OnRichPreviewBackColorChanged

當豐富的預覽背景色彩已變更時呼叫。

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewfontchanged"></a>CDocument：： OnRichPreviewFontChanged

當豐富的預覽字型已變更時呼叫。

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewsitechanged"></a>CDocument：： OnRichPreviewSiteChanged

當豐富的預覽網站已變更時呼叫。

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>備註

##  <a name="onrichpreviewtextcolorchanged"></a>CDocument：： OnRichPreviewTextColorChanged

當豐富的預覽文字色彩已變更時呼叫。

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>備註

##  <a name="onsavedocument"></a>CDocument：： OnSaveDocument

由架構在 [檔案] [儲存] 或 [檔案] [另存新檔] 命令中呼叫。

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向應該儲存檔案的完整路徑。

### <a name="return-value"></a>傳回值

如果成功儲存檔，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式的預設實作用會開啟指定的檔案，呼叫[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)以將檔的資料寫入檔案，然後將檔標示為清除。 如果您想要在架構儲存檔時執行特殊處理，請覆寫此函數。 例如，您可以撰寫應用程式，其中檔代表資料庫中的記錄，而不是個別的檔案。

##  <a name="onunloadhandler"></a>CDocument：： OnUnloadHandler

在卸載預覽處理常式時，由架構呼叫。

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>備註

##  <a name="onupdatefilesendmail"></a>CDocument：： OnUpdateFileSendMail

如果郵件支援（MAPI）存在，則啟用 ID_FILE_SEND_MAIL 命令。

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
與 ID_FILE_SEND_MAIL 命令相關聯之[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

### <a name="remarks"></a>備註

否則，函式會從功能表中移除 ID_FILE_SEND_MAIL 命令，並視需要在功能表項目的上方或下方包含分隔符號。 如果 MAPI32.DLL，則會啟用 MAPI。DLL 存在於路徑中，而在 WIN 的 [Mail] 區段中。INI 檔，MAPI = 1。 大部分的應用程式都會將此命令放在 [檔案] 功能表上。

`CDocument` 支援透過 mail 傳送您的檔（若有郵件支援（MAPI））。 請參閱 MFC 中的[Mapi 主題](../../mfc/mapi.md)和[mapi 支援](../../mfc/mapi-support-in-mfc.md)文章。

##  <a name="precloseframe"></a>CDocument：:P reCloseFrame

這個成員函式是由架構在框架視窗終結之前呼叫。

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
包含相關聯 `CDocument` 物件之[CFrameWnd](../../mfc/reference/cframewnd-class.md)的指標。

### <a name="remarks"></a>備註

您可以覆寫它來提供自訂清除，但也請務必呼叫基類。

`PreCloseFrame` 的預設值不會在 `CDocument`中執行任何操作。 `CDocument`衍生的類別[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)會使用此成員函式。

##  <a name="readnextchunkvalue"></a>CDocument：： ReadNextChunkValue

讀取下一個區塊值。

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>參數

*ppValue*<br/>
脫銷當函式傳回時， *ppValue*會包含已讀取的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

##  <a name="releasefile"></a>CDocument：： ReleaseFile

此成員函式是由架構呼叫，以釋放檔案，讓其他應用程式可以使用它。

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>參數

*pFile*<br/>
要釋放之 CFile 物件的指標。

*bAbort*<br/>
指定是否要使用 `CFile::Close` 或 `CFile::Abort`釋放檔案。 如果要使用[CFile：： Close](../../mfc/reference/cfile-class.md#close)釋放檔案，則為 FALSE;如果要使用[CFile：： Abort](../../mfc/reference/cfile-class.md#abort)釋放檔案，則為 TRUE。

### <a name="remarks"></a>備註

如果*bAbort*為 TRUE，`ReleaseFile` 會呼叫 `CFile::Abort`，並釋放檔案。 `CFile::Abort` 不會擲回例外狀況。

如果*bAbort*為 FALSE，`ReleaseFile` 會呼叫 `CFile::Close` 並且釋放檔案。

覆寫這個成員函式，以在釋放檔案之前要求使用者採取動作。

##  <a name="removechunk"></a>CDocument：： RemoveChunk

移除具有指定之 GUID 的區塊。

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*Guid*<br/>
指定要移除之區塊的 GUID。

*P&id*<br/>
指定要移除之區塊的 PID。

### <a name="remarks"></a>備註

##  <a name="removeview"></a>CDocument：： RemoveView

呼叫此函式可從檔卸離視圖。

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
指向要移除的視圖。

### <a name="remarks"></a>備註

此函式會從與檔相關聯的視圖清單中移除指定的 view;它也會將視圖的檔指標設定為 Null。 當框架視窗關閉或分隔器視窗的窗格關閉時，架構會呼叫這個函式。

只有在您手動卸離視圖時，才能呼叫此函式。 通常您會藉由定義[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來關聯檔類別、視圖類別和框架視窗類別，讓架構卸離檔和視圖。

如需範例執行，請參閱[AddView](#addview)的範例。

##  <a name="reportsaveloadexception"></a>CDocument：： ReportSaveLoadException

在儲存或載入檔時，如果擲回例外狀況（通常是[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveException](../../mfc/reference/carchiveexception-class.md)），則會呼叫。

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向正在儲存或載入之檔的名稱。

*e*<br/>
指向所擲回的例外狀況。 可能是 NULL。

*bSaving*<br/>
指出正在進行哪些作業的旗標;如果正在儲存檔，則為非零，如果正在載入檔，則為0。

*nIDPDefault*<br/>
當函式未指定更明確的錯誤訊息時，所要顯示的錯誤訊息識別碼。

### <a name="remarks"></a>備註

預設的實作為檢查例外狀況物件，並尋找特別描述原因的錯誤訊息。 如果找不到特定的訊息，或如果*e*是 Null，則會使用*nIDPDefault*參數所指定的一般訊息。 然後，函式會顯示包含錯誤訊息的訊息方塊。 如果您想要提供其他自訂的失敗訊息，請覆寫此函數。 這是一個先進的可覆寫。

##  <a name="savemodified"></a>CDocument：： SaveModified

在修改的檔即將關閉之前，由架構呼叫。

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>傳回值

如果可以安全地繼續並關閉檔，則為非零值。如果不應關閉檔，則為0。

### <a name="remarks"></a>備註

此函式的預設執行會顯示訊息方塊，詢問使用者是否要儲存檔的變更（如果有的話）。 如果您的程式需要不同的提示程式，請覆寫此函式。 這是一個先進的可覆寫。

##  <a name="setchunkvalue"></a>CDocument：： SetChunkValue

設定區塊值。

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指定要設定的區塊值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

##  <a name="setmodifiedflag"></a>CDocument：： SetModifiedFlag

在您對檔進行任何修改之後，請呼叫此函式。

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
表示檔是否已修改的旗標。

### <a name="remarks"></a>備註

藉由一致地呼叫此函式，您可以確保架構在關閉檔之前，會提示使用者儲存變更。 通常，您應該使用*bModified*參數的預設值 TRUE。 若要將檔標記為清除（未修改），請呼叫此函式，並將值設為 FALSE。

##  <a name="setpathname"></a>CDocument：： SetPathName

呼叫此函式可指定檔磁片檔案的完整路徑。

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
指向要用來做為檔路徑的字串。

*bAddToMRU*<br/>
判斷檔案名是否已加入最近使用的（MRU）檔案清單。 若為 TRUE，則會加入檔案名;如果為 FALSE，則不會新增。

### <a name="remarks"></a>備註

視*bAddToMRU*的值而定，路徑會加入或不會加入至應用程式所維護的 MRU 清單。 請注意，有些檔不會與磁片檔案相關聯。 只有當您要覆寫用於開啟和儲存架構所使用之檔案的預設執行時，才能呼叫此函式。

##  <a name="settitle"></a>CDocument：： SetTitle

呼叫此函式可指定檔的標題（顯示在框架視窗標題列中的字串）。

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
指向要當做檔標題使用的字串。

### <a name="remarks"></a>備註

呼叫此函式會更新顯示檔之所有框架視窗的標題。

##  <a name="updateallviews"></a>CDocument：： UpdateAllViews

在檔修改後呼叫此函式。

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改檔的視圖，如果要更新所有的視圖，則為 Null。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
指向儲存修改相關資訊的物件。

### <a name="remarks"></a>備註

呼叫[SetModifiedFlag](#setmodifiedflag)成員函式之後，您應該呼叫這個函式。 此函式會通知每一個視圖附加至檔，但*pSender*指定的視圖除外，已修改過該檔。 您通常會在使用者透過視圖變更檔之後，從 view 類別呼叫這個函式。

此函式會針對每個檔的視圖呼叫[CView：： OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函式，但傳送視圖除外，傳遞*pHint*和*lHint*。 使用這些參數，將資訊傳遞給對檔所做修改的相關觀點。 您可以使用*lHint*和/或來編碼資訊，您可以定義[CObject](../../mfc/reference/cobject-class.md)衍生類別來儲存修改的相關資訊，並使用*pHint*傳遞該類別的物件。 在您的[CView](../../mfc/reference/cview-class.md)衍生類別中覆寫 `CView::OnUpdate` 成員函式，以根據傳遞的資訊優化視圖顯示的更新。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
