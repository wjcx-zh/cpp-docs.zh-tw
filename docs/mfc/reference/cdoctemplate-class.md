---
title: CDocTemplate 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 3376b8febe8ae4586ce649f3f83386875acb678f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375497"
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
|[CDocTemplate:CDocTemplate](#cdoctemplate)|建構 `CDocTemplate` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocTemplate:: 新增文件](#adddocument)|將文件添加到範本。|
|[CDocTemplate::關閉所有文件](#closealldocuments)|關閉與此範本關聯的所有文檔。|
|[CDocTemplate::建立新文件](#createnewdocument)|創建新文檔。|
|[CDocTemplate::建立新框架](#createnewframe)|創建新框架視窗,其中包含文檔和檢視。|
|[CDocTemplate::建立OleFrame](#createoleframe)|建立啟用 OLE 的框架視窗。|
|[CDocTemplate::建立預覽框架](#createpreviewframe)|創建用於"豐富預覽"的子框架。|
|[CDocTemplate::取得DocString](#getdocstring)|檢索與文件類型關聯的字串。|
|[CDocTemplate:取得第一個文件位置](#getfirstdocposition)|檢索與此範本關聯的第一個文檔的位置。|
|[CDocTemplate::取得下一個文件](#getnextdoc)|檢索文件和下一個文檔的位置。|
|[CDocTemplate::初始更新框架](#initialupdateframe)|初始化框架視窗,並選擇性地使其可見。|
|[CDocTemplate:載入樣本](#loadtemplate)|載入給定`CDocTemplate`類或派生類的資源。|
|[CDocTemplate::符合文件類型](#matchdoctype)|確定文件類型和此範本之間匹配的置信度。|
|[CDocTemplate::開啟檔案檔案](#opendocumentfile)|開啟由路徑名稱指定的檔。|
|[CDocTemplate::刪除文件](#removedocument)|從範本中刪除文檔。|
|[CDocTemplate::儲存所有修改](#saveallmodified)|保存與此範本關聯的所有已修改的文檔。|
|[CDocTemplate::設定容器資訊](#setcontainerinfo)|在編輯就地 OLE 項時確定 OLE 容器的資源。|
|[CDocTemplate::設定預設標題](#setdefaulttitle)|在文件視窗的標題列中顯示預設標題。|
|[CDocTemplate::設定預覽資訊](#setpreviewinfo)|進程預覽處理程序的設置。|
|[CDocTemplate::設定伺服器資訊](#setserverinfo)|確定伺服器文件在就地嵌入或編輯時的資源和類。|

## <a name="remarks"></a>備註

通常在應用程式`InitInstance`函數的實現中創建一個或多個文檔範本。 文件樣本定義三種類型的類之間的關係:

- 從 派生的`CDocument`文檔類。

- 視圖類,它顯示來自上面列出的文檔類的數據。 可以從`CView`派生此類`CScrollView`,`CFormView``CEditView`或 。 ( 您也可以直接`CEditView`使用 。

- 包含檢視的框架視窗類。 對於單個文檔介面 (SDI) 應用程式,`CFrameWnd`從派生 此類。 對於多個文件介面 (MDI) 應用程式,從`CMDIChildWnd`派生 此類。 如果不需要自定義框架視窗的行為,則可以使用或直接在不`CFrameWnd`派生自己的類的情況下使用`CMDIChildWnd`或 直接自定義框架視窗。

應用程式對於它支援的每種類型的文檔都有一個文檔範本。 例如,如果應用程式同時支援電子表格和文本文件,則應用程式有兩個文檔範本物件。 每個文件範本負責創建和管理其類型的所有文檔。

文件範本儲存指向文件、檢視`CRuntimeClass`和框架視窗類物件的指標。 這些`CRuntimeClass`物件在構造文檔範本時指定。

文件範本包含與文件類型(如功能表、圖示或快捷表資源)一起使用的資源的 ID。 文件範本還具有包含有關其文件類型的其他資訊的字串。 其中包括文件類型的名稱(例如,"工作表")和檔擴展名(例如,".xls")。 或者,它可以包含應用程式的使用者介面、Windows 檔管理器以及物件連結和嵌入 (OLE) 支援使用的其他字串。

如果應用程式是 OLE 容器和/或伺服器,文檔範本還會定義就地啟動期間使用的功能表的 ID。 如果應用程式是 OLE 伺服器,則文件範本將定義就地激活期間使用的工具列和功能表的 ID。 通過調用`SetContainerInfo``SetServerInfo`和 指定這些額外的 OLE 資源。

因為`CDocTemplate`是抽象類,因此不能直接使用該類。 典型的應用程式使用 Microsoft`CDocTemplate`基礎類 庫提供的兩派生類之`CSingleDocTemplate`一:, 實現`CMultiDocTemplate`SDI,和 ,實現 MDI。 有關使用文檔範本的詳細資訊,請參閱這些類。

如果應用程式需要與 SDI 或 MDI 根本不同的使用者介面範例`CDocTemplate`,則可以從 派生您自己的類。

有關的詳細資訊`CDocTemplate`,請參考[文件樣本與文件/檢視建立過程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate:: 新增文件

使用此函數將文檔添加到範本。

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向要添加的文件的指標。

### <a name="remarks"></a>備註

派生類[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)和[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)重寫此函數。 如果派生自`CDocTemplate`,派生類必須重寫此函數。

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate:CDocTemplate

建構 `CDocTemplate` 物件。

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nID資源*<br/>
指定與文件類型一起使用的資源的識別碼。 這可能包括功能表、圖示、快速鍵表和字串資源。

字串資源由最多七個子字串組成,由"\n"字元分隔(如果不包括子字串,則需要"\n"字元作為佔位元;但是,尾隨的"\n"字元是不需要的);這些子字串描述文件類型。 有關子字串的資訊,請參閱[GetDocString](#getdocstring)。 此字串資源位於應用程式的資源檔中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

請注意,字串以「\n」字元開頭;這是因為第一個子字串不用於 MDI 應用程式,因此不包括。 您可以使用字串編輯器編輯此字串;但是,使用字串編輯器可以編輯此字串。整個字串在字串編輯器中顯示為單個條目,而不是七個單獨的條目。

*pDocClass*<br/>
指向文檔`CRuntimeClass`類的物件。 此類是您定義的`CDocument`表示文檔的派生類。

*pFrame 類別*<br/>
指向框架視窗`CRuntimeClass`類的物件。 類可以是`CFrameWnd`派生類,也可以`CFrameWnd`是自己的,如果您想要主框架視窗的默認行為。

*pView 類別*<br/>
指向視圖類`CRuntimeClass`的物件。 此類是您為`CView`顯示文檔而定義的派生類。

### <a name="remarks"></a>備註

使用此成員函式建構物件`CDocTemplate`。 動態分配`CDocTemplate`物件並將其傳遞給[CWinApp::](../../mfc/reference/cwinapp-class.md#adddoctemplate)`InitInstance`從應用程式類的成員函數添加 DocTemplate。

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate::關閉所有文件

呼叫此成員函數關閉所有打開的文檔。

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>參數

*bEndSession*<br/>
未使用。

### <a name="remarks"></a>備註

此成員函數通常用作檔退出命令的一部分。 此函數的預設實現調用[CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents)成員函數,以刪除文檔的數據,然後關閉附加到文檔的所有檢視的幀視窗。

如果要要求使用者在文檔關閉之前執行特殊的清理處理,請覆蓋此函數。 例如,如果文檔表示資料庫中的記錄,則可能需要重寫此函數以關閉資料庫。

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate::建立新文件

呼叫此成員函數以創建與此文件範本關聯的類型的新文件。

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>傳回值

指向新建立的文件的指標,如果發生錯誤,則指向 NULL。

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate::建立新框架

創建新框架視窗,其中包含文檔和檢視。

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
新框架視窗應引用的文檔。 可以是 NULL。

*p其他*<br/>
新框架視窗所基於的幀視窗。 可以是 NULL。

### <a name="return-value"></a>傳回值

指向新創建的幀視窗的指標,如果發生錯誤,則指向 NULL。

### <a name="remarks"></a>備註

`CreateNewFrame`使用傳遞給`CRuntimeClass`建構函數的物件創建一個附加檢視和文檔的新框架視窗。 如果*pDoc*參數為 NULL,則框架將輸出 TRACE 消息。

*pOther*參數用於實現"視窗新"命令。 它提供了一個框架視窗,用於對新的框架視窗進行建模。 新的框架視窗通常是不可見的。 呼叫此函數以在檔案新建和文件打開的標準框架實現之外創建框架視窗。

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate::建立OleFrame

創建 OLE 框架視窗。

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向幀的父視窗的指標。

*pDoc*<br/>
指向新 OLE 框架視窗應引用的文件的指標。

*b 建立檢視*<br/>
確定是否隨框架一起創建檢視。

### <a name="return-value"></a>傳回值

指向幀視窗的指標(如果成功);如果成功,則指向框架視窗的指標。否則 NULL。

### <a name="remarks"></a>備註

如果*bCreateView*為零,則創建一個空幀。

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate::取得DocString

檢索與文件類型關聯的字串。

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>參數

*rString*<br/>
對在`CString`函數返回時將包含字串的物件的引用。

*指數*<br/>
從描述文件類型的字串中檢索的子字串的索引。 這個參數的值可以是下列其中一個：

- `CDocTemplate::windowTitle`顯示在應用程式視窗的標題列中的名稱(例如,"Microsoft Excel")。 僅在 SDI 應用程式的文件樣本中顯示。

- `CDocTemplate::docName`默認文件名稱的根目錄(例如,"Sheet")。 當使用者從「檔案」功能選單中選擇「新建」命令(例如,「Sheet1」或「Sheet2」)時,此根(加上數位)用於此類型新文件的預設名稱。 如果未指定,"無標題"將用作預設值。

- `CDocTemplate::fileNewName`此文件類型的名稱。 如果應用程式支援多種類型的文件,則此字串將顯示在「檔案新建」對話框中(例如,「工作表」)。 如果未指定,則無法使用「檔案新建」命令存取文件類型。

- `CDocTemplate::filterName`文件類型的說明和匹配此類型的文件的通配符篩選器。 此字串顯示在「檔案打開」對話方塊中的「類型清單檔」 下拉清單中(例如,"工作表 (*.xls)")。 如果未指定,則無法使用檔案打開命令訪問文檔類型。

- `CDocTemplate::filterExt`此類型文件的擴展(例如,".xls")。 如果未指定,則無法使用檔案打開命令訪問文檔類型。

- `CDocTemplate::regFileTypeId`要存儲在 Windows 維護的註冊資料庫中的文件類型的標識碼。 此字串僅供內部使用(例如,"Excel工作表")。 如果未指定,則無法向 Windows 檔管理員註冊文件類型。

- `CDocTemplate::regFileTypeName`要存儲在註冊資料庫中的文件類型的名稱。 此字串可以顯示在訪問註冊資料庫的應用程式的對話方塊中(例如,"Microsoft Excel 工作表")。

### <a name="return-value"></a>傳回值

如果找到指定的子字串,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫此函數以檢索描述文件類型的特定子字串。 包含這些子字串的字串儲存在文件範本中,並且派生自應用程式資源檔中的字串。 框架呼叫此函數是為了獲取應用程式使用者介面所需的字串。 如果為應用程式的文檔指定了檔名副檔名,則在將條目添加到 Windows 註冊資料庫時,框架也會調用此功能;如果為應用程式的文檔指定了檔名副檔名,則框架還會調用此功能。這允許從 Windows 檔管理器打開文檔。

僅當從`CDocTemplate`派生自己的類時,才調用此函數。

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate:取得第一個文件位置

檢索與此範本關聯的第一個文檔的位置。

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>傳回值

可用於遍經與本文檔範本關聯的文檔清單的「位置」值;如果清單為空,則為 NULL。

### <a name="remarks"></a>備註

使用此函數可以獲取與此範本關聯的文件清單中的第一個文件的位置。 使用"位置"值作為[CDocTemplate 的參數::GetNextDoc](#getnextdoc)可以遍遍查看與範本關聯的文檔清單。

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)和[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)都重寫了此純虛擬函數。 派生自`CDocTemplate`的任何類也必須重寫此函數。

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate::取得下一個文件

檢索*由 rPos*標識的列表元素,然後將*rPos*設置到清單中下一個條目的"

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>傳回值

指向與此範本關聯的文件清單中的下一個文件的指標。

### <a name="parameters"></a>參數

*rPos*<br/>
對前一個調用[GetFirstDoc定位](#getfirstdocposition)或`GetNextDoc`返回的定位值的引用。

### <a name="remarks"></a>備註

如果檢索到的元素是清單中的最後一個元素,則*rPos*的新值將設置為 NULL。

如果使用對`GetNextDoc` [GetFirstDoc定位](#getfirstdocposition)的呼叫建立初始位置,則可以在轉發反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate::初始更新框架

初始化框架視窗,並選擇性地使其可見。

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
需要初始更新的幀視窗。

*pDoc*<br/>
框架關聯的文檔。 可以是 NULL。

*b 使可見*<br/>
指示幀是否應變得可見和活動。

### <a name="remarks"></a>備註

使用`IntitialUpdateFrame``CreateNewFrame`建立新的幀後呼叫 。 調用此函數會導致該幀視窗中的視圖接收其`OnInitialUpdate`調用。 此外,如果以前沒有活動視圖,則框架視窗的主視圖將變為活動檢視;主視圖是具有 AFX_IDW_PANE_FIRST 子 ID 的檢視。 最後,如果*bMakeVisible*是非零,則幀視窗變得可見。 如果*bMakeVisible*為零,則幀視窗的當前焦點和可見狀態將保持不變。

使用框架的「檔案新建」和「檔案打開」實現時,不必呼叫此功能。

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate:載入樣本

載入給定`CDocTemplate`類或派生類的資源。

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>備註

框架調用此成員函數以載入給定`CDocTemplate`類或派生類的資源。 通常,在構造期間調用它,除非範本是全域構造的。 在這種情況下,調用`LoadTemplate`將延遲到[CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)調用。

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate::符合文件類型

確定文件類型和此範本之間匹配的置信度。

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
要確定其類型的檔的路徑名稱。

*rpDocMatch*<br/>
如果*lpszPathName*指定的檔案已打開,則指向已分配匹配文件的文件的指標。

### <a name="return-value"></a>傳回值

**"信心**"枚舉中的值,定義如下:

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

使用此函數可以確定用於打開文件的文件範本的類型。 例如,如果應用程式支援多種文件類型,則可以使用此函數通過依次調用`MatchDocType`每個範本並根據返回的置信度值選擇範本來確定適用於給定檔的可用文件範本。

如果*lpszPathName*指定的檔案已開啟,則此函`CDocTemplate::yesAlreadyOpen`數將傳`CDocument`回該檔案的物件並將其複製到*rpDocMatch*上的物件中。

如果檔案未開啟,但*lpszPathName*中的副檔名`CDocTemplate::filterExt`與 指定的副`CDocTemplate::yesAttemptNative`檔名符合,則此函數將傳回並將*rpDocMatch*設定為 NULL。 有關詳細資訊,`CDocTemplate::filterExt`請參考[CDocTemplate:getDocString](#getdocstring)。

如果兩種情況都不正確,則函數將`CDocTemplate::yesAttemptForeign`返回 。

預設可傳`CDocTemplate::maybeAttemptForeign`回或`CDocTemplate::maybeAttemptNative`。 重寫此函數以實現適合應用程式的類型匹配邏輯,可能使用 **「信心」** 枚舉中的這兩個值。

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate::開啟檔案檔案

打開路徑指定的檔。

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
[在]指向包含要打開的文件的檔的路徑的指標。

*bAddtoMRU*<br/>
[在]TRUE 表示文檔是最新的檔之一;FALSE 表示文檔不是最新的檔之一。

### <a name="return-value"></a>傳回值

指向其檔案由*lpszPathName*命名的文件的指標。如果失敗,則為 NULL。

### <a name="remarks"></a>備註

開啟其路徑由*lpszPathName*指定的檔案。 如果*lpszPathName*為 NULL,則將建立新檔案,該檔包含與此樣本關聯的類型的文件。

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate::刪除文件

從與此範本關聯的文件清單中刪除*pDoc*指向的文檔。

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向要刪除的文件的指標。

### <a name="remarks"></a>備註

派生類`CMultiDocTemplate``CSingleDocTemplate`並 重寫此函數。 如果派生自`CDocTemplate`,派生類必須重寫此函數。

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate::儲存所有修改

保存已修改的所有文檔。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>傳回值

如果成功,則為非零;否則 0。

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate::設定容器資訊

在編輯就地 OLE 項時確定 OLE 容器的資源。

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>參數

*NIDOleInplace 容器*<br/>
啟動嵌入物件時使用的資源的 ID。

### <a name="remarks"></a>備註

呼叫此函數以設置在 OLE 物件就地啟動時要使用的資源。 這些資源可能包括功能表和加速器表。 此函數通常在應用程式的[CWinApp::initInstance](../../mfc/reference/cwinapp-class.md#initinstance)函數中調用。

與*nIDOleInPlace 容器*關聯的功能表包含分隔符,允許啟動的就地項的菜單與容器應用程式的功能表合併。 有關合併伺服器和容器功能表的詳細資訊,請參閱文章[「功能表和資源」(OLE)。](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate::設定預設標題

呼叫此函數以載入文件的預設標題,並將其顯示在文件的標題列中。

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>參數

*pDocument*<br/>
指向要設置其標題的文件的指標。

### <a name="remarks"></a>備註

有關預設標題的資訊,請參`CDocTemplate::docName`閱[CDocTemplate 中的說明::GetDocString](#getdocstring)。

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate::設定伺服器資訊

確定伺服器文件在就地嵌入或編輯時的資源和類。

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>參數

*nIDOle 嵌入*<br/>
在單獨的視窗中打開嵌入物件時使用的資源的 ID。

*nIDOleInplace 伺服器*<br/>
就地啟動嵌入物件時使用的資源的 ID。

*pOleFrame 類別*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標,其中包含發生就地啟動時創建的幀視窗物件的類資訊。

*pOleView 類別*<br/>
指向包含`CRuntimeClass`發生就地啟動時創建的檢視物件的類資訊的結構的指標。

### <a name="remarks"></a>備註

呼叫此成員函數以標識在使用者請求啟動嵌入物件時伺服器應用程式將使用的資源。 這些資源由功能表和快捷鍵表組成。 此函數通常在應用程式中呼叫`InitInstance`。

與*nIDOleInPlaceServer*關聯的功能表包含允許伺服器功能表與容器功能表合併的分隔符。 有關合併伺服器和容器功能表的詳細資訊,請參閱文章[「功能表和資源」(OLE)。](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate::建立預覽框架

創建用於"豐富預覽"的子框架。

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向父視窗的指標(通常由 Shell 提供)。

*pDoc*<br/>
指向文檔物件的指標,其內容將預覽。

### <a name="return-value"></a>傳回值

指向`CFrameWnd`物件的有效指標,如果建立失敗,則為 NULL。

### <a name="remarks"></a>備註

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate::設定預覽資訊

設置行程外預覽處理程式。

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>參數

*nID 預覽框架*<br/>
指定預覽幀的資源 ID。

*p 預覽框架類別*<br/>
指定指向預覽幀的運行時類資訊結構的指標。

*p預覽檢視類*<br/>
指定指向預覽檢視的運行時類資訊結構的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate 類別](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate 類別](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CScrollView 類別](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView 類別](../../mfc/reference/ceditview-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)
