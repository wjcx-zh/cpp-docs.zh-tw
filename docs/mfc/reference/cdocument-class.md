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
ms.openlocfilehash: 2f8ba8d0b35bd72efa8f8d63dbefd689e645d768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374041"
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
|[CDocument:CDocument](#cdocument)|建構 `CDocument` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocument::新增檢視](#addview)|將檢視附加到文檔。|
|[CDocument::開始閱讀](#beginreadchunks)|初始化塊讀取。|
|[CDocument::可以關閉框架](#cancloseframe)|高級可重寫;在關閉查看此文件的框架視窗之前調用。|
|[CDocument:清除區塊清單](#clearchunklist)|清除塊清單。|
|[CDocument:: 清除路徑名稱](#clearpathname)|清除文件物件的路徑。|
|[CDocument::D內容](#deletecontents)|調用 以執行文檔的清理。|
|[CDocument::尋找區塊](#findchunk)|尋找具有指定 GUID 的塊。|
|[CDocument::取得配接器](#getadapter)|返回指向對象`IDocument`實現 介面的指標。|
|[CDocument::取得文件樣本](#getdoctemplate)|返回指向描述文檔類型的文件範本的指標。|
|[CDocument::取得檔案](#getfile)|返回指向所需`CFile`物件的指標。|
|[CDocument:取得第一檢視位置](#getfirstviewposition)|返回檢視清單中第一個位置;用於開始反覆運算。|
|[CDocument::取得下一個檢視](#getnextview)|通過與文檔關聯的檢視清單進行一次遍視。|
|[CDocument::取得路徑名稱](#getpathname)|返回文件數據檔的路徑。|
|[CDocument::取得縮圖](#getthumbnail)|呼叫 以建立要由縮圖提供程式用於顯示縮圖的點陣圖。|
|[CDocument::取得標題](#gettitle)|返回文件的標題。|
|[CDocument::初始化搜尋內容](#initializesearchcontent)|已調用以初始化搜索處理程式的搜尋內容。|
|[CDocument::已修改](#ismodified)|指示自上次保存文檔以來是否已修改文檔。|
|[CDocument::正在搜尋和組織處理程式](#issearchandorganizehandler)|告知此`CDocument`物件實例是否為搜索&組織處理程序創建。|
|[CDocument::從流載入文件](#loaddocumentfromstream)|調用以載入流中的文件數據。|
|[CDocument::在裡希預覽字型更改之前開啟](#onbeforerichpreviewfontchanged)|在更改「富預覽」字體之前調用。|
|[CDocument::開啟檢視清單](#onchangedviewlist)|在將檢視添加到文檔或從文件中刪除後調用。|
|[CDocument::開啟文件](#onclosedocument)|已調用以關閉文檔。|
|[CDocument::在建立預覽框架](#oncreatepreviewframe)|當需要為富預覽創建預覽框架時,由框架調用。|
|[CDocument::在文件事件](#ondocumentevent)|框架為回應文檔事件而調用。|
|[CDocument::在縮略圖上](#ondrawthumbnail)|重寫派生類中的此方法以繪製縮略圖的內容。|
|[CDocument::從流載入文件](#onloaddocumentfromstream)|當需要從流載入文件數據時,由框架調用。|
|[CDocument::關於新文件](#onnewdocument)|調用以創建新文檔。|
|[CDocument::開啟文件](#onopendocument)|已調用以打開現有文檔。|
|[CDocument::在預覽處理程序查詢焦點](#onpreviewhandlerqueryfocus)|指示預覽處理程式從調用 GetFocus 函數返回 HWND。|
|[CDocument::在預覽處理程式翻譯加速器](#onpreviewhandlertranslateaccelerator)|指示預覽處理程序處理從運行預覽處理程序的進程的消息泵傳入的擊鍵。|
|[CDocument::在裡希預覽背面顏色已更改](#onrichpreviewbackcolorchanged)|在「富預覽」背景顏色已更改時調用。|
|[CDocument::在裡希預覽字體上](#onrichpreviewfontchanged)|在「富預覽」字體已更改時調用。|
|[CDocument::在裡希預覽網站更改](#onrichpreviewsitechanged)|在「豐富預覽」網站已更改時調用。|
|[CDocument::在裡希預覽文字顏色修改](#onrichpreviewtextcolorchanged)|在「富預覽」文本顏色已更改時調用。|
|[CDocument::儲存文件上](#onsavedocument)|調用以將文檔保存到磁碟。|
|[CDocument::開啟卸載處理程式](#onunloadhandler)|在卸載預覽處理程式時由框架調用。|
|[CDocument::P重新關閉框架](#precloseframe)|在框架視窗關閉之前調用。|
|[CDocument::閱讀下一個塊值](#readnextchunkvalue)|讀取下一個塊值。|
|[CDocument::發佈檔案](#releasefile)|釋放檔,使其可供其他應用程式使用。|
|[CDocument::刪除區塊](#removechunk)|刪除具有指定 GUID 的塊。|
|[CDocument::刪除檢視](#removeview)|從文檔分離視圖。|
|[CDocument:報告儲存載入異常](#reportsaveloadexception)|高級可重寫;當由於異常而無法完成打開或保存操作時調用。|
|[CDocument::儲存修改](#savemodified)|高級可重寫;調用 以詢問使用者是否應保存文檔。|
|[CDocument::設定區塊值](#setchunkvalue)|設置塊值。|
|[CDocument::設定修改後的 Flag](#setmodifiedflag)|設置一個標誌,指示自上次保存文檔以來已修改文檔。|
|[CDocument::設定路徑名稱](#setpathname)|設置文件使用的數據檔的路徑。|
|[CDocument::設定標題](#settitle)|設置文件的標題。|
|[CDocument::更新所有檢視](#updateallviews)|通知文檔已修改的所有檢視。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDocument::在檔案傳送郵件](#onfilesendmail)|發送附有文件的郵件。|
|[CDocument::更新檔案傳送郵件](#onupdatefilesendmail)|如果存在郵件支援,請啟用「發送郵件」命令。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定該`CDocument`物件由縮略圖的 dllhost 創建。 應簽入`CView::OnDraw`。|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定物件`CDocument`由的預主`Rich Preview`為創建。 應簽入`CView::OnDraw`。|
|[CDocument:m_bSearchMode](#m_bsearchmode)|指定`CDocument`物件由索引器或其他搜索應用程式創建。|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定「富預覽」視窗的背景顏色。 此顏色由主機設置。|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定「富預覽」視窗的前景顏色。 此顏色由主機設置。|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|為「富預覽」視窗指定文本字型。 此字體資訊由主機設置。|

## <a name="remarks"></a>備註

文件表示使用者通常使用檔案打開命令打開的數據單元,並保存檔保存命令。

`CDocument`支援標準操作,如創建文檔、載入文件和保存文檔。 框架使用 定義`CDocument`的 介面操作文檔。

應用程式可以支援多種類型的文檔;但是,應用程式可以支援多種類型的文檔。例如,應用程式可能同時支援電子表格和文本文檔。 每種類型的文檔都有關聯的文檔範本;文檔範本指定用於該類型文件的資源(例如,功能表、圖示或快速鍵表)。 每個文檔都包含指向其`CDocTemplate`關聯 物件的指標。

用戶透過與其關聯的[CView](../../mfc/reference/cview-class.md)物件與文件進行互動。 檢視在框架視窗中呈現文件的圖像,並將使用者輸入解釋為對文件的操作。 文檔可以有多個與其關聯的視圖。 當使用者打開文檔上的視窗時,框架將創建一個檢視並將其附加到文檔。 文件範本指定用於顯示每種文件類型的檢視和框架視窗的類型。

文檔是框架的標準命令路由的一部分,因此接收來自標準使用者介面元件的命令(如檔保存功能表項)。 文件接收活動檢視轉發的命令。 如果文件不處理給定命令,它將該命令轉發給管理該命令的文檔範本。

修改文檔數據時,其每個檢視都必須反映這些修改。 `CDocument`提供[UpdateAllViews](#updateallviews)成員函數,以便通知您此類更改的檢視,以便檢視可以根據需要重新繪製它們。 框架還提示使用者在關閉修改後的檔案之前保存該檔。

要在典型應用程式中實現文件,必須執行以下操作:

- 從`CDocument`每種類型的文檔派生類。

- 添加成員變數以存儲每個文件的數據。

- 實現用於讀取和修改文檔數據的成員函數。 文檔的檢視是這些成員函數的最重要使用者。

- 覆蓋[CObject::序列化](../../mfc/reference/cobject-class.md#serialize)文件類別中的成員函數,以在磁碟和磁碟中寫入和讀取文件的資料。

`CDocument`支援通過郵件支援 (MAPI) 傳送文件。 請參閱 MFC 中的[MAPI](../../mfc/mapi.md)和[MAPI 支援](../../mfc/mapi-support-in-mfc.md)文章。

有關`CDocument`的詳細資訊,請參閱[序列化](../../mfc/serialization-in-mfc.md)、[文件/檢視體系結構主題](../../mfc/document-view-architecture.md)與[文件/檢視建立](../../mfc/document-view-creation.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::新增檢視

調用此函數以將檢視附加到文檔。

```
void AddView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
指向要添加的視圖。

### <a name="remarks"></a>備註

此函數將指定的檢視添加到與文檔關聯的檢視清單中;該函數還設置檢視的文件指標到此文檔。 將新創建的檢視物件附加到文檔時,框架將調用此功能;這將用於回應檔新建、檔案打開或新建視窗命令或拆分視窗時發生的。

僅當手動創建和附加檢視時,才調用此功能。 通常,通過定義[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來關聯文檔類、視圖類和框架視窗類,允許框架連接文檔和視圖。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::開始閱讀

初始化塊讀取。

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>備註

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::可以關閉框架

框架在關閉顯示文檔的框架視窗之前調用。

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
指向附加到文檔的檢視的幀視窗。

### <a name="return-value"></a>傳回值

如果可以安全地關閉框架視窗,則非零;否則 0。

### <a name="remarks"></a>備註

預設實現檢查是否有其他框架視窗顯示文檔。 如果指定的框架視窗是顯示文件的最後一個框架視窗,則函數將提示使用者保存文檔(如果文檔已被修改)。 如果要在框架視窗關閉時執行特殊處理,則重寫此函數。 這是一個高級的可重寫。

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument:CDocument

建構 `CDocument` 物件。

```
CDocument();
```

### <a name="remarks"></a>備註

框架為您處理文件創建。 覆蓋[OnNewDocument](#onnewdocument)成員函數,以按文檔執行初始化;這在單文檔介面 (SDI) 應用程式中尤其重要。

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument:清除區塊清單

清除塊清單。

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>備註

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument:: 清除路徑名稱

清除文件物件的路徑。

```
virtual void ClearPathName();
```

### <a name="remarks"></a>備註

從`CDocument`物件清除路徑會導致應用程式在下次保存文檔時提示使用者。 這使得 **「保存」** 命令類似於 **「保存為」** 命令。

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::D內容

由框架調用以刪除文檔的數據而不`CDocument`破壞 物件本身。

```
virtual void DeleteContents();
```

### <a name="remarks"></a>備註

在銷毀文檔之前調用它。 還調用它以確保文檔在重用之前為空。 這對僅使用一個文檔的 SDI 應用程式尤其重要;每當用戶創建或打開另一個文檔時,文檔都會被重用。 呼叫此函數以實現刪除文件所有資料的"全部編輯清除"或類似命令。 此函式的預設實作不做任何動作。 重寫此函數以刪除文件中的數據。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::尋找區塊

尋找具有指定 GUID 的塊。

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*Guid*<br/>
指定要查找的塊的 GUID。

*pid*<br/>
指定要尋找的塊的 PID。

### <a name="return-value"></a>傳回值

如果成功,則位於內部區塊清單中的位置。 否則 NULL。

### <a name="remarks"></a>備註

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::取得配接器

返回指向實現介面的物件的`IDocument`指標。

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>傳回值

指向實現介面的物件的`IDocument`指標。

### <a name="remarks"></a>備註

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::取得文件樣本

呼叫此函數以獲取指向此文件類型的文件範本的指標。

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>傳回值

指向此文件類型的文件範本的指標,如果文檔不是由文檔範本管理,則指向 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::取得檔案

調用此成員函數以獲取指向`CFile`物件的指標。

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
是所需檔的路徑的字串。 路徑可以是相對路徑,也可以是絕對路徑。

*pError*<br/>
指向指示操作完成狀態的現有文件異常物件的指標。

*nOpenFlags*<br/>
共用和訪問模式。 指定開啟檔時要執行的操作。 您可以使用位或(&#124;)運算符組合 CFile 建構函數[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)中列出的選項。 需要一個訪問許可權和一個共用選項;`modeCreate`和`modeNoInherit`模式是可選的。

### <a name="return-value"></a>傳回值

`CFile` 物件的指標。

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument:取得第一檢視位置

呼叫此函數以獲取有關文件關聯的檢視清單中第一個檢視的位置。

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>傳回值

可用於使用[GetNextView](#getnextview)成員函數進行反覆運算的定位值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::取得下一個檢視

調用此函數以遍接文檔的所有檢視。

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*r 定位*<br/>
對前一個調用`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成員函數返回的定位值的引用。 此值不能為 NULL。

### <a name="return-value"></a>傳回值

指向 r 定位識別的檢視*的指標*。

### <a name="remarks"></a>備註

函數傳回*由 r定位*識別的檢視,然後將*r 定位*設定到清單中下一個檢視的「位置」值。 如果檢索到的檢視是清單中的最後一個檢視,則*r定位*設置為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::取得路徑名稱

呼叫此函數獲取文檔磁碟檔的完全限定路徑。

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>傳回值

文檔的完全限定路徑。 如果文檔尚未保存或沒有與其關聯的磁碟檔,則此字串為空。

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::取得縮圖

創建要由縮圖提供程式用於顯示縮圖的點陣圖。

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>參數

*殘雪*<br/>
指定點陣圖的寬度和高度。

*phbmp*<br/>
當函數成功返回時,包含位圖的句柄。

*pdwAlpha*<br/>
包含指定 Alpha 通道值的 DWORD,當函數成功返回時。

### <a name="return-value"></a>傳回值

如果成功創建了縮略圖的位圖,則返回 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::取得標題

呼叫此函數獲取文件的標題,該標題通常派生自文檔的檔名。

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>傳回值

文件的標題。

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::初始化搜尋內容

已調用以初始化搜索處理程式的搜尋內容。

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>備註

重寫派生類中的此方法以初始化搜索內容。 內容應為字串,其部分以";"分隔。 例如,"點;"矩形;ole 專案"。

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument::已修改

調用此函數以確定文檔自上次保存以來是否已修改。

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>傳回值

自上次保存文檔以來已修改的文檔,則非零;否則 0。

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::正在搜尋和組織處理程式

說明是否為搜索&`CDocument`組織處理程式創建了此實例。

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>傳回值

如果為搜索&組織處理程式`CDocument`創建了此實例,則返回 TRUE。

### <a name="remarks"></a>備註

目前,此函數僅對在行程外伺服器中實現的富預覽處理程式返回 TRUE。 您可以在應用程式級別設置適當的標誌(m_bPreviewHandlerMode、m_bSearchMode、m_bGetThumbnailMode),以使此函數返回 TRUE。

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::從流載入文件

調用以載入流中的文件數據。

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
指向流的指標。 此流由 Shell 提供。

*德夫格夫莫德*<br/>
訪問流模式。

### <a name="return-value"></a>傳回值

如果載入操作成功,S_OK,否則使用錯誤代碼的 HRESULT。

### <a name="remarks"></a>備註

可以在派生類中重寫此方法,以自定義如何從流中載入數據。

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

指定`CDocument`物件由縮略圖的 dllhost 創建。 應簽入`CView::OnDraw`。

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>備註

`TRUE`指示文件是由縮略圖的 dllhost 創建的。

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

指定`CDocument`物件由富預覽的前主創建。 應簽入`CView::OnDraw`。

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>備註

TRUE 表示文檔是由「富預覽」的前主創建的。

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument:m_bSearchMode

指定`CDocument`物件由索引器或其他搜索應用程式創建。

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>備註

`TRUE`指示文檔是由索引器或其他搜索應用程式創建的。

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

指定「富預覽」視窗的背景顏色。 此顏色由主機設置。

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>備註

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

指定「富預覽」視窗的前景顏色。 此顏色由主機設置。

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>備註

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

指定「富預覽」視窗的文字字型。 此字體資訊由主機設置。

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>備註

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::在裡希預覽字型更改之前開啟

在更改「富預覽」字體之前調用。

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::開啟檢視清單

在將檢視添加到文檔或從文檔中刪除檢視後由框架調用。

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>備註

此函數的默認實現檢查是否刪除了最後一個檢視,如果是,則刪除文檔。 如果要在框架添加或刪除檢視時執行特殊處理,則重寫此函數。 例如,如果希望文檔保持打開狀態,即使文檔沒有附加檢視,則重寫此函數。

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::開啟文件

在文件關閉時由框架調用,通常作為檔關閉命令的一部分調用。

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>備註

此函數的預設實現將銷毀用於查看文檔的所有幀、關閉檢視、清理文檔內容,然後調用[DeleteContents](#deletecontents)成員函數刪除文檔的資料。

如果要在框架關閉文檔時執行特殊的清理處理,請覆蓋此函數。 例如,如果文檔表示資料庫中的記錄,則可能需要重寫此函數以關閉資料庫。 應從重寫調用此函數的基類版本。

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::在建立預覽框架

當需要為富預覽創建預覽框架時,由框架調用。

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>傳回值

如果框架已成功創建,則返回 TRUE;如果框架已成功創建,則返回 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::在文件事件

框架為回應文檔事件而調用。

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>參數

*deEvent*<br/>
[在]描述事件類型的枚舉數據類型。

### <a name="remarks"></a>備註

文檔事件可能會影響多個類。 此方法負責處理影響[CDocument 類](../../mfc/reference/cdocument-class.md)以外的類的文檔事件。 目前,必須回應文件事件的唯一類是[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 類別`CDocument`還有其他可重寫的方法,負責處理對`CDocument`的影響 。

下表列出了*deEvent*的可能值及其對應的事件。

|值|相應的事件|
|-----------|-------------------------|
|`onAfterNewDocument`|已創建新文檔。|
|`onAfterOpenDocument`|打開了一個新文檔。|
|`onAfterSaveDocument`|文檔已保存。|
|`onAfterCloseDocument`|文件已關閉。|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::在縮略圖上

重寫派生類中的此方法以繪製縮略圖。

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>參數

*直流*<br/>
對設備上下文的引用。

*lprcBounds*<br/>
指定應繪製縮略圖的區域的邊界矩形。

### <a name="remarks"></a>備註

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::在檔案傳送郵件

通過駐留郵件主機(如果有)發送郵件,並將文檔作為附件。

```
void OnFileSendMail();
```

### <a name="remarks"></a>備註

`OnFileSendMail`調用[OnSaveDocument](#onsavedocument)將無標題和修改的文檔序列化(保存)到暫存檔案,然後透過電子郵件發送。 如果文檔尚未修改,則不需要臨時檔;因此,不需要臨時檔。原始檔已發送。 `OnFileSendMail`載入 MAPI32。尚未載入 DLL。

[COleDocument](../../mfc/reference/coledocument-class.md)`OnFileSendMail`的特殊實現可正確處理複合檔。

`CDocument`支援通過郵件支援 (MAPI) 傳送文件。 請參閱 MFC 中的[MAPI 主題](../../mfc/mapi.md)和[MAPI 支援](../../mfc/mapi-support-in-mfc.md)文章。

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::從流載入文件

當需要從流載入文件數據時,由框架調用。

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>參數

*pStream*<br/>
指向傳入流的指標。

*grfMode*<br/>
訪問流模式。

### <a name="return-value"></a>傳回值

如果負載成功,S_OK;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::關於新文件

框架作為"檔新"命令的一部分調用。

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>傳回值

如果文檔已成功初始化,則非零;否則 0。

### <a name="remarks"></a>備註

此函數的預設實現調用[DeleteContents](#deletecontents)成員函數,以確保文檔為空,然後將新文檔標記為乾淨。 重寫此函數以初始化新文件的數據結構。 應從重寫調用此函數的基類版本。

如果使用者在 SDI 應用程式中選擇「檔新」命令,則框架使用此函數重新初始化現有文檔,而不是創建新文檔。 如果使用者在多個文檔介面 (MDI) 應用程式中選擇「檔案新建」,則框架每次都會創建新文檔,然後調用此函數進行初始化。 您必須將初始化代碼放在此函數中,而不是將初始化代碼放在建構函數中,以便 File New 命令在 SDI 應用程式中有效。

請注意,在某些情況下`OnNewDocument`,調用兩次。 當文檔嵌入為 ActiveX 文件伺服器時,將發生這種情況。 函數`CreateInstance`首先由方法調用`COleObjectFactory`( 由派生類公開),第二`InitNew`次由 方法調`COleServerDoc`用(由 派生類公開)。

### <a name="example"></a>範例

以下範例說明了初始化文件物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::開啟文件

框架作為文件打開命令的一部分調用。

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
指向要打開的文檔的路徑。

### <a name="return-value"></a>傳回值

如果文檔已成功載入,則非零;否則 0。

### <a name="remarks"></a>備註

此函數的預設實現將打開指定的文件,調用[DeleteContents](#deletecontents)成員函數以確保文件為空,調用[CObject::序列化](../../mfc/reference/cobject-class.md#serialize)以讀取檔的內容,然後將文檔標記為乾淨。 如果要使用存檔機制或檔機制以外的內容,則重寫此函數。 例如,可以編寫一個應用程式,其中文檔表示資料庫中的記錄,而不是單獨的檔。

如果使用者在 SDI 應用程式中選擇「檔案打開」命令,則框架使用此函數重新初始`CDocument`化現有 物件,而不是創建新物件。 如果使用者在 MDI 應用程式中選擇「檔打開」,則框架每次都會建`CDocument`構一 個新物件,然後調用此函數來初始化它。 您必須將初始化代碼放在此函數中,而不是將文件打開命令放在建構函數中,才能在 SDI 應用程式中有效。

### <a name="example"></a>範例

以下範例說明了初始化文件物件的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::在預覽處理程序查詢焦點

指示預覽處理程式返回從調用`GetFocus`函數中檢索到的 HWND。

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>參數

*phwnd*<br/>
[出]當此方法返回時,包含從預覽處理程式的前景線程調用`GetFocus`函數返回的 HWND 的指標。

### <a name="return-value"></a>傳回值

如果成功,返回S_OK;或錯誤值,否則。

### <a name="remarks"></a>備註

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::在預覽處理程式翻譯加速器

指示預覽處理程序處理從運行預覽處理程序的進程的消息泵傳入的擊鍵。

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>參數

*pmsg*<br/>
[在]指向視窗消息的指標。

### <a name="return-value"></a>傳回值

如果預覽處理程式可以處理擊鍵消息,則處理程式將處理該消息並返回S_OK。 如果預覽處理程式無法處理擊鍵消息,則通過`IPreviewHandlerFrame::TranslateAccelerator`向主機提供該消息。 如果主機處理消息,此方法將返回S_OK。 如果主機不處理消息,此方法將返回S_FALSE。

### <a name="remarks"></a>備註

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::在裡希預覽背面顏色已更改

當「富預覽」背景顏色已更改時調用。

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::在裡希預覽字體上

當「富預覽」字體已更改時調用。

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::在裡希預覽網站更改

在「豐富預覽」網站已更改時調用。

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::在裡希預覽文字顏色修改

當「富預覽」文本顏色已更改時調用。

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::儲存文件上

框架作為檔案保存或檔保存為命令的一部分調用。

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
指向應將檔保存到的完全限定路徑。

### <a name="return-value"></a>傳回值

如果文檔已成功保存,則非零;否則 0。

### <a name="remarks"></a>備註

此函數的預設實現將打開指定的文件,調用[CObject::序列化](../../mfc/reference/cobject-class.md#serialize)以將文件的數據寫入檔,然後將文檔標記為乾淨。 如果要在框架保存文檔時執行特殊處理,則重寫此函數。 例如,可以編寫一個應用程式,其中文檔表示資料庫中的記錄,而不是單獨的檔。

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::開啟卸載處理程式

卸載預覽處理程式時由框架調用。

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>備註

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::更新檔案傳送郵件

如果存在郵件支援 (MAPI),則啟用ID_FILE_SEND_MAIL命令。

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向與ID_FILE_SEND_MAIL命令關聯的[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

### <a name="remarks"></a>備註

否則,該函數將從菜單中刪除ID_FILE_SEND_MAIL命令,包括功能表項上方或下方的分隔符( 如果 MAPI32,則啟用 MAPI。DLL 存在於路徑中,並且存在於 WIN 的 [郵件] 部分中。INI 檔案,MAPI=1。 大多數應用程式都在此命令放在"檔"功能表上。

`CDocument`支援通過郵件支援 (MAPI) 傳送文件。 請參閱 MFC 中的[MAPI 主題](../../mfc/mapi.md)和[MAPI 支援](../../mfc/mapi-support-in-mfc.md)文章。

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::P重新關閉框架

在銷毀框架視窗之前,框架將調用此成員函數。

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
指向保存關聯`CDocument`物件的[CFrameWnd 的](../../mfc/reference/cframewnd-class.md)指標。

### <a name="remarks"></a>備註

可以重寫它來提供自定義清理,但請務必調用基類。

中的預設值`PreCloseFrame`在`CDocument`中 不執行任何操作。 派生類[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此`CDocument`成員函數。

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::閱讀下一個塊值

讀取下一個塊值。

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>參數

*ppValue*<br/>
[出]當函數返回時 *,ppValue*包含讀取的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::發佈檔案

框架呼叫此成員函數以發布檔,使其可供其他應用程式使用。

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>參數

*pFile*<br/>
指向要釋放的 CFile 物件的指標。

*bAbort*<br/>
指定是否使用`CFile::Close`或釋放檔`CFile::Abort`。 如果要使用 CFile 釋放檔案,則[FALSE:關閉](../../mfc/reference/cfile-class.md#close);如果要使用[CFile:::中止](../../mfc/reference/cfile-class.md#abort)發佈檔,則為 TRUE。

### <a name="remarks"></a>備註

如果*bAbort*為`ReleaseFile``CFile::Abort`TRUE,則調用 ,然後釋放該檔。 `CFile::Abort`不會引發異常。

如果*bAbort*是`ReleaseFile``CFile::Close`FALSE,則調用和檔將被釋放。

重寫此成員函數,要求在釋放檔之前由使用者執行操作。

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::刪除區塊

使用指定的 GUID 刪除區塊。

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>參數

*Guid*<br/>
指定要刪除的塊的 GUID。

*Pid*<br/>
指定要刪除的塊的 PID。

### <a name="remarks"></a>備註

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::刪除檢視

調用此函數以從文檔分離檢視。

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
指向要刪除的檢視。

### <a name="remarks"></a>備註

此函數從與文檔關聯的檢視清單中刪除指定的檢視;它還將檢視的文件指標設定為 NULL。 當框架視窗關閉或拆分器視窗的窗格關閉時,框架將調用此功能。

僅當手動分離視圖時,才調用此功能。 通常,通過定義[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來關聯文檔類、視圖類和框架視窗類,可以讓框架分離文檔和視圖。

有關示例實現,請參閱[AddView](#addview)上的範例。

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument:報告儲存載入異常

如果在保存或載入文件時引發異常(通常是[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveexception),](../../mfc/reference/carchiveexception-class.md)則調用。

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
指向要保存或載入的文件的名稱。

*e*<br/>
指向引發的異常。 可能是 NULL。

*b 儲存*<br/>
指示正在進行的操作的標誌;如果保存文檔,則非零;如果正在載入文檔,則為 0。

*nIDPDefault*<br/>
如果函數未指定更具體的錯誤消息,則要顯示的錯誤消息的標識符。

### <a name="remarks"></a>備註

預設實現檢查異常物件並查找專門描述原因的錯誤消息。 如果未找到特定消息或*e*為 NULL,則使用*nIDPDefault*參數指定的常規訊息。 然後,該函數將顯示一個包含錯誤消息的消息框。 如果要提供其他自定義失敗消息,請覆蓋此函數。 這是一個高級的可重寫。

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::儲存修改

在要關閉修改的文檔之前,框架調用。

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>傳回值

如果可以安全地繼續並關閉文檔,則非零;如果不應關閉文檔,則為 0。

### <a name="remarks"></a>備註

此函數的預設實現將顯示一個消息框,詢問使用者是否保存對文檔的更改(如果有)。 如果程式需要不同的提示過程,請覆蓋此函數。 這是一個高級的可重寫。

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::設定區塊值

設置塊值。

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指定要設置的塊值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::設定修改後的 Flag

對文檔進行任何修改後,請調用此功能。

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*b 修改*<br/>
指示文檔是否已修改的標誌。

### <a name="remarks"></a>備註

通過一致地調用此函數,可確保框架在關閉文檔之前提示使用者保存更改。 通常,您應該對*b修改*參數使用預設值 TRUE。 要將文件標記為乾淨(未修改),請使用此函數的值為 FALSE。

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::設定路徑名稱

呼叫此函數以指定文檔磁碟檔的完全限定路徑。

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
指向要用作文件路徑的字串。

*bAddtoMRU*<br/>
確定檔案名是否加入最近使用的 (MRU) 檔案清單中。 如果為 TRUE,則添加檔名;如果為 TRUE,則添加檔名。如果 FALSE,則不添加它。

### <a name="remarks"></a>備註

根據*bAddToMRU*的值,路徑將添加到應用程式維護的 MRU 清單中,或者未添加路徑。 請注意,某些文檔未與磁碟文件關聯。 僅當重寫用於打開和保存框架使用的檔案的預設實現時,才調用此函數。

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::設定標題

呼叫此函數以指定文件的標題(框架視窗的標題列中顯示的字串)。

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
指向要用作文件標題的字串。

### <a name="remarks"></a>備註

呼叫此函數會更新顯示文件的所有框架視窗的標題。

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::更新所有檢視

修改文件後調用此函數。

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改文件的檢視,如果要更新所有檢視,則指向 NULL。

*lHint*<br/>
包含有關修改的資訊。

*pHint*<br/>
指向存儲有關修改資訊的物件。

### <a name="remarks"></a>備註

呼叫[Set 修改 Flag](#setmodifiedflag)成員函數後,應呼叫此函數。 此函數通知附加到文檔的每個檢視 *(pSender*指定的檢視除外)文檔已被修改。 通常在用戶通過檢視更改文檔後,從視圖類調用此函數。

此函數調用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函數,用於文檔的每個檢視,但發送檢視、傳遞*pHint*和*lHint*除外。 使用這些參數將信息傳遞給有關文檔修改的檢視。 您可以使用*lHint*和/或者定義[CObject](../../mfc/reference/cobject-class.md)派生類來存儲有關修改的資訊,並使用*pHint*傳遞該類的物件。 覆蓋`CView::OnUpdate`[CView](../../mfc/reference/cview-class.md)派生類中的成員函數,以便根據傳遞的資訊優化檢視顯示的更新。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
