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
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420607"
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
|[CDocTemplate：： CDocTemplate](#cdoctemplate)|建構 `CDocTemplate` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocTemplate：： AddDocument](#adddocument)|將檔新增至範本。|
|[CDocTemplate：： CloseAllDocuments](#closealldocuments)|關閉所有與此範本相關聯的檔。|
|[CDocTemplate：： CreateNewDocument](#createnewdocument)|建立新檔。|
|[CDocTemplate：： CreateNewFrame](#createnewframe)|建立包含檔和視圖的新框架視窗。|
|[CDocTemplate：： CreateOleFrame](#createoleframe)|建立啟用 OLE 的框架視窗。|
|[CDocTemplate：： CreatePreviewFrame](#createpreviewframe)|建立用於豐富預覽的子框架。|
|[CDocTemplate：： GetDocString](#getdocstring)|抓取與檔案類型相關聯的字串。|
|[CDocTemplate：： GetFirstDocPosition](#getfirstdocposition)|抓取與此範本相關聯之第一個檔的位置。|
|[CDocTemplate：： GetNextDoc](#getnextdoc)|抓取檔和下一個檔的位置。|
|[CDocTemplate：： InitialUpdateFrame](#initialupdateframe)|初始化框架視窗，並選擇性地使其可見。|
|[CDocTemplate：： LoadTemplate](#loadtemplate)|載入指定 `CDocTemplate` 或衍生類別的資源。|
|[CDocTemplate：： MatchDocType](#matchdoctype)|決定檔案類型與這個範本之間的信心程度。|
|[CDocTemplate：： OpenDocumentFile](#opendocumentfile)|開啟路徑名稱所指定的檔案。|
|[CDocTemplate：： RemoveDocument](#removedocument)|從範本中移除檔。|
|[CDocTemplate：： SaveAllModified](#saveallmodified)|儲存與此範本相關聯且已修改的所有檔。|
|[CDocTemplate：： SetContainerInfo](#setcontainerinfo)|當編輯就地 OLE 專案時，決定 OLE 容器的資源。|
|[CDocTemplate：： SetDefaultTitle](#setdefaulttitle)|在文件視窗的標題列中顯示預設標題。|
|[CDocTemplate：： SetPreviewInfo](#setpreviewinfo)|已從進程預覽處理常式中進行。|
|[CDocTemplate：： SetServerInfo](#setserverinfo)|決定就地內嵌或編輯服務器檔時的資源和類別。|

## <a name="remarks"></a>備註

您通常會在應用程式的 `InitInstance` 功能的執行中建立一或多個檔範本。 檔範本會定義三種類別類型之間的關聯性：

- 您從 `CDocument`衍生的檔類別。

- View 類別，它會顯示上列檔類別中所列的資料。 您可以從 `CView`、`CScrollView`、`CFormView`或 `CEditView`衍生這個類別。 （您也可以直接使用 `CEditView`）。

- 包含視圖的框架視窗類別。 針對單一檔介面（SDI）應用程式，您可以從 `CFrameWnd`衍生這個類別。 針對多重文件介面（MDI）應用程式，您可以從 `CMDIChildWnd`衍生這個類別。 如果您不需要自訂框架視窗的行為，您可以直接使用 `CFrameWnd` 或 `CMDIChildWnd`，而不會衍生您自己的類別。

您的應用程式針對其支援的每一種檔案類型，都有一個檔範本。 例如，如果您的應用程式同時支援試算表和文字檔，則應用程式會有兩個檔範本物件。 每個檔範本都會負責建立及管理其類型的所有檔。

檔範本會儲存檔、視圖和框架視窗類別之 `CRuntimeClass` 物件的指標。 這些 `CRuntimeClass` 物件是在建立檔範本時指定的。

檔範本包含與檔案類型搭配使用之資源的識別碼（例如功能表、圖示或快速鍵對應表資源）。 檔範本也有字串，其中包含其檔案類型的其他相關資訊。 這些包括檔案類型的名稱（例如，"工作表"）和副檔名（例如 ".xls"）。 （選擇性）它可以包含應用程式的使用者介面、Windows 檔案管理員，以及物件連結和內嵌（OLE）支援所使用的其他字串。

如果您的應用程式是 OLE 容器和/或伺服器，檔範本也會定義就地啟用期間所使用之功能表的識別碼。 如果您的應用程式是 OLE 伺服器，則檔範本會定義在就地啟用期間所使用的工具列和功能表的識別碼。 您可以藉由呼叫 `SetContainerInfo` 和 `SetServerInfo`來指定這些額外的 OLE 資源。

因為 `CDocTemplate` 是抽象類別，所以您無法直接使用類別。 一般應用程式會使用 MFC 程式庫所提供的兩個 `CDocTemplate`衍生類別之一： `CSingleDocTemplate`，它會實行 SDI，而 `CMultiDocTemplate`則會執行 MDI。 如需使用檔範本的詳細資訊，請參閱這些類別。

如果您的應用程式需要的使用者介面範例基本上與 SDI 或 MDI 不同，您可以從 `CDocTemplate`衍生自己的類別。

如需 `CDocTemplate`的詳細資訊，請參閱[檔範本和檔/視圖建立](../../mfc/document-templates-and-the-document-view-creation-process.md)程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="adddocument"></a>CDocTemplate：： AddDocument

使用此函式將檔新增至範本。

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
要加入之檔的指標。

### <a name="remarks"></a>備註

衍生類別[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)和[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)會覆寫這個函式。 如果您從 `CDocTemplate`衍生自己的檔範本類別，則您的衍生類別必須覆寫此函數。

##  <a name="cdoctemplate"></a>CDocTemplate：： CDocTemplate

建構 `CDocTemplate` 物件。

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
指定與檔案類型搭配使用之資源的識別碼。 這可能包括功能表、圖示、快速鍵對應表和字串資源。

字串資源包含最多七個以 ' \n ' 字元分隔的子字串（如果未包含子字串，則需要 ' \n ' 字元做為預留位置，但不需要尾端 ' \n ' 字元）;這些子字串描述檔案類型。 如需子字串的詳細資訊，請參閱[GetDocString](#getdocstring)。 這個字串資源會在應用程式的資源檔中找到。 例如，

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

請注意，字串開頭為 ' \n ' 字元;這是因為第一個子字串不會用於 MDI 應用程式，因此不會包含在內。 您可以使用 [字串編輯器] 來編輯此字串;整個字串在字串編輯器中會顯示為單一專案，而不是七個不同的專案。

*pDocClass*<br/>
指向 document 類別的 `CRuntimeClass` 物件。 這個類別是您定義的 `CDocument`衍生類別，可代表您的檔。

*pFrameClass*<br/>
指向框架視窗類別的 `CRuntimeClass` 物件。 這個類別可以是 `CFrameWnd`衍生的類別，如果您想要主框架視窗的預設行為，則可以 `CFrameWnd` 本身。

*pViewClass*<br/>
指向 view 類別的 `CRuntimeClass` 物件。 這個類別是您定義用來顯示檔的 `CView`衍生類別。

### <a name="remarks"></a>備註

使用此成員函式來建立 `CDocTemplate` 物件。 以動態方式配置 `CDocTemplate` 物件，並從應用程式類別的 `InitInstance` 成員函式將它傳遞至[CWinApp：： AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) 。

##  <a name="closealldocuments"></a>CDocTemplate：： CloseAllDocuments

呼叫這個成員函式以關閉所有開啟的檔。

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>參數

*bEndSession*<br/>
未使用。

### <a name="remarks"></a>備註

這個成員函式通常用來做為 File Exit 命令的一部分。 此函式的預設執行會呼叫[CDocument：:D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents)成員函式來刪除檔的資料，然後關閉附加至檔之所有視圖的框架視窗。

如果您想要要求使用者在關閉檔之前執行特殊清除處理，請覆寫此函數。 例如，如果檔代表資料庫中的記錄，您可能會想要覆寫此函數來關閉資料庫。

##  <a name="createnewdocument"></a>CDocTemplate：： CreateNewDocument

呼叫這個成員函式，以建立與此檔範本相關聯之類型的新檔。

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>傳回值

新建立之檔的指標，如果發生錯誤，則為 Null。

##  <a name="createnewframe"></a>CDocTemplate：： CreateNewFrame

建立包含檔和視圖的新框架視窗。

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
新框架視窗應該參考的檔。 可以是 NULL。

*pOther*<br/>
新框架視窗要根據的框架視窗。 可以是 NULL。

### <a name="return-value"></a>傳回值

新建立之框架視窗的指標，如果發生錯誤，則為 Null。

### <a name="remarks"></a>備註

`CreateNewFrame` 使用傳遞至此函式的 `CRuntimeClass` 物件，來建立已附加視圖和檔的新框架視窗。 如果*pDoc*參數為 Null，則架構會輸出追蹤訊息。

*POther*參數是用來執行 Window New 命令。 它會提供框架視窗，以建立新框架視窗的模型。 新的框架視窗通常會建立為不可見。 呼叫此函式可在「檔案新增」和「開啟檔案」的標準架構執行以外建立框架視窗。

##  <a name="createoleframe"></a>CDocTemplate：： CreateOleFrame

建立 OLE 框架視窗。

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
框架父視窗的指標。

*pDoc*<br/>
新的 OLE 框架視窗應參考之檔的指標。

*bCreateView*<br/>
決定是否要與框架一併建立一個視圖。

### <a name="return-value"></a>傳回值

如果成功，則為框架視窗的指標;否則為 Null。

### <a name="remarks"></a>備註

如果*bCreateView*為零，則會建立空的框架。

##  <a name="getdocstring"></a>CDocTemplate：： GetDocString

抓取與檔案類型相關聯的字串。

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>參數

*rString*<br/>
當函式傳回時，將包含字串之 `CString` 物件的參考。

*index*<br/>
從描述檔案類型的字串中，所抓取之子字串的索引。 這個參數的值可以是下列其中一個：

- 出現在應用程式視窗標題列中 `CDocTemplate::windowTitle` 名稱（例如「Microsoft Excel」）。 只存在於 SDI 應用程式的檔範本中。

- `CDocTemplate::docName` 預設檔案名稱的根目錄（例如「工作表」）。 當使用者從 [檔案] 功能表選擇新的命令時（例如，"Sheet1" 或 "Sheet2"），這個根和一個數位就會用來做為此類型之新檔的預設名稱。 如果未指定，則會使用「未命名」做為預設值。

- `CDocTemplate::fileNewName` 此檔案類型的名稱。 如果應用程式支援一種以上的檔案類型，這個字串會顯示在 [檔案] [新增] 對話方塊中（例如，"工作表"）。 如果未指定，則會使用 [檔案] [新增] 命令來無法存取檔案類型。

- `CDocTemplate::filterName` 檔案類型的描述，以及符合此類型檔的萬用字元篩選準則。 這個字串會顯示在 [開啟檔案] 對話方塊中的 [清單檔案類型] 下拉式清單中（例如，「工作表（* .xls）」）。 如果未指定，則會使用 [檔案開啟] 命令來無法存取檔案類型。

- 此類型檔的 `CDocTemplate::filterExt` 延伸模組（例如 ".xls"）。 如果未指定，則會使用 [檔案開啟] 命令來無法存取檔案類型。

- 要儲存在 Windows 維護的註冊資料庫中的檔案類型 `CDocTemplate::regFileTypeId` 識別碼。 這個字串僅供內部使用（例如，"ExcelWorksheet"）。 如果未指定，則無法向 Windows 檔案管理員註冊檔案類型。

- 要儲存在註冊資料庫中的檔案類型 `CDocTemplate::regFileTypeName` 名稱。 這個字串可能會顯示在存取註冊資料庫之應用程式的對話方塊中（例如「Microsoft Excel 工作表」）。

### <a name="return-value"></a>傳回值

如果找到指定的子字串，則為非零值;否則為0。

### <a name="remarks"></a>備註

呼叫此函式可抓取描述檔案類型的特定子字串。 包含這些子字串的字串會儲存在檔範本中，並且衍生自應用程式資源檔中的字串。 架構會呼叫這個函式，以取得應用程式使用者介面所需的字串。 如果您已為應用程式的檔指定副檔名，則在將專案新增至 Windows 註冊資料庫時，架構也會呼叫這個函式。這可讓您從 Windows 檔案管理員開啟檔。

只有當您從 `CDocTemplate`衍生您自己的類別時，才能呼叫此函式。

##  <a name="getfirstdocposition"></a>CDocTemplate：： GetFirstDocPosition

抓取與此範本相關聯之第一個檔的位置。

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>傳回值

可以用來逐一查看與此檔範本相關聯之檔案清單的位置值;如果清單是空的，則為 Null。

### <a name="remarks"></a>備註

使用此函式可取得與此範本相關聯的檔案清單中第一份檔的位置。 使用 POSITION 值做為[CDocTemplate：： GetNextDoc](#getnextdoc)的引數，以逐一查看與範本相關聯的檔案清單。

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)和[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)都會覆寫這個純虛擬函式。 您從 `CDocTemplate` 衍生的任何類別也必須覆寫此函數。

##  <a name="getnextdoc"></a>CDocTemplate：： GetNextDoc

抓取*rpo*所識別的清單元素，然後將*rpo*設定為清單中下一個專案的位置值。

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>傳回值

與此範本相關聯的檔案清單中，下一個檔的指標。

### <a name="parameters"></a>參數

*Rpo*<br/>
先前呼叫[GetFirstDocPosition](#getfirstdocposition)或 `GetNextDoc`所傳回之位置值的參考。

### <a name="remarks"></a>備註

如果所抓取的專案是清單中的最後一個專案，則會將新的*rpo*值設定為 Null。

如果您使用[GetFirstDocPosition](#getfirstdocposition)的呼叫來建立初始位置，可以在正向反復專案迴圈中使用 `GetNextDoc`。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

##  <a name="initialupdateframe"></a>CDocTemplate：： InitialUpdateFrame

初始化框架視窗，並選擇性地使其可見。

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>參數

*pFrame*<br/>
需要初始更新的框架視窗。

*pDoc*<br/>
與框架相關聯的檔。 可以是 NULL。

*bMakeVisible*<br/>
指出畫面格是否應為可見且作用中。

### <a name="remarks"></a>備註

在建立具有 `CreateNewFrame`的新框架之後，呼叫 `IntitialUpdateFrame`。 呼叫此函式會導致該框架視窗中的 views 接收其 `OnInitialUpdate` 呼叫。 此外，如果先前沒有使用中的視圖，框架視窗的主要視圖會成為作用中;主要視圖是 AFX_IDW_PANE_FIRST 的子系識別碼的視圖。 最後，如果*bMakeVisible*為非零，則會顯示框架視窗。 如果*bMakeVisible*為零，則框架視窗目前的焦點和可見狀態會保持不變。

使用架構的「檔案新增」和「開啟檔案」的執行時，不需要呼叫此函式。

##  <a name="loadtemplate"></a>CDocTemplate：： LoadTemplate

載入指定 `CDocTemplate` 或衍生類別的資源。

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>備註

此成員函式會由架構呼叫，以載入指定 `CDocTemplate` 或衍生類別的資源。 通常在結構中會呼叫它，但在全域建立範本時除外。 在這種情況下，`LoadTemplate` 的呼叫會延遲到呼叫[CWinApp：： AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)為止。

##  <a name="matchdoctype"></a>CDocTemplate：： MatchDocType

決定檔案類型與這個範本之間的信心程度。

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
要判斷其型別之檔案的路徑名稱。

*rpDocMatch*<br/>
如果已開啟*lpszPathName*所指定的檔案，則為已指派比對檔之檔的指標。

### <a name="return-value"></a>傳回值

**信賴**型列舉中的值，定義如下：

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

使用此函式來判斷用來開啟檔案的檔範本類型。 例如，如果您的應用程式支援多個檔案類型，您可以使用此函式來判斷哪一個可用的檔範本適用于指定的檔案，方法是依序呼叫每個範本的 `MatchDocType`，並根據傳回的信賴值來選擇範本。

如果*lpszPathName*所指定的檔案已經開啟，此函式會傳回 `CDocTemplate::yesAlreadyOpen` 並將檔案的 `CDocument` 物件複製到物件中的*rpDocMatch*。

如果檔案未開啟，但*lpszPathName*中的副檔名符合 `CDocTemplate::filterExt`所指定的副檔名，則此函式會傳回 `CDocTemplate::yesAttemptNative`，並將*RPDOCMATCH*設定為 Null。 如需 `CDocTemplate::filterExt`的詳細資訊，請參閱[CDocTemplate：： GetDocString](#getdocstring)。

如果這兩種情況都不成立，函數會傳回 `CDocTemplate::yesAttemptForeign`。

預設的執行不會傳回 `CDocTemplate::maybeAttemptForeign` 或 `CDocTemplate::maybeAttemptNative`。 覆寫此函式，以實作用於應用程式的類型比對邏輯，也許是從**信賴**型列舉中使用這兩個值。

##  <a name="opendocumentfile"></a>CDocTemplate：： OpenDocumentFile

開啟路徑所指定的檔案。

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
在檔案路徑的指標，該檔案包含要開啟的檔。

*bAddToMRU*<br/>
在TRUE 表示檔是最新的其中一個檔案;FALSE 表示檔不是其中一個最新的檔案。

### <a name="return-value"></a>傳回值

檔的指標，其檔案是由*lpszPathName*命名;如果失敗，則為 Null。

### <a name="remarks"></a>備註

開啟其路徑是由*lpszPathName*指定的檔案。 如果*lpszPathName*為 Null，則會建立新的檔案，其中包含與此範本相關聯之類型的檔。

##  <a name="removedocument"></a>CDocTemplate：： RemoveDocument

從與此範本相關聯的檔案清單中，移除*pDoc*所指向的檔。

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
要移除之檔的指標。

### <a name="remarks"></a>備註

衍生的類別 `CMultiDocTemplate` 和 `CSingleDocTemplate` 覆寫此函式。 如果您從 `CDocTemplate`衍生自己的檔範本類別，則您的衍生類別必須覆寫此函數。

##  <a name="saveallmodified"></a>CDocTemplate：： SaveAllModified

儲存所有已修改的檔。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>傳回值

如果成功，則為非零;否則為0。

##  <a name="setcontainerinfo"></a>CDocTemplate：： SetContainerInfo

當編輯就地 OLE 專案時，決定 OLE 容器的資源。

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>參數

*nIDOleInPlaceContainer*<br/>
啟用内嵌物件時所使用的資源識別碼。

### <a name="remarks"></a>備註

呼叫此函式可設定就地啟用 OLE 物件時所要使用的資源。 這些資源可能包含功能表和快速鍵對應表。 此函式通常會在應用程式的[CWinApp：： InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)函式中呼叫。

與*nIDOleInPlaceContainer*相關聯的功能表包含分隔符號，可讓啟用的就地專案的功能表與容器應用程式的功能表合併。 如需有關合併伺服器和容器功能表的詳細資訊，請參閱文章[功能表和資源（OLE）](../../mfc/menus-and-resources-ole.md)。

##  <a name="setdefaulttitle"></a>CDocTemplate：： SetDefaultTitle

呼叫此函式可載入檔的預設標題，並將其顯示在檔的標題列中。

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>參數

*pDocument*<br/>
要設定其標題之檔的指標。

### <a name="remarks"></a>備註

如需預設標題的詳細資訊，請參閱[CDocTemplate：： GetDocString](#getdocstring)中的 `CDocTemplate::docName` 描述。

##  <a name="setserverinfo"></a>CDocTemplate：： SetServerInfo

決定就地內嵌或編輯服務器檔時的資源和類別。

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>參數

*nIDOleEmbedding*<br/>
在個別視窗中開啟内嵌物件時所使用的資源識別碼。

*nIDOleInPlaceServer*<br/>
就地啟用内嵌物件時所使用的資源識別碼。

*pOleFrameClass*<br/>
[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)結構的指標，其中包含就地啟用時所建立之框架視窗物件的類別資訊。

*pOleViewClass*<br/>
`CRuntimeClass` 結構的指標，其中包含就地啟用時所建立之 view 物件的類別資訊。

### <a name="remarks"></a>備註

呼叫這個成員函式，以識別當使用者要求啟用内嵌物件時，伺服器應用程式將使用的資源。 這些資源是由功能表和快速鍵對應表所組成。 此函式通常會在應用程式的 `InitInstance` 中呼叫。

與*nIDOleInPlaceServer*相關聯的功能表包含分隔符號，可讓 [伺服器] 功能表與容器的功能表合併。 如需有關合併伺服器和容器功能表的詳細資訊，請參閱文章[功能表和資源（OLE）](../../mfc/menus-and-resources-ole.md)。

##  <a name="createpreviewframe"></a>CDocTemplate：： CreatePreviewFrame

建立用於豐富預覽的子框架。

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
父視窗的指標（通常是由 Shell 所提供）。

*pDoc*<br/>
檔物件的指標，其內容將會預覽。

### <a name="return-value"></a>傳回值

`CFrameWnd` 物件的有效指標，如果建立失敗，則為 Null。

### <a name="remarks"></a>備註

##  <a name="setpreviewinfo"></a>CDocTemplate：： SetPreviewInfo

設定進程外預覽處理常式。

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>參數

*nIDPreviewFrame*<br/>
指定預覽框架的資源識別碼。

*pPreviewFrameClass*<br/>
指定預覽框架的執行時間類別資訊結構的指標。

*pPreviewViewClass*<br/>
指定預覽視圖的執行時間類別資訊結構的指標。

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
