---
title: CDocTemplate 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
dev_langs:
- C++
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd7e80d3c01cf84080ba2b5851da99584122ec4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023939"
---
# <a name="cdoctemplate-class"></a>CDocTemplate 類別
定義文件範本基本功能的抽象基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|建構 `CDocTemplate` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|將文件加入至範本。|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|關閉所有使用此範本相關聯的文件。|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|建立新的文件。|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|建立新的框架視窗，其中包含文件和檢視。|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|建立已啟用 OLE 的框架視窗。|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|建立子框架用於豐富的預覽。|  
|[CDocTemplate::GetDocString](#getdocstring)|擷取的文件類型相關聯的字串。|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|擷取與此範本關聯的第一個文件的位置。|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|擷取文件和下一個位置。|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|初始化框架視窗中，並選擇性地使其可見。|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|載入的資源指定`CDocTemplate`或衍生類別。|  
|[CDocTemplate::MatchDocType](#matchdoctype)|決定文件類型和此範本之間的比對的信心程度。|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|開啟 路徑名稱所指定的檔案。|  
|[CDocTemplate::RemoveDocument](#removedocument)|從範本移除文件。|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|儲存所有文件與此範本關聯的已修改。|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|編輯就地 OLE 項目時，請決定適用於 OLE 容器資源。|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|文件視窗的標題列中顯示的預設標題。|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|跨處理序的設定預覽處理常式。|  
|[Coleresizebar](#setserverinfo)|伺服器文件內嵌或特殊處理時，請決定資源與類別。|  
  
## <a name="remarks"></a>備註  
 您通常會在您的應用程式的實作中建立一或多個文件範本`InitInstance`函式。 文件範本會定義三種類型的類別之間的關聯性：  
  
-   文件類別，衍生自`CDocument`。  
  
-   檢視類別，會顯示上面所列的文件類別的資料。 您可以衍生此類別`CView`， `CScrollView`， `CFormView`，或`CEditView`。 (您也可以使用`CEditView`直接。)  
  
-   框架視窗類別，其中包含檢視。 為單一文件介面 (SDI) 應用程式中，類別衍生此類別從`CFrameWnd`。 針對多個文件介面 (MDI) 應用程式中，類別衍生此類別從`CMDIChildWnd`。 如果您不需要自訂框架視窗的行為，您可以使用`CFrameWnd`或`CMDIChildWnd`直接而不需衍生您自己的類別。  
  
 您的應用程式有一個用於每一種支援的文件的文件範本。 例如，如果您的應用程式支援試算表和文字文件，應用程式會有兩個文件範本物件。 每個文件範本負責建立和管理其類型的所有文件。  
  
 文件範本將指標儲存至`CRuntimeClass`文件、 檢視和框架視窗類別的物件。 這些`CRuntimeClass`建構的文件範本時，會指定物件。  
  
 文件範本包含與文件類型 （例如功能表、 圖示或快速鍵對應表資源） 所使用的資源識別碼。 文件範本也有包含其文件類型的其他資訊的字串。 其中包括文件類型 （例如，「 工作表 」） 和檔案的副檔名 (例如，".xls") 的名稱。 （選擇性），它可以包含其他應用程式的使用者介面、 Windows 檔案管理員 中，與物件連結與嵌入 (OLE) 支援所使用的字串。  
  
 如果您的應用程式的 OLE 容器和/或伺服器，文件範本也會定義在就地啟用期間所用的功能表的識別碼。 如果您的應用程式是 OLE 伺服器，文件範本會定義為工具列和功能表就地啟用期間所使用的識別碼。 您可以指定這些其他的 OLE 資源藉由呼叫`SetContainerInfo`和`SetServerInfo`。  
  
 因為`CDocTemplate`是抽象類別，您無法直接使用類別。 一般應用程式會使用兩個的其中一個`CDocTemplate`-衍生的 Mfc 程式庫所提供的類別： `CSingleDocTemplate`，它會實作 SDI，和`CMultiDocTemplate`，它會實作 MDI。 使用文件範本，請參閱這些類別，如需詳細資訊。  
  
 如果您的應用程式需要從 SDI 或 MDI 本質上不同的使用者介面典範，您可以衍生自己的類別，從`CDocTemplate`。  
  
 如需詳細資訊`CDocTemplate`，請參閱 <<c2> [ 文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 若要加入至範本的文件中使用此函式。  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>參數  
 *pDoc*  
 要加入的文件指標。  
  
### <a name="remarks"></a>備註  
 在衍生的類別[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)並[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)覆寫這個函式。 如果您衍生您自己的文件樣板類別，從`CDocTemplate`，衍生的類別必須覆寫這個函式。  
  
##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate  
 建構 `CDocTemplate` 物件。  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>參數  
 *nIDResource*  
 指定文件類型所使用的資源的識別碼。 這可能包括功能表、 圖示、 快速鍵對應表和字串資源。  
  
 最多七個以 '\n' 字元分隔的子字串所組成的字串資源 （不包含子字串時，需要 '\n' 字元做為預留位置; 不過，不需要尾端的 '\n' 字元;）這些子字串會描述文件類型。 如需子字串的資訊，請參閱[GetDocString](#getdocstring)。 應用程式的資源檔中找到此字串資源。 例如:   

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

 請注意，字串開頭 '\n' 字元;這是因為第一個子字串不能用於 MDI 應用程式，因此就不會包含。 您可以編輯這個字串使用字串編輯器;整個字串會顯示為單一項目在字串編輯器中中,，不為七個不同的項目。  
  
 *pDocClass*  
 指向`CRuntimeClass`文件類別的物件。 這個類別是`CDocument`-衍生的類別定義以代表您的文件。  
  
 *pFrameClass*  
 指向`CRuntimeClass`框架視窗類別的物件。 這個類別可以`CFrameWnd`-衍生的類別，或者它可以是`CFrameWnd`本身如果您想要為您的主框架視窗的預設行為。  
  
 *pViewClass*  
 指向`CRuntimeClass`檢視類別的物件。 這個類別是`CView`-衍生的類別，您會定義顯示您的文件。  
  
### <a name="remarks"></a>備註  
 使用此成員函式來建構`CDocTemplate`物件。 以動態方式配置`CDocTemplate`物件，並將它傳遞給[CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)從`InitInstance`應用程式類別的成員函式。  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 呼叫此成員函式，以關閉所有開啟的文件。  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>參數  
 *bEndSession*  
 未使用。  
  
### <a name="remarks"></a>備註  
 此成員函式通常是作為檔案結束命令的一部分。 此函式的預設實作會呼叫[CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents)成員函式來刪除文件的資料，然後關閉所有檢視的框架視窗附加至文件。  
  
 如果您想要要求使用者執行特殊清除處理序在關閉文件之前，請覆寫這個函式。 比方說，如果文件代表資料庫中的記錄，您可能想要覆寫這個函式來關閉資料庫。  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 呼叫此成員函式，來建立新的文件，此文件範本與相關聯的類型。  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>傳回值  
 新建立的文件或如果發生錯誤則為 NULL 指標。  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 建立新的框架視窗，其中包含文件和檢視。  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>參數  
 *pDoc*  
 新的框架視窗應參考的文件。 可以是 NULL。  
  
 *其他*  
 隨著新的框架視窗所在的框架視窗。 可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 新建立的框架視窗中或如果發生錯誤則為 NULL 指標。  
  
### <a name="remarks"></a>備註  
 `CreateNewFrame` 使用`CRuntimeClass`物件傳遞至建構函式來建立新的框架視窗與檢視和附加的文件。 如果*pDoc*參數為 NULL，framework 輸出追蹤訊息。  
  
 *其他*參數用來實作新視窗的命令。 它提供用來建立新的框架視窗的模型上的框架視窗。 新的框架視窗通常會建立不可見的。 呼叫此函式來建立新檔案] 和 [開啟檔案的標準架構實作外部框架視窗。  
  
##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame  
 建立的 OLE 框架視窗。  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 畫面格的父視窗的指標。  
  
 *pDoc*  
 新的 OLE 框架視窗應參考的文件的指標。  
  
 *bCreateView*  
 判斷是否要將檢視建立畫面格以及。  
  
### <a name="return-value"></a>傳回值  
 如果成功，框架視窗的指標否則為 NULL。  
  
### <a name="remarks"></a>備註  
 如果*bCreateView*為零，會建立空白的框架。  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 擷取的文件類型相關聯的字串。  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>參數  
 *rString*  
 參考`CString`函式傳回時，將包含字串的物件。  
  
 *index*  
 從描述文件類型的字串擷取子字串的索引。 這個參數的值可以是下列其中一個：  
  
- `CDocTemplate::windowTitle` 會出現在應用程式視窗的標題列 (例如，「 Microsoft Excel 」) 的名稱。 呈現只在 SDI 應用程式的文件範本中。  
  
- `CDocTemplate::docName` 預設文件名稱 （例如，「 工作表 」） 的根。 這個根目錄中，再加上數字，使用於此類型的新文件的預設名稱每當使用者選擇新的命令，從 [檔案] 功能表 （例如，「 1 」 或 「 Sheet2"）。 如果未指定，則會使用 「 未命名的"為預設值。  
  
- `CDocTemplate::fileNewName` 此文件類型的名稱。 如果應用程式支援多個文件類型，這個字串會顯示在開新檔案的對話方塊中 （例如，「 工作表 」）。 如果未指定，此文件類型為無法存取使用的新檔案的命令。  
  
- `CDocTemplate::filterName` 文件類型和萬用字元篩選條件比對此類型的文件的描述。 此字串會顯示在 檔案類型下拉式清單中，開啟舊檔 對話方塊中 （例如，「 工作表 (*.xls)"） 中。 如果未指定，此文件類型為無法使用 [開啟舊檔] 命令。  
  
- `CDocTemplate::filterExt` 此類型 (例如，".xls") 的文件的副檔名。 如果未指定，此文件類型為無法使用 [開啟舊檔] 命令。  
  
- `CDocTemplate::regFileTypeId` 在 Windows 註冊資料庫中儲存的文件類型的識別項。 此字串是僅供內部使用 (例如，"ExcelWorksheet 」)。 如果未指定，文件的類型無法註冊使用 Windows 檔案管理員。  
  
- `CDocTemplate::regFileTypeName` 在 註冊資料庫中儲存的文件類型的名稱。 此字串可能會顯示在對話方塊中的應用程式以存取系統註冊資料庫 （例如，"Microsoft Excel 工作表 」）。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果找不到指定的子字串;否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取特定的子字串，描述的文件類型。 字串，包含這些子字串會儲存在文件範本，而衍生自應用程式的資源檔中的字串。 架構會呼叫此函式可取得所需的應用程式的使用者介面字串。 如果您已經指定您的應用程式的文件檔案的副檔名，架構也會呼叫此函式時將項目新增至 Windows 註冊資料庫;這可讓從 Windows 檔案管理員中開啟的文件。  
  
 呼叫此函式，只有當您衍生您自己的類別，從`CDocTemplate`。  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 擷取與此範本關聯的第一個文件的位置。  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>傳回值  
 位置值，可用來逐一查看與此文件範本; 相關聯的文件清單或者，如果清單是空的則為 NULL。  
  
### <a name="remarks"></a>備註  
 使用此函數來取得與此範本關聯的文件清單中第一個文件的位置。 使用位置值當做引數[CDocTemplate::GetNextDoc](#getnextdoc)來逐一查看與範本相關聯的文件清單。  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)並[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)都會覆寫這個純虛擬函式。 您可以從衍生的任何類別`CDocTemplate`也必須覆寫這個函式。  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 擷取所識別的清單項目*Rpo*，然後設定*Rpo*位置值的清單中的下一個項目。  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>傳回值  
 在此範本相關聯的文件清單中下一個文件指標。  
  
### <a name="parameters"></a>參數  
 *Rpo*  
 先前呼叫所傳回的位置值的參考[GetFirstDocPosition](#getfirstdocposition)或`GetNextDoc`。  
  
### <a name="remarks"></a>備註  
 如果擷取的項目是在清單中，最後一則新值*Rpo*設為 NULL。  
  
 您可以使用`GetNextDoc`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫[GetFirstDocPosition](#getfirstdocposition)。  
  
 您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 初始化框架視窗中，並選擇性地使其可見。  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pFrame*  
 需要初始更新框架視窗。  
  
 *pDoc*  
 框架有相關聯的文件。 可以是 NULL。  
  
 *bMakeVisible*  
 表示框架是否應該都變成可見且作用中。  
  
### <a name="remarks"></a>備註  
 呼叫`IntitialUpdateFrame`之後建立新的框架，具有`CreateNewFrame`。 呼叫此函式可讓以接收該框架視窗中檢視其`OnInitialUpdate`呼叫。 此外，如果有先前未使用中的檢視，框架視窗的主要檢視會變成作用;主要的檢視是具有子系識別碼的 AFX_IDW_PANE_FIRST 的檢視。 最後，框架視窗就會顯示如果*bMakeVisible*為非零。 如果*bMakeVisible*為零，目前的焦點和框架視窗的可見狀態將保持不變。  
  
 您不需要呼叫此函式時使用的新檔案] 和 [開啟檔案架構的實作。  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 載入的資源指定`CDocTemplate`或衍生類別。  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>備註  
 若要載入的資源架構會呼叫此成員函式指定`CDocTemplate`或衍生類別。 通常它是在建構期間，除了時呼叫全域正在建構的範本。 在此情況下，呼叫`LoadTemplate`延遲直到[CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)呼叫。  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 決定文件類型和此範本之間的比對的信心程度。  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>參數  
 *lpszPathName*  
 判斷型別之檔案的路徑名稱。  
  
 *rpDocMatch*  
 如果指定的檔案指派比對的文件，文件的指標*lpszPathName*已經開啟。  
  
### <a name="return-value"></a>傳回值  
 值，以從**信心**列舉型別，其定義，如下所示：  
  
```  
enum Confidence  
    {  
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };  
```  
  
### <a name="remarks"></a>備註  
 使用此函數來決定要用於開啟檔案的文件範本的類型。 如果您的應用程式支援多個檔案類型，例如，您可以使用此函式來決定哪一個可用的文件範本適用於指定的檔案藉由呼叫`MatchDocType`開啟，並選擇根據範本中每個範本傳回的信心值。  
  
 如果指定的檔案*lpszPathName*已經開啟，此函數會傳回`CDocTemplate::yesAlreadyOpen`，並將複製的檔案`CDocument`成為在物件的物件*rpDocMatch*。  
  
 如果檔案不是開啟，但是中的擴充功能*lpszPathName*符合所指定的副檔名`CDocTemplate::filterExt`，此函數會傳回`CDocTemplate::yesAttemptNative`並設定*rpDocMatch*為 NULL。 如需詳細資訊`CDocTemplate::filterExt`，請參閱 < [CDocTemplate::GetDocString](#getdocstring)。  
  
 如果兩種情況下，則為 true，則函式會傳回`CDocTemplate::yesAttemptForeign`。  
  
 預設實作不會傳回`CDocTemplate::maybeAttemptForeign`或`CDocTemplate::maybeAttemptNative`。 覆寫這個函式來實作適合您的應用程式，可能使用 從這兩個值的型別符合邏輯**信心**列舉型別。  
  
##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile  
 開啟檔案的路徑所指定。  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>參數  
*lpszPathName*<br/>
[in]指標，包含要開啟的文件之檔案的路徑。  
  
*bAddToMRU*<br/>
[in]TRUE 表示在文件是其中一個最新的檔案;FALSE 表示文件不是其中一個最新的檔案。  
  
### <a name="return-value"></a>傳回值  
 其檔案的命名方式的文件的指標*lpszPathName*;如果不成功，則為 NULL。  
  
### <a name="remarks"></a>備註  
 開啟的檔案的路徑由*lpszPathName*。 如果*lpszPathName*為 NULL，就會建立新的檔案，其中包含與此範本關聯類型的文件。  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 移除所指的文件*pDoc*從與此範本關聯的文件的清單。  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>參數  
 *pDoc*  
 要移除文件的指標。  
  
### <a name="remarks"></a>備註  
 在衍生的類別`CMultiDocTemplate`和`CSingleDocTemplate`覆寫這個函式。 如果您衍生您自己的文件樣板類別，從`CDocTemplate`，衍生的類別必須覆寫這個函式。  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 儲存修改過的所有文件。  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>傳回值  
 非零成功; 如果否則為 0。  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo  
 編輯就地 OLE 項目時，請決定適用於 OLE 容器資源。  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>參數  
 *nIDOleInPlaceContainer*  
 內嵌的物件啟動時所使用的資源識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將設定就地啟動 OLE 物件時要使用的資源。 這些資源可能包括功能表與快速鍵對應表。 通常會呼叫此函數[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)函式應用程式。  
  
 與相關聯的功能表*nIDOleInPlaceContainer*包含分隔符號，讓已啟動的就地項目合併的功能表與容器應用程式的功能表。 如需有關合併伺服器和容器的功能表的詳細資訊，請參閱[功能表和資源 (OLE)](../../mfc/menus-and-resources-ole.md)。  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 呼叫此函式來載入文件的預設標題，並顯示文件的標題列中。  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>參數  
 *pDocument*  
 職稱是設定文件的指標。  
  
### <a name="remarks"></a>備註  
 在預設標題上的資訊，請參閱 popis`CDocTemplate::docName`中[CDocTemplate::GetDocString](#getdocstring)。  
  
##  <a name="setserverinfo"></a>  Coleresizebar  
 伺服器文件內嵌或特殊處理時，請決定資源與類別。  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>參數  
 *nIDOleEmbedding*  
 另一個視窗中開啟內嵌的物件時所使用的資源識別碼。  
  
 *nIDOleInPlaceServer*  
 就地啟動時，內嵌的物件是所使用的資源識別碼。  
  
 *pOleFrameClass*  
 指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構，其中包含建立就地啟用時的框架視窗物件的類別資訊。  
  
 *pOleViewClass*  
 指標`CRuntimeClass`結構，其中包含建立就地啟用時的檢視物件的類別資訊。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以識別使用者要求內嵌物件的啟動時將伺服器應用程式所使用的資源。 這些資源包括功能表與快速鍵對應表。 通常會呼叫此函數`InitInstance`應用程式。  
  
 與相關聯的功能表*nIDOleInPlaceServer*包含允許容器的功能表與 [伺服器] 功能表合併的分隔符號。 如需有關合併伺服器和容器的功能表的詳細資訊，請參閱[功能表和資源 (OLE)](../../mfc/menus-and-resources-ole.md)。  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 建立子框架用於豐富的預覽。  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 （通常是由命令介面提供） 的父視窗指標。  
  
 *pDoc*  
 文件物件，將會預覽其內容指標。  
  
### <a name="return-value"></a>傳回值  
 有效指標`CFrameWnd`物件，或如果建立失敗，則為 NULL。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 設定外的處理序預覽處理常式。  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>參數  
 *nIDPreviewFrame*  
 指定的資源識別碼的預覽畫面。  
  
 *pPreviewFrameClass*  
 指定的預覽畫面格的執行階段類別資訊結構的指標。  
  
 *pPreviewViewClass*  
 指定 [預覽] 檢視的執行階段類別資訊結構的指標。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate 類別](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate 類別](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CScrollView 類別](../../mfc/reference/cscrollview-class.md)   
 [CEditView 類別](../../mfc/reference/ceditview-class.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)
