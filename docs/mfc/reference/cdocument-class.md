---
title: "CDocument 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocument
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], serialization
- files [C++], documents
- command handling, documents and
- documents [C++], document classes
- documents [C++], multiple views
- serialization [C++], documents and
- CDocument class
- command routing, documents and
- views [C++], document
- documents [C++], command routing
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4d64b95f77139d984b855e710f3951434e489dd5
ms.lasthandoff: 02/24/2017

---
# <a name="cdocument-class"></a>CDocument 類別
提供使用者定義的文件類別的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocument : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocument::CDocument](#cdocument)|建構 `CDocument` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocument::AddView](#addview)|將檢視附加至文件。|  
|[CDocument::BeginReadChunks](#beginreadchunks)|初始化區塊讀取。|  
|[CDocument::CanCloseFrame](#cancloseframe)|進階可覆寫。關閉框架視窗檢視這份文件之前呼叫。|  
|[CDocument::ClearChunkList](#clearchunklist)|清除區塊清單。|  
|[CDocument::ClearPathName](#clearpathname)|清除文件物件的路徑。|  
|[CDocument::DeleteContents](#deletecontents)|呼叫以執行清除作業的文件。|  
|[CDocument::FindChunk](#findchunk)|會尋找具有指定之 GUID。|  
|[CDocument::GetAdapter](#getadapter)|將指標傳回至物件實作`IDocument`介面。|  
|[CDocument::GetDocTemplate](#getdoctemplate)|傳回描述文件類型的文件範本的指標。|  
|[CDocument::GetFile](#getfile)|將指標傳回至想要的`CFile`物件。|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|傳回第一個清單中的檢視。用來開始反覆項目。|  
|[CDocument::GetNextView](#getnextview)|逐一查看的文件相關聯的檢視清單。|  
|[CDocument::GetPathName](#getpathname)|傳回文件的資料檔案的路徑。|  
|[CDocument::GetThumbnail](#getthumbnail)|呼叫來建立縮圖的提供者用來顯示縮圖中的點陣圖。|  
|[CDocument::GetTitle](#gettitle)|傳回文件的標題。|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|呼叫以初始化搜尋內容搜尋處理常式。|  
|[CDocument::IsModified](#ismodified)|表示自上次儲存後是否已修改文件。|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|指示是否的這個執行個體`CDocument`搜尋 i 組織處理常式建立物件。|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|呼叫以從資料流載入文件資料。|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|豐富的預覽字型變更之前呼叫。|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|檢視加入或移除文件之後呼叫。|  
|[CDocument::OnCloseDocument](#onclosedocument)|呼叫以關閉文件。|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|需要建立豐富的預覽預覽框架時，由架構呼叫。|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|以文件事件回應的架構所呼叫。|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|衍生的類別，用來繪製內容的縮圖中，這個方法會覆寫。|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|需要從資料流載入文件資料時，由架構呼叫。|  
|[CDocument::OnNewDocument](#onnewdocument)|呼叫以建立新的文件。|  
|[CDocument::OnOpenDocument](#onopendocument)|呼叫以開啟現有文件。|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示預覽處理常式從呼叫 GetFocus 函式傳回的 HWND。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|指示預覽處理常式來處理按鍵，從預覽處理常式正在執行的程序的訊息幫浦中向上傳遞。|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|豐富的預覽背景色彩變更時呼叫。|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|豐富的預覽字型變更時呼叫。|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|豐富的預覽網站已經變更時呼叫。|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|豐富的預覽文字色彩變更時呼叫。|  
|[CDocument::OnSaveDocument](#onsavedocument)|呼叫以將文件儲存至磁碟。|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|正在卸載預覽處理常式時，由架構呼叫。|  
|[CDocument::PreCloseFrame](#precloseframe)|框架視窗關閉之前呼叫。|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|讀取下一個區塊的值。|  
|[CDocument::ReleaseFile](#releasefile)|釋出要使其可供使用的其他應用程式的檔案。|  
|[CDocument::RemoveChunk](#removechunk)|移除具有指定之 GUID。|  
|[CDocument::RemoveView](#removeview)|中斷連結文件的檢視。|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|進階可覆寫。呼叫時已開啟或儲存作業無法完成，因為發生例外狀況。|  
|[CDocument::SaveModified](#savemodified)|進階可覆寫。呼叫以詢問使用者是否應該儲存文件。|  
|[CDocument::SetChunkValue](#setchunkvalue)|設定區塊值。|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|設定旗標，表示自上次儲存後，您已修改文件。|  
|[CDocument::SetPathName](#setpathname)|設定文件所使用的資料檔案的路徑。|  
|[CDocument::SetTitle](#settitle)|設定文件的標題。|  
|[CDocument::UpdateAllViews](#updateallviews)|通知所有文件的檢視已經過修改。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|附加的文件傳送郵件訊息。|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|是否有郵件支援，可讓傳送郵件命令。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定`CDocument`dllhost 的縮圖建立物件。 應該簽入`CView::OnDraw`。|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定`CDocument`物件所建立的 prevhost `Rich Preview`。 應該簽入`CView::OnDraw`。|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定`CDocument`索引子或其他的搜尋應用程式所建立物件。|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定豐富的預覽視窗的背景色彩。 這個色彩是由主應用程式設定。|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定前景色彩豐富的預覽視窗。 這個色彩是由主應用程式設定。|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主應用程式設定。|  
  
## <a name="remarks"></a>備註  
 文件表示使用者通常會開啟並開啟檔案 命令，並儲存檔案的命令會將資料的單元。  
  
 **CDocument**支援標準作業，例如建立文件、 載入它，以及儲存它。 架構會管理使用介面所定義的文件**CDocument**。  
  
 應用程式可以支援多個類型的文件。例如，應用程式可能支援試算表和文字文件。 每一種文件具有相關聯的文件範本。文件範本指定哪些資源 （例如，功能表、 圖示或加速器資料表） 會使用該類型的文件。 每份文件包含與其相關聯的指標`CDocTemplate`物件。  
  
 透過文件與使用者互動[CView](../../mfc/reference/cview-class.md)與其相關聯的物件。 檢視呈現文件框架視窗中的影像，而且會將使用者輸入解譯為文件上的作業。 文件可以有多個與其相關聯的檢視。 當使用者開啟文件視窗時，架構會建立檢視，並將其附加至文件。 文件範本指定的檢視和框架視窗類型用來顯示每一種文件。  
  
 文件屬於架構的標準命令路由，並因此接收標準使用者介面元件 （例如儲存檔案 功能表項目） 中的命令。 文件接收轉送的使用中檢視的命令。 如果文件不會處理指定的命令，它會轉送命令來管理它的文件範本。  
  
 文件的資料修改時，每個檢視必須反映這些修改。 **CDocument**提供[UpdateAllViews](#updateallviews) ，以通知這類變更的檢視，讓檢視可以重新繪製所需的成員函式。 架構也會提示使用者關閉之前儲存修改過的檔案。  
  
 若要實作典型的應用程式中的文件，您必須執行下列作業︰  
  
-   自**CDocument**每種類型的文件。  
  
-   加入成員變數來儲存每個文件資料。  
  
-   實作成員函式來讀取和修改文件的資料。 文件的檢視是這些成員函式的最重要的使用者。  
  
-   覆寫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)成員函式，在您的文件類別，以讀取和寫入文件的資料磁碟。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI](../../mfc/mapi.md)和[MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
 如需有關**CDocument**，請參閱[序列化](../../mfc/serialization-in-mfc.md)，[文件/檢視架構主題](../../mfc/document-view-architecture.md)，和[文件/檢視建立](../../mfc/document-view-creation.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-nameaddviewa--cdocumentaddview"></a><a name="addview"></a>CDocument::AddView  
 呼叫此函式可附加至文件的檢視。  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pView`  
 指向 [新增] 檢視。  
  
### <a name="remarks"></a>備註  
 此函式會將指定的檢視加入至文件; 相關聯的檢視清單函式也會設定此文件檢視的文件指標。 將新建立的檢視物件附加至文件時，架構會呼叫此函式這個問題發生在回應新檔案、 開啟檔案或新的視窗的命令或分隔視窗被分割。  
  
 只有當您以手動方式建立並附加檢視，請呼叫此函式。 通常您會讓連接文件和檢視表定義架構[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別、 檢視類別和框架視窗類別建立關聯的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocViewSDI #&12;](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="a-namebeginreadchunksa--cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 初始化區塊讀取。  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecancloseframea--cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame  
 顯示文件框架視窗關閉之前，由架構呼叫。  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 `pFrame`  
 框架視窗的檢視附加至文件的指標。  
  
### <a name="return-value"></a>傳回值  
 安全地關閉框架視窗; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會檢查是否有其他框架視窗，顯示文件。 如果指定的框架視窗會顯示文件的最後一個，函數就會提示使用者儲存文件，如果已修改。 如果您想要執行特殊處理的框架視窗關閉時，覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="a-namecdocumenta--cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument  
 建構**CDocument**物件。  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>備註  
 為您的文件建立可由架構處理。 覆寫[OnNewDocument](#onnewdocument)成員函式來初始化每個文件各執行; 這是在單一文件介面 (SDI) 應用程式中非常重要。  
  
##  <a name="a-nameclearchunklista--cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList  
 清除區塊清單。  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameclearpathnamea--cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName  
 清除文件物件的路徑。  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>備註  
 清除從路徑`CDocument`物件讓應用程式接著儲存文件時，提示使用者。 這可讓**儲存**命令行為就像**另存新檔**命令。  
  
##  <a name="a-namedeletecontentsa--cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents  
 若要刪除文件的資料，而不會終結架構呼叫**CDocument**物件本身。  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>備註  
 它是在文件，則會終結之前呼叫。 它也稱為以確保文件是空的才能重複使用它。 這是非常重要的 SDI 應用程式，使用只有一個文件。每當使用者建立或開啟另一個文件時，會重複使用文件。 呼叫此函式以實作 [編輯全部清除] 或類似的命令會刪除所有文件的資料。 此函式的預設實作不做任何動作。 覆寫這個函式來刪除您的文件中的資料。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&57;](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="a-namefindchunka--cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk  
 會尋找具有指定之 GUID。  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>參數  
 `guid`  
 指定要尋找區塊的 GUID。  
  
 `pid`  
 指定區塊來尋找的 PID。  
  
### <a name="return-value"></a>傳回值  
 如果成功內部的區塊清單中的位置。 否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetadaptera--cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter  
 將指標傳回至物件實作`IDocument`介面。  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>傳回值  
 指向物件實作`IDocument`介面。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetdoctemplatea--cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 呼叫此函式可取得此文件類型的文件範本的指標。  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此文件類型的文件範本的指標或**NULL**如果文件未受管理的文件範本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&58;](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="a-namegetfilea--cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile  
 若要取得的指標，此成員函式的呼叫`CFile`物件。  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可能是相對或絕對。  
  
 `pError`  
 現有的檔案例外狀況物件，表示作業的完成狀態指標。  
  
 `nOpenFlags`  
 共用和存取模式。 指定當開啟檔案時要採取的動作。 您可以結合 CFile 建構函式中列出的選項[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)所使用的位元 OR (|) 運算子。 一個存取權，以及一個共用選項是必要的。**modeCreate**和**modeNoInherit**是選擇性的模式。  
  
### <a name="return-value"></a>傳回值  
 指標`CFile`物件。  
  
##  <a name="a-namegetfirstviewpositiona--cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 呼叫此函式可取得的文件相關聯的檢視清單中的第一個檢視的位置。  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目與[GetNextView](#getnextview)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="a-namegetnextviewa--cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView  
 呼叫此函式來逐一查看所有的文件的檢視。  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 `rPosition`  
 參考**位置**先前呼叫所傳回的值`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成員函式。 此值不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 檢視所識別的指標`rPosition`。  
  
### <a name="remarks"></a>備註  
 此函數會傳回所識別的檢視`rPosition`，然後設定`rPosition`至**位置**下一步檢視清單中的值。 如果擷取的檢視是在清單中，最後則`rPosition`設為**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="a-namegetpathnamea--cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName  
 呼叫此函式可取得文件的磁碟檔案的完整的路徑。  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文件的完整的路徑。 如果文件尚未儲存，或沒有與其相關聯的磁碟檔案，這個字串是空的。  
  
##  <a name="a-namegetthumbnaila--cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail  
 建立縮圖的提供者用來顯示縮圖的點陣圖。  
  
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
 函式成功傳回時包含點陣圖的控制代碼。  
  
 `pdwAlpha`  
 包含函式成功傳回時，指定 alpha 色頻值 DWORD。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`是否成功，否則為建立縮圖的點陣圖`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettitlea--cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle  
 呼叫此函式可取得文件的標題，通常衍生自文件的檔名。  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文件的標題。  
  
##  <a name="a-nameinitializesearchcontenta--cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 呼叫以初始化搜尋內容搜尋處理常式。  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>備註  
 覆寫此方法以初始化搜尋內容的衍生類別中。 內容應該要分隔的組件包含字串 「; 」。 例如，「 點。矩形。ole 項目 」。  
  
##  <a name="a-nameismodifieda--cdocumentismodified"></a><a name="ismodified"></a>CDocument::IsModified  
 呼叫此函式可判斷自上次儲存後是否已修改文件。  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已修改文件自上次儲存。否則為 0。  
  
##  <a name="a-nameissearchandorganizehandlera--cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 指示是否的這個執行個體`CDocument`建立搜尋 i 組織處理常式。  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果這個執行個體`CDocument`建立搜尋 i 組織處理常式。  
  
### <a name="remarks"></a>備註  
 此函數會傳回目前`TRUE`僅適用於豐富的預覽處理常式中處理序伺服器的實作。 您可以設定適當的旗標 （m_bPreviewHandlerMode、 m_bSearchMode、 m_bGetThumbnailMode），以使此函式回到您應用程式層級`TRUE`。  
  
##  <a name="a-nameloaddocumentfromstreama--cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 呼叫以從資料流載入文件資料。  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 資料流的指標。 介面會提供這個資料流。  
  
 `dwGrfMode`  
 資料流的存取模式。  
  
### <a name="return-value"></a>傳回值  
 如果載入作業成功，否則為 HRESULT 錯誤碼，S_OK。  
  
### <a name="remarks"></a>備註  
 您可以覆寫這個方法來自訂如何將資料從資料流載入在衍生類別中。  
  
##  <a name="a-namembgetthumbnailmodea--cdocumentmbgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 指定`CDocument`dllhost 的縮圖建立物件。 應該簽入`CView::OnDraw`。  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示文件由 dllhost 的縮圖。  
  
##  <a name="a-namembpreviewhandlermodea--cdocumentmbpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 指定`CDocument`prevhost 已建立物件的豐富預覽。 應該簽入`CView::OnDraw`。  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示文件所建立的 prevhost 豐富的預覽。  
  
##  <a name="a-namembsearchmodea--cdocumentmbsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 指定`CDocument`索引子或另一個搜尋應用程式建立物件。  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`表示建立文件的索引子或另一個搜尋應用程式。  
  
##  <a name="a-namemclrrichpreviewbackcolora--cdocumentmclrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 指定豐富的預覽視窗的背景色彩。 這個色彩是由主應用程式設定。  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemclrrichpreviewtextcolora--cdocumentmclrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 指定豐富的預覽視窗的前景色彩。 這個色彩是由主應用程式設定。  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemlfrichpreviewfonta--cdocumentmlfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 指定豐富的預覽視窗的文字字型。 這個字型的資訊是由主應用程式設定。  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonbeforerichpreviewfontchangeda--cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 豐富的預覽字型變更之前呼叫。  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonchangedviewlista--cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 加入或移除文件檢視之後，由框架呼叫。  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作檢查是否的最後一個檢視已停用，是否是的話，會刪除文件。 如果您想要執行特殊處理的架構中加入或移除檢視時，覆寫這個函式。 例如，如果您想要保持開啟，即使沒有附加至該檢視的文件時，覆寫這個函式。  
  
##  <a name="a-nameonclosedocumenta--cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument  
 當文件關閉時，通常做為檔案關閉命令的一部分，由架構呼叫。  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會終結所有可用來檢視文件的框架，關閉檢視、 清除文件的內容，然後呼叫[DeleteContents](#deletecontents)成員函式來刪除文件的資料。  
  
 如果您想要執行特殊清除處理序架構關閉文件時，覆寫這個函式。 比方說，如果文件代表資料庫中的記錄，您可能想要覆寫這個函式來關閉資料庫。 您應該從您的覆寫呼叫此函式的基底類別版本。  
  
##  <a name="a-nameoncreatepreviewframea--cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 需要建立豐富的預覽預覽框架時，由架構呼叫。  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果成功，否則為建立框架`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondocumenteventa--cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 以文件事件回應的架構所呼叫。  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>參數  
 [in] `deEvent`  
 描述事件的型別列舉的資料型別。  
  
### <a name="remarks"></a>備註  
 文件事件可能會影響多個類別。 這個方法會負責處理只會影響類別的文件事件[CDocument 類別](../../mfc/reference/cdocument-class.md)。 目前，唯一必須回應文件事件的類別是[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument`類別有其他可覆寫方法負責處理效果`CDocument`。  
  
 下表列出可能的值為`deEvent`和它們對應到事件。  
  
|值|相對應的事件|  
|-----------|-------------------------|  
|`onAfterNewDocument`|建立新的文件。|  
|`onAfterOpenDocument`|開啟新文件。|  
|`onAfterSaveDocument`|已儲存文件。|  
|`onAfterCloseDocument`|已關閉文件。|  
  
##  <a name="a-nameondrawthumbnaila--cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 在衍生的類別，用來繪製縮圖中，這個方法會覆寫。  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 裝置內容的參考。  
  
 `lprcBounds`  
 指定縮圖應該要繪製的區域的周框的矩形。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfilesendmaila--cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 傳送訊息透過內建的郵件主機 （如果有的話） 與文件作為附件。  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>備註  
 `OnFileSendMail`呼叫[OnSaveDocument](#onsavedocument)序列化 （儲存） 到暫存檔案，然後透過電子郵件會傳送未命名和修改過的文件。 如果未修改文件，不被必要的暫存檔;原始會傳送。 `OnFileSendMail`載入 MAPI32。如果它已經尚未載入的 DLL。  
  
 特殊實作`OnFileSendMail`的[COleDocument](../../mfc/reference/coledocument-class.md)控點正確複合檔案。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI 主題](../../mfc/mapi.md)和[MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="a-nameonloaddocumentfromstreama--cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 需要從資料流載入文件資料時，由架構呼叫。  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 內送資料流的指標。  
  
 `grfMode`  
 資料流的存取模式。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果負載是成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonnewdocumenta--cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument  
 做為新檔案 命令的一部分的架構所呼叫。  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>傳回值  
 已成功初始化文件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的且隨後會將標示為初始狀態的新文件。 覆寫這個函式來初始化新的文件的資料結構。 您應該從您的覆寫呼叫此函式的基底類別版本。  
  
 如果使用者選擇在 SDI 應用程式中的新檔案 命令，架構會使用此函式來重新初始化現有的文件，而不是建立一個新。 如果使用者選擇新檔案的多個文件介面 (MDI) 應用程式中，每次建立新的文件架構，並接著呼叫此函式可將它初始化。 您必須將初始化程式碼，而不是此函式中的新檔案 命令會在 SDI 應用程式中有效的建構函式。  
  
 請注意，有案例 where`OnNewDocument`呼叫兩次。 會發生這種情況是當文件會內嵌為 ActiveX 文件伺服程式。 第一次呼叫函式`CreateInstance`方法 (由`COleObjectFactory`-衍生的類別) 和第二次的`InitNew`方法 (所公開`COleServerDoc`-衍生的類別)。  
  
### <a name="example"></a>範例  
 下列範例說明初始化文件物件的替代方法。  
  
 [!code-cpp[NVC_MFCDocView #&60;](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="a-nameonopendocumenta--cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::OnOpenDocument  
 開啟檔案 命令的一部分的架構所呼叫。  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 若要開啟的文件的路徑點。  
  
### <a name="return-value"></a>傳回值  
 已成功載入文件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會開啟指定的檔案，呼叫[DeleteContents](#deletecontents)成員函式，以確保文件是空的會呼叫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)讀取檔案的內容，以及隨後會將標示為全新的文件。 如果您想要使用的項目保存機制或檔案機制以外，覆寫這個函式。 例如，您可以撰寫應用程式的文件，代表資料庫，而不是個別檔案中的記錄。  
  
 如果使用者選擇開啟檔案 命令在 SDI 應用程式中，架構會使用此函式重新初始化現有**CDocument**物件，而不是建立一個新。 如果使用者選擇開啟檔案的 MDI 應用程式中，建構新的架構**CDocument**每次物件，然後再呼叫此函式可將它初始化。 您必須將初始化程式碼，而不是此函式中開啟檔案 命令會在 SDI 應用程式中有效的建構函式。  
  
### <a name="example"></a>範例  
 下列範例說明初始化文件物件的替代方法。  
  
 [!code-cpp[NVC_MFCDocView #&60;](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&63;](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="a-nameonpreviewhandlerqueryfocusa--cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 指示預覽處理常式傳回 HWND 擷取自呼叫`GetFocus`函式。  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>參數  
 `phwnd`  
 [out]當這個方法會傳回包含從呼叫傳回的 HWND 指標`GetFocus`函式的預覽處理常式的幕前執行緒。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果登錄成功。或其他原因的錯誤值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonpreviewhandlertranslateacceleratora--cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 指示預覽處理常式來處理按鍵，從預覽處理常式正在執行的程序的訊息幫浦中向上傳遞。  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>參數  
 `pmsg`  
 [in]視窗訊息指標。  
  
### <a name="return-value"></a>傳回值  
 如果可以由預覽處理常式處理按鍵訊息，此處理常式加以處理，並傳回 S_OK。 如果預覽處理常式無法處理按鍵訊息，它會提供它透過主機`IPreviewHandlerFrame::TranslateAccelerator`。 如果主應用程式處理訊息時，這個方法會傳回 S_OK。 如果主應用程式不會處理訊息，這個方法會傳回 S_FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonrichpreviewbackcolorchangeda--cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 豐富的預覽背景色彩變更時呼叫。  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonrichpreviewfontchangeda--cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 豐富的預覽字型變更時呼叫。  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonrichpreviewsitechangeda--cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 豐富的預覽網站已經變更時呼叫。  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonrichpreviewtextcolorchangeda--cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 豐富的預覽文字色彩變更時呼叫。  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsavedocumenta--cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument  
 儲存檔案] 或 [另存新檔命令中的架構所呼叫。  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 指向檔案應該儲存的完整路徑。  
  
### <a name="return-value"></a>傳回值  
 已成功儲存文件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會開啟指定的檔案，呼叫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)文件的資料寫入至檔案，然後將文件標記為清除。 如果您想要執行特殊處理的架構儲存文件時，覆寫這個函式。 例如，您可以撰寫應用程式的文件，代表資料庫，而不是個別檔案中的記錄。  
  
##  <a name="a-nameonunloadhandlera--cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 卸載預覽處理常式時，由架構呼叫。  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonupdatefilesendmaila--cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail  
 可讓**ID_FILE_SEND_MAIL**命令郵件支援 (MAPI) 是否存在。  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件相關聯**ID_FILE_SEND_MAIL**命令。  
  
### <a name="remarks"></a>備註  
 否則函式會移除**ID_FILE_SEND_MAIL**命令從功能表中，包括上述分隔符號或功能表項目會視情況下。 如果啟用 MAPI MAPI32。DLL 會在路徑中，以及獲得 [Mail] 區段中。INI 檔案中，MAPI =&1;。 大部分的應用程式檔案 功能表上，將此命令。  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 請參閱文章[MAPI 主題](../../mfc/mapi.md)和[MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="a-nameprecloseframea--cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame  
 終結框架視窗，架構會呼叫此成員函式。  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 `pFrame`  
 指標[CFrameWnd](../../mfc/reference/cframewnd-class.md)保存相關聯**CDocument**物件。  
  
### <a name="remarks"></a>備註  
 您可以覆寫來提供自訂清除，但請務必呼叫基底類別。  
  
 預設值是`PreCloseFrame`不做任何動作**CDocument**。 **CDocument**-衍生的類別[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此成員函式。  
  
##  <a name="a-namereadnextchunkvaluea--cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 讀取的下一個區塊的值。  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>參數  
 `ppValue`  
 [out]函式傳回時，`ppValue`包含可讀取的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namereleasefilea--cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile  
 此成員函式是由發行檔案，因此可以使用其他應用程式的架構所呼叫。  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>參數  
 `pFile`  
 釋出 CFile 物件的指標。  
  
 `bAbort`  
 指定檔案是否要使用發行`CFile::Close`或`CFile::Abort`。 **FALSE**如果檔案是使用發行[CFile::Close](../../mfc/reference/cfile-class.md#close);**TRUE**如果檔案是使用發行[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="remarks"></a>備註  
 如果`bAbort`是**TRUE**，`ReleaseFile`呼叫`CFile::Abort`，並且檔案時。 `CFile::Abort`不會擲回例外狀況。  
  
 如果`bAbort`是**FALSE**，`ReleaseFile`呼叫`CFile::Close`和釋放檔案。  
  
 覆寫此成員函式釋放檔案之前，需要使用者動作。  
  
##  <a name="a-nameremovechunka--cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk  
 移除具有指定之 GUID。  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>參數  
 `Guid`  
 指定要移除區塊的 GUID。  
  
 `Pid`  
 指定要移除區塊的 PID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremoveviewa--cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView  
 呼叫此函式可卸離的文件的檢視。  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pView`  
 指向要移除的檢視。  
  
### <a name="remarks"></a>備註  
 此函式的文件; 相關聯的檢視清單中移除指定的檢視它也會將設定檢視的文件指標**NULL**。 框架視窗已關閉或已關閉的分隔視窗窗格時，則架構會呼叫此函數。  
  
 只有當您手動卸離的檢視，請呼叫此函式。 通常您會讓卸離的文件和檢視表定義架構[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)文件類別、 檢視類別和框架視窗類別建立關聯的物件。  
  
 請參閱範例[AddView](#addview)實作範例。  
  
##  <a name="a-namereportsaveloadexceptiona--cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 如果發生例外狀況時呼叫 (通常[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveException](../../mfc/reference/carchiveexception-class.md)) 時，儲存或載入文件。  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 指向所要的文件的名稱儲存或載入。  
  
 *e*  
 已擲回的例外狀況的點。 可能是**NULL**。  
  
 *bSaving*  
 旗標，指出哪一個作業正在進行。如果文件儲存，0 如果文件載入為非零。  
  
 `nIDPDefault`  
 如果函式未指定更特定的顯示錯誤訊息的識別碼。  
  
### <a name="remarks"></a>備註  
 預設實作會檢查例外狀況物件，並尋找能具體描述所造成的錯誤訊息。 如果找不到特定的訊息，或如果*e*是**NULL**，由指定的一般訊息`nIDPDefault`參數使用。 函式接著會顯示包含錯誤訊息的訊息方塊。 如果您想要提供額外的自訂錯誤訊息，請覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="a-namesavemodifieda--cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::SaveModified  
 架構修改的文件關閉之前呼叫。  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>傳回值  
 安全地繼續並關閉文件; 如果為非零0，表示不會關閉文件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會顯示訊息方塊，詢問使用者是否要將變更儲存至文件中，如果您未做任何。 如果您的程式都需要不同的提示程序，請覆寫這個函式。 這是進階可覆寫。  
  
##  <a name="a-namesetchunkvaluea--cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue  
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
  
##  <a name="a-namesetmodifiedflaga--cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 在您進行任何修改文件之後，請呼叫此函式。  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 旗標，指出是否已修改文件。  
  
### <a name="remarks"></a>備註  
 一致的方式呼叫此函數，您可以確保架構會提示使用者關閉文件之前先儲存變更。 通常您應該使用的預設值**TRUE**的`bModified`參數。 若要標記的乾淨的文件 （未修改），呼叫此函數中使用的值**FALSE**。  
  
##  <a name="a-namesetpathnamea--cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName  
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
 判斷是否有檔案名稱新增至最近使用過 (MRU) 檔案清單。 如果**為 TRUE，**加入檔案名稱; 如果**FALSE**，會將其加入。  
  
### <a name="remarks"></a>備註  
 值而定`bAddToMRU`加入，或未加入至應用程式所維護的 MRU 清單的路徑。 請注意，某些文件不相關聯的磁碟檔案。 只有當您正在覆寫預設實作，來開啟和儲存架構所使用的檔案，請呼叫此函式。  
  
##  <a name="a-namesettitlea--cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle  
 呼叫此函式可指定文件的標題 （框架視窗的標題列中顯示的字串）。  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>參數  
 `lpszTitle`  
 指向要做為文件的標題字串。  
  
### <a name="remarks"></a>備註  
 呼叫此函式會更新所有顯示的文件的框架視窗的標題。  
  
##  <a name="a-nameupdateallviewsa--cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews  
 修改文件之後，請呼叫此函式。  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 指向修改文件中，檢視或**NULL**如果所有的檢視更新。  
  
 `lHint`  
 包含有關修改資訊。  
  
 `pHint`  
 指向以儲存修改的相關資訊的物件。  
  
### <a name="remarks"></a>備註  
 在您呼叫後，您應該呼叫此函式[SetModifiedFlag](#setmodifiedflag)成員函式。 此函式，就會通知附加至文件，除了由指定的檢視每個檢視`pSender`，已修改過的文件。 一般都會呼叫此函式從您的檢視類別之後使用者已透過檢視文件。  
  
 此函數會呼叫[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)的文件之外傳送的每個成員函式檢視，請傳遞`pHint`和`lHint`。 使用這些參數將資訊傳遞至相關文件所做的修改檢視。 您可以編碼資訊使用`lHint`和 （或) 您可以定義[CObject](../../mfc/reference/cobject-class.md)-衍生類別，以儲存修改的相關資訊，並傳遞物件，該類別使用的`pHint`。 覆寫`CView::OnUpdate`成員函式中的您[CView](../../mfc/reference/cview-class.md)-衍生的類別，來最佳化更新檢視的顯示根據傳遞的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&64;](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 範例 NPP](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)

