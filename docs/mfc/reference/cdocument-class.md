---
title: "CDocument 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6cfe4dc779fb4ad50f2171ef8811785f48275a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cdocument-class"></a>CDocument 類別
提供使用者定義的文件類別的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocument : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocument::CDocument](#cdocument)|建構 `CDocument` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocument::AddView](#addview)|將檢視附加至文件。|  
|[CDocument::BeginReadChunks](#beginreadchunks)|初始化區塊讀取。|  
|[CDocument::CanCloseFrame](#cancloseframe)|進階可覆寫。關閉 檢視此文件框架視窗前呼叫。|  
|[CDocument::ClearChunkList](#clearchunklist)|清除區塊清單。|  
|[CDocument::ClearPathName](#clearpathname)|清除文件物件的路徑。|  
|[CDocument::DeleteContents](#deletecontents)|呼叫以執行文件的清除作業。|  
|[CDocument::FindChunk](#findchunk)|會尋找具有指定之 GUID。|  
|[CDocument::GetAdapter](#getadapter)|讓指標回到物件實作`IDocument`介面。|  
|[CDocument::GetDocTemplate](#getdoctemplate)|傳回描述文件類型的文件範本的指標。|  
|[CDocument::GetFile](#getfile)|讓指標回到所需`CFile`物件。|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|傳回的第一個位置清單中的檢視。用來開始反覆項目。|  
|[CDocument::GetNextView](#getnextview)|逐一查看文件相關聯的檢視清單。|  
|[CDocument::GetPathName](#getpathname)|傳回文件的資料檔案的路徑。|  
|[CDocument::GetThumbnail](#getthumbnail)|呼叫以建立縮圖的提供者用來顯示縮圖中的點陣圖。|  
|[CDocument::GetTitle](#gettitle)|傳回文件的標題。|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|呼叫以初始化搜尋內容搜尋處理常式。|  
|[CDocument::IsModified](#ismodified)|表示自上次儲存後是否已修改文件。|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|指示是否的這個執行個體`CDocument`搜尋和組織的處理常式建立物件。|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|呼叫以從資料流載入文件資料。|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|豐富的預覽字型變更之前呼叫。|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|檢視加入或移除文件中後呼叫。|  
|[CDocument::OnCloseDocument](#onclosedocument)|呼叫以關閉文件。|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|若要建立預覽框架 for Rich Preview 需要時由架構呼叫。|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|呼叫以回應文件事件的 framework。|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|在衍生類別來繪製內容的縮圖中，這個方法會覆寫。|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|需要從資料流載入文件資料時由架構呼叫。|  
|[CDocument::OnNewDocument](#onnewdocument)|呼叫以建立新的文件。|  
|[CDocument::OnOpenDocument](#onopendocument)|呼叫以開啟現有文件。|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示要從呼叫 GetFocus 函式傳回 HWND 預覽處理常式。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|預覽處理常式來處理從預覽處理常式正在執行的程序的訊息幫浦往上傳遞一個按鍵動作時，會指示。|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|豐富的預覽背景色彩變更時呼叫。|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|豐富的預覽字型已變更時呼叫。|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Rich Preview 站台已變更時呼叫。|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|豐富的預覽文字色彩變更時呼叫。|  
|[CDocument::OnSaveDocument](#onsavedocument)|呼叫以將文件儲存至磁碟。|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|預覽處理常式正在卸載模組時由架構呼叫。|  
|[CDocument::PreCloseFrame](#precloseframe)|框架視窗關閉之前呼叫。|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|讀取下一個區塊的值。|  
|[CDocument::ReleaseFile](#releasefile)|釋出要使其可供使用的其他應用程式的檔案。|  
|[CDocument::RemoveChunk](#removechunk)|移除具有指定之 GUID。|  
|[CDocument::RemoveView](#removeview)|中斷連結文件的檢視。|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|進階可覆寫。呼叫時開啟或儲存作業無法完成，因為發生例外狀況。|  
|[CDocument::SaveModified](#savemodified)|進階可覆寫。呼叫以要求使用者是否應該儲存文件。|  
|[CDocument::SetChunkValue](#setchunkvalue)|設定區塊值。|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|設定旗標，表示自上次儲存後已修改文件。|  
|[CDocument::SetPathName](#setpathname)|設定文件所使用的資料檔案的路徑。|  
|[CDocument::SetTitle](#settitle)|設定文件的標題。|  
|[CDocument::UpdateAllViews](#updateallviews)|通知所有文件的檢視已經過修改。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|傳送郵件訊息與附加的文件。|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|如果存在郵件支援，可讓傳送郵件命令。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定`CDocument`縮圖的 dllhost 式建立物件。 應該簽入`CView::OnDraw`。|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定`CDocument`物件所建立的 prevhost `Rich Preview`。 應該簽入`CView::OnDraw`。|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定`CDocument`物件由索引子或建立其他的搜尋應用程式。|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定豐富預覽視窗的背景的色彩。 此色彩是由主機設定。|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定豐富預覽視窗的前景的色彩。 此色彩是由主機設定。|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主機設定。|  
  
## <a name="remarks"></a>備註  
 文件表示使用者通常會隨即開啟，並開啟檔案 命令，並會以儲存檔案的命令，將資料的單元。  
  
 **CDocument**支援標準的作業，例如建立文件、 載入它，以及儲存它。 架構會管理使用介面所定義的文件**CDocument**。  
  
 應用程式可以支援多個類型的文件。例如，應用程式可能支援試算表和文字文件。 文件的每種類型有關聯的文件範本。文件範本會指定哪些資源 （例如，功能表、 圖示或快速鍵對應資料表） 會使用該類型的文件。 每份文件包含與其相關聯的指標`CDocTemplate`物件。  
  
 透過文件與使用者互動[CView](../../mfc/reference/cview-class.md)與其相關聯的物件。 檢視轉譯的文件框架視窗中的映像，並解譯使用者輸入為文件上的作業。 文件可以有多個與其相關聯的檢視。 當使用者開啟文件視窗時，架構會建立檢視，並將其附加至文件。 文件範本會指定何種檢視和框架視窗用來顯示每一種文件。  
  
 文件屬於 framework 的標準命令路由，因此接收命令，從標準使用者介面元件 （例如儲存檔案 功能表項目）。 文件接收轉送的現用檢視表的命令。 如果文件不會處理指定的命令，會轉送命令來管理它的文件範本。  
  
 文件的資料修改時，每個自己的檢視必須反映這些修改。 **CDocument**提供[UpdateAllViews](#updateallviews)要通知的這類變更，檢視，讓這些檢視可以重新繪製視成員函式。 架構也會提示使用者關閉之前儲存已修改的檔案。  
  
 若要實作典型的應用程式中的文件，您必須執行下列作業：  
  
-   自**CDocument**每種類型的文件。  
  
-   加入成員變數來儲存每個文件的資料。  
  
-   實作成員函式來讀取和修改文件的資料。 文件的檢視是這些成員函式的最重要的使用者。  
  
-   覆寫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)寫入和讀取文件的資料磁碟的文件類別中的成員函式。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
 如需有關**CDocument**，請參閱[序列化](../../mfc/serialization-in-mfc.md)，[文件/檢視架構的主題](../../mfc/document-view-architecture.md)，和[文件/檢視建立](../../mfc/document-view-creation.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="addview"></a>CDocument::AddView  
 呼叫此函式可附加至文件的檢視。  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pView`  
 要加入的檢視點。  
  
### <a name="remarks"></a>備註  
 此函式會將指定的檢視加入至文件; 相關聯的檢視清單函式也會設定此文件檢視的文件指標。 將新建立的檢視物件附加至文件; 時，架構會呼叫此函式這個問題發生在回應新檔案、 開啟檔案或新視窗的命令，或當分割分隔視窗。  
  
 只有當您以手動方式建立並附加檢視，請呼叫此函式。 通常您會讓連接文件和檢視所定義的 framework [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別，檢視類別和框架視窗類別建立關聯的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 初始化區塊讀取。  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 顯示文件框架視窗關閉之前由架構呼叫。  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 `pFrame`  
 指向框架視窗的 附加至文件的檢視。  
  
### <a name="return-value"></a>傳回值  
 安全地關閉框架視窗; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作會檢查是否有其他框架視窗，顯示文件。 如果指定的框架視窗會顯示文件的最後一個，則函數會提示使用者儲存文件，如果已修改。 如果您想要執行特殊處理，框架視窗關閉時，覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 建構**CDocument**物件。  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>備註  
 架構會處理為您建立文件。 覆寫[OnNewDocument](#onnewdocument)成員函式來執行初始設定以個別文件為基礎; 在這個步驟特別重要，在單一文件介面 (SDI) 應用程式中。  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 清除區塊清單。  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="clearpathname"></a>CDocument::ClearPathName  
 清除文件物件的路徑。  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>備註  
 清除 從路徑`CDocument`物件會造成提示使用者下一步在儲存文件時應用程式。 這可讓**儲存**命令的行為與相同**存**命令。  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 由架構呼叫以刪除文件的資料，而不會終結**CDocument**物件本身。  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>備註  
 它稱為之前在文件也將被銷毀。 它也稱為以確保文件是空的就會重複使用之前。 這是非常重要的 SDI 應用程式，使用只有一個文件。每當使用者建立或開啟另一個文件中重複使用文件。 呼叫此函式以實作 [編輯全部清除] 或類似的命令會刪除所有文件的資料。 此函式的預設實作不做任何動作。 覆寫這個函式來刪除您的文件中的資料。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 會尋找具有指定的 GUID。  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>參數  
 `guid`  
 指定要尋找區塊的 GUID。  
  
 `pid`  
 指定的區塊 (chunk) 若要尋找的 PID。  
  
### <a name="return-value"></a>傳回值  
 如果成功內部的區塊清單中的位置。 否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getadapter"></a>CDocument::GetAdapter  
 讓指標回到實作`IDocument`介面。  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>傳回值  
 指標，實作`IDocument`介面。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 呼叫此函式可取得此文件類型的文件範本的指標。  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此文件類型的文件範本的指標或**NULL**如果文件不受管理的文件範本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>CDocument::GetFile  
 呼叫此成員函式取得的指標`CFile`物件。  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可能為相對或絕對。  
  
 `pError`  
 現有檔案例外狀況物件，表示作業的完成狀態指標。  
  
 `nOpenFlags`  
 共用及存取模式。 指定開啟檔案時要採取的動作。 您可以結合 CFile 建構函式中列出的選項[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)使用位元 OR (&#124;) 運算子。 一個存取權限，以及一個共用選項是必要的。**modeCreate**和**modeNoInherit**是選擇性的模式。  
  
### <a name="return-value"></a>傳回值  
 指標`CFile`物件。  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 呼叫此函式可取得的文件相關聯的檢視清單中的第一個檢視的位置。  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目： [GetNextView](#getnextview)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 呼叫此函式可逐一查看所有文件的檢視。  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 `rPosition`  
 若要參考**位置**先前呼叫所傳回的值`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成員函式。 此值不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 檢視所識別的指標`rPosition`。  
  
### <a name="remarks"></a>備註  
 此函數會傳回所識別的檢視`rPosition`，然後設定`rPosition`至**位置**下一個檢視清單中的值。 如果擷取的檢視是在清單中，最後則`rPosition`設**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 呼叫此函式可取得的文件的磁碟檔案的完整的路徑。  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文件的完整的路徑。 如果文件尚未儲存，或沒有與它相關聯的磁碟檔案，這個字串是空的。  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 建立縮圖的提供者用來顯示縮圖中的點陣圖。  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>參數  
 `cx`  
 指定點陣圖的高度與寬度。  
  
 `phbmp`  
 此函式成功傳回時包含點陣圖的控制代碼。  
  
 `pdwAlpha`  
 包含指定的 alpha 色板值，此函式成功傳回時為 DWORD。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`成功，否則，如果已建立點陣圖的縮圖`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 呼叫此函式可取得文件的標題，通常衍生自文件的檔案名稱。  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文件的標題。  
  
##  <a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 呼叫以初始化搜尋內容搜尋處理常式。  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別初始化搜尋內容中。 內容應該要以分隔的部分的字串 「; 」。 例如，「 點。矩形。ole 項目 」。  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 呼叫此函式可判斷自上次儲存後是否已經修改文件。  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果自上次儲存; 後修改文件否則便是 0。  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 指示是否的這個執行個體`CDocument`建立搜尋和組織的處理常式。  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果這個執行個體`CDocument`建立搜尋和組織的處理常式。  
  
### <a name="remarks"></a>備註  
 此函數會傳回目前`TRUE`僅適用於實作中的處理序伺服器的豐富預覽處理常式。 您可以將此函式傳回您應用程式層級設定適當的旗標 （m_bPreviewHandlerMode、 m_bSearchMode、 m_bGetThumbnailMode） `TRUE`。  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 呼叫以從資料流載入文件資料。  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 資料流的指標。 這個資料流是由 Shell 來提供。  
  
 `dwGrfMode`  
 資料流的存取模式。  
  
### <a name="return-value"></a>傳回值  
 如果在載入作業成功，否則為錯誤碼的 HRESULT 為 S_OK。  
  
### <a name="remarks"></a>備註  
 您可以覆寫這個方法來自訂如何從資料流載入資料的衍生類別中。  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 指定`CDocument`縮圖的 dllhost 式建立物件。 應該簽入`CView::OnDraw`。  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示文件由 dllhost 縮圖。  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 指定`CDocument`for Rich Preview prevhost 式建立物件。 應該簽入`CView::OnDraw`。  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示文件已所建立的 prevhost for Rich Preview。  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 指定`CDocument`索引子或另一個搜尋應用程式建立物件。  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示索引子或另一個搜尋應用程式建立文件。  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 指定豐富預覽視窗的背景的色彩。 此色彩是由主機設定。  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 指定前景色彩的豐富預覽視窗。 此色彩是由主機設定。  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主機設定。  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 豐富的預覽字型變更之前呼叫。  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 檢視會加入或移除文件後，由架構呼叫。  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作檢查是否的最後一個檢視已被移除，是否是的話，會刪除文件。 如果您想要執行特殊處理的架構新增或移除檢視時，覆寫這個函式。 例如，如果您想要保持開啟，即使沒有連接到它的檢視表的文件時，覆寫這個函式。  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 文件關閉時，通常作為 File Close 命令的一部分，由架構呼叫。  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會終結所有框架用於檢視文件，關閉檢視、 清除文件的內容，然後呼叫[DeleteContents](#deletecontents)成員函式來刪除的文件資料。  
  
 如果您想要執行特殊清除處理序架構關閉文件時，覆寫這個函式。 例如，如果文件代表資料庫中的記錄，您可以覆寫這個函式來關閉資料庫。 您應該從您的覆寫來呼叫此函式的基底類別版本。  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 若要建立預覽框架 for Rich Preview 需要時由架構呼叫。  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果成功，否則為建立框架`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 呼叫以回應文件事件的 framework。  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>參數  
 [in] `deEvent`  
 描述事件的型別列舉的資料型別。  
  
### <a name="remarks"></a>備註  
 文件事件可能會影響多個類別。 這個方法會負責處理會影響類別以外的文件事件[CDocument 類別](../../mfc/reference/cdocument-class.md)。 目前，唯一必須回應文件事件的類別是[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument`類別具有其他可覆寫方法負責處理效果`CDocument`。  
  
 下表列出可能的值為`deEvent`和它們對應到事件。  
  
|值|對應事件|  
|-----------|-------------------------|  
|`onAfterNewDocument`|建立新的文件。|  
|`onAfterOpenDocument`|已開啟新文件。|  
|`onAfterSaveDocument`|已儲存的文件。|  
|`onAfterCloseDocument`|已關閉文件。|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 在衍生類別來繪製縮圖中的，這個方法會覆寫。  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 裝置內容的參考。  
  
 `lprcBounds`  
 指定縮圖應該要繪製的區域的周的框。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 傳送訊息透過內建的郵件主機 （如果有的話） 與文件做為附件。  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>備註  
 `OnFileSendMail`呼叫[OnSaveDocument](#onsavedocument) （儲存） 未命名和已修改的暫存檔案，然後透過電子郵件傳送文件序列化。 如果未修改文件，則不會需要的暫存檔案;原始會傳送。 `OnFileSendMail`載入 MAPI32。如果它已經尚未載入的 DLL。  
  
 特殊實作`OnFileSendMail`如[COleDocument](../../mfc/reference/coledocument-class.md)控點正確複合檔案。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI 主題](../../mfc/mapi.md)和[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 需要從資料流載入文件資料時由架構呼叫。  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 內送的資料流的指標。  
  
 `grfMode`  
 資料流的存取模式。  
  
### <a name="return-value"></a>傳回值  
 如果負載是成功;，S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 由架構呼叫做為新檔案 命令的一部分。  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功初始化文件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的且隨後會將標示為初始狀態的新文件。 覆寫這個函式來初始化新的文件的資料結構。 您應該從您的覆寫來呼叫此函式的基底類別版本。  
  
 如果使用者選擇新檔案 命令在 SDI 應用程式中，架構會使用此函式來重新初始化現有的文件，而不是建立一個新。 如果使用者選擇新檔案中的多個文件介面 (MDI) 應用程式，架構會每次建立新文件，並接著呼叫此函式可將它初始化。 初始化程式碼必須放置在新檔案 命令在 SDI 應用程式中有效的建構函式而不是這個函式。  
  
 請注意，有狀況下`OnNewDocument`呼叫兩次。 會發生這種情況是當文件會內嵌為 ActiveX 文件伺服程式。 首先會呼叫函式`CreateInstance`方法 (所公開`COleObjectFactory`-衍生的類別) 和第二個階段`InitNew`方法 (由`COleServerDoc`-衍生的類別)。  
  
### <a name="example"></a>範例  
 下列範例說明初始化文件物件的替代方法。  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument::OnOpenDocument  
 由架構呼叫以開啟舊檔 命令的一部分。  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 要開啟的文件的路徑點。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功載入文件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會開啟指定的檔案，呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的會呼叫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)讀取檔案隨後會將標示為全新的文件和內容。 如果您想要使用的項目以外的封存機制或檔案機制，請覆寫這個函式。 例如，您可以撰寫應用程式的文件位置代表資料庫，而不是個別檔案中的記錄。  
  
 如果使用者選擇開啟檔案 命令在 SDI 應用程式中，架構會使用此函式重新初始化現有**CDocument**物件，而不是建立一個新。 如果使用者選擇開啟檔案的 MDI 應用程式中，建構新架構**CDocument**每次物件，接著再呼叫此函式可將它初始化。 初始化程式碼必須放置在這個函式而不是有效 SDI 應用程式中開啟檔案 命令的建構函式。  
  
### <a name="example"></a>範例  
 下列範例說明初始化文件物件的替代方法。  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 指示預覽處理常式傳回 HWND 擷取自呼叫`GetFocus`函式。  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>參數  
 `phwnd`  
 [out]此方法傳回時，包含從呼叫傳回 HWND 指標`GetFocus`函式，從預覽處理常式的前景執行緒。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果登錄成功。或其他原因的錯誤值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 預覽處理常式來處理從預覽處理常式正在執行的程序的訊息幫浦往上傳遞一個按鍵動作時，會指示。  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>參數  
 `pmsg`  
 [in]視窗訊息指標。  
  
### <a name="return-value"></a>傳回值  
 如果預覽處理常式可以處理按鍵訊息，此處理常式處理它，並傳回 S_OK。 如果預覽處理常式無法處理按鍵訊息，它提供其主機可透過`IPreviewHandlerFrame::TranslateAccelerator`。 如果主應用程式處理訊息時，這個方法會傳回 S_OK。 如果主機不會處理訊息，這個方法會傳回 S_FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 豐富的預覽背景色彩變更時呼叫。  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 豐富的預覽字型已變更時呼叫。  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 Rich Preview 站台已變更時呼叫。  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 豐富的預覽文字色彩變更時呼叫。  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsavedocument"></a>CDocument::OnSaveDocument  
 由架構呼叫以儲存檔案 或 另存新檔 命令的一部分。  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 指向檔案應該儲存的完整路徑。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功儲存文件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會開啟指定的檔案，呼叫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)寫入文件的資料檔案，然後再標記文件做為初始狀態。 如果您想要執行特殊處理的架構儲存文件時，覆寫這個函式。 例如，您可以撰寫應用程式的文件位置代表資料庫，而不是個別檔案中的記錄。  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 卸載預覽處理常式時，由架構呼叫。  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail  
 可讓**ID_FILE_SEND_MAIL**命令 mail 支援 (MAPI) 是否存在。  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件相關聯**ID_FILE_SEND_MAIL**命令。  
  
### <a name="remarks"></a>備註  
 否則函式會移除**ID_FILE_SEND_MAIL**命令從功能表中，包括分隔符號上述或功能表項目依適當情況下。 如果啟用 MAPI MAPI32。DLL 存在於路徑中，以及 WIN [Mail] 區段中。INI 檔案，MAPI = 1。 大部分的應用程式檔案 功能表上，將此命令。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI 主題](../../mfc/mapi.md)和[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 終結框架視窗之前，此成員函式是由架構呼叫。  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 `pFrame`  
 指標[CFrameWnd](../../mfc/reference/cframewnd-class.md)包含相關聯之**CDocument**物件。  
  
### <a name="remarks"></a>備註  
 它會覆寫以提供自訂的清除作業，但請確定呼叫基底類別。  
  
 預設值是`PreCloseFrame`不做任何動作**CDocument**。 **CDocument**-衍生的類別[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用這個成員函式。  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 讀取的下一個區塊的值。  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>參數  
 `ppValue`  
 [out]此函式傳回時，`ppValue`包含已讀取的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 若要發行檔案，因此可以使用其他應用程式架構會呼叫此成員函式。  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>參數  
 `pFile`  
 釋出 CFile 物件的指標。  
  
 `bAbort`  
 指定檔案是否使用釋出`CFile::Close`或`CFile::Abort`。 **FALSE**如果檔案是使用釋出[CFile::Close](../../mfc/reference/cfile-class.md#close);**TRUE**如果檔案是使用釋出[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="remarks"></a>備註  
 如果`bAbort`是**TRUE**，`ReleaseFile`呼叫`CFile::Abort`，檔案會釋出。 `CFile::Abort`不會擲回例外狀況。  
  
 如果`bAbort`是**FALSE**，`ReleaseFile`呼叫`CFile::Close`和釋放檔案。  
  
 覆寫此成員函式，以釋放檔案之前，需要使用者動作。  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 移除具有指定之 GUID 的區塊。  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>參數  
 `Guid`  
 指定要移除區塊 (chunk) 的 GUID。  
  
 `Pid`  
 指定要移除區塊 (chunk) 的 PID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 呼叫此函式可卸離文件的檢視。  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pView`  
 指向要移除的檢視。  
  
### <a name="remarks"></a>備註  
 此函式的文件; 相關聯的檢視清單中移除指定的檢視這也設定檢視的文件指標**NULL**。 框架視窗已關閉或已關閉的分隔視窗窗格時，此函式是由架構呼叫。  
  
 只有當您手動卸離的檢視，請呼叫此函式。 通常您會讓卸離文件和檢視定義的 framework [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別，檢視類別和框架視窗類別建立關聯的物件。  
  
 請參閱在範例[AddView](#addview)實作範例。  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 如果擲回例外狀況呼叫 (通常[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveException](../../mfc/reference/carchiveexception-class.md)) 時儲存或載入文件。  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 在的文件的名稱會指向儲存或載入。  
  
 *e*  
 指向已擲回的例外狀況。 可能是**NULL**。  
  
 *bSaving*  
 旗標，指出哪一個作業正在進行。非零，如果文件儲存，0 如果載入文件。  
  
 `nIDPDefault`  
 如果函式未指定更特定的顯示錯誤訊息的識別碼。  
  
### <a name="remarks"></a>備註  
 預設實作會檢查例外狀況物件，並尋找特別說明原因的錯誤訊息。 如果找不到特定的訊息，或如果*e*是**NULL**，由指定的一般訊息`nIDPDefault`使用參數。 此函數接著會顯示訊息方塊包含錯誤訊息。 如果您想要提供額外的自訂錯誤訊息，請覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="savemodified"></a>CDocument::SaveModified  
 修改過的文件關閉前，由架構呼叫。  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全地繼續並關閉文件，則為非零0，表示不應該關閉文件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會顯示訊息方塊，詢問使用者是否要將變更儲存至文件中，如果您未做任何。 如果您的程式需要不同的提示程序，請覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 設定區塊值。  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>參數  
 `pValue`  
 指定要設定的區塊值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 您所做的任何修改文件之後，請呼叫此函式。  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 指出是否已修改文件的旗標。  
  
### <a name="remarks"></a>備註  
 以一致的方式呼叫此函式，您可以確保架構會提示使用者關閉文件之前先儲存變更。 通常您應該使用的預設值**TRUE**如`bModified`參數。 若要標記乾淨的文件 （未修改），呼叫此函數中使用的值**FALSE**。  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 呼叫此函式可指定文件的磁碟檔案的完整的路徑。  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 指向要做為文件路徑的字串。  
  
 `bAddToMRU`  
 決定是否在檔案名稱加入至最近使用的 (MRU) 檔案清單。 如果**為 TRUE，**加入檔案名稱; 如果**FALSE**，會將其加入。  
  
### <a name="remarks"></a>備註  
 值而定`bAddToMRU`加入，或未加入至應用程式所維護的 MRU 清單的路徑。 請注意，某些文件相關聯的磁碟檔案。 只有當您正在覆寫開啟和儲存檔案架構所使用的預設實作，請呼叫此函式。  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 呼叫此函式可指定文件的標題 （框架視窗的標題列中顯示的字串）。  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>參數  
 `lpszTitle`  
 指向要做為文件的標題字串。  
  
### <a name="remarks"></a>備註  
 呼叫此函式會更新所有顯示的文件的框架視窗的標題。  
  
##  <a name="updateallviews"></a>CDocument::UpdateAllViews  
 在修改文件之後，請呼叫此函式。  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 指向修改文件中，檢視或**NULL**如果所有檢視更新。  
  
 `lHint`  
 包含有關修改資訊。  
  
 `pHint`  
 指向以儲存修改的相關資訊的物件。  
  
### <a name="remarks"></a>備註  
 您呼叫之後，您應該呼叫此函式[SetModifiedFlag](#setmodifiedflag)成員函式。 此函式會通知附加至文件中，除了所指定的檢視每個檢視`pSender`，已經修改文件。 您通常呼叫此函式從檢視類別使用者透過檢視文件變更後。  
  
 此函數會呼叫[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)除了傳送的文件的檢視表的每個成員函式檢視，請傳遞`pHint`和`lHint`。 使用這些參數將資訊傳遞至相關的文件進行的修改檢視。 您可以編碼資訊使用`lHint`和 （或) 您可以定義[CObject](../../mfc/reference/cobject-class.md)-衍生類別來儲存所做的修改的相關資訊，並將該類別使用的物件傳遞`pHint`。 覆寫`CView::OnUpdate`成員函式中的您[CView](../../mfc/reference/cview-class.md)-衍生的類別，以最佳化更新檢視的顯示根據傳遞的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 範例 NPP](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
