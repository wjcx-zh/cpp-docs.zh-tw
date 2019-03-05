---
title: CMultiDocTemplate 類別
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 5fefe91fa2067831c0263146ff3b2cd143b9c647
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284251"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 類別

定義實作多重文件介面 (MDI) 的文件範本。

## <a name="syntax"></a>語法

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|建構 `CMultiDocTemplate` 物件。|

## <a name="remarks"></a>備註

MDI 應用程式會做使用者可以在其中開啟零或多個文件框架視窗，其中每個文件顯示的工作區中的主框架視窗。 MDI 更詳細的描述，請參閱 <<c0>  *軟體設計的 Windows 介面指導方針*。

文件範本會定義三種類型的類別之間的關聯性：

- 文件類別，衍生自[CDocument](../../mfc/reference/cdocument-class.md)。

- 檢視類別，會顯示上面所列的文件類別的資料。 您可以衍生此類別[CView](../../mfc/reference/cview-class.md)， `CScrollView`， `CFormView`，或`CEditView`。 (您也可以使用`CEditView`直接。)

- 框架視窗類別，其中包含檢視。 MDI 文件範本，您可以衍生此類別`CMDIChildWnd`，或者，如果您不需要自訂文件框架視窗的行為，您可以使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)直接而不需衍生您自己的類別。

MDI 應用程式可支援多個文件、 類型和不同類型的文件可以同時開啟。 您的應用程式有一個用於支援每個文件類型的文件範本。 例如，如果您的 MDI 應用程式支援試算表和文字文件，應用程式有兩個`CMultiDocTemplate`物件。

在使用者建立新的文件時，應用程式會使用文件範本。 如果應用程式支援多個類型的文件，架構會從 文件範本取得支援的文件類型的名稱，並顯示在 開新檔案 對話方塊中的清單。 一旦使用者選取文件類型，應用程式會建立文件類別物件、 框架視窗物件，以及檢視物件，並將其附加到彼此。

您不需要呼叫任何成員函式`CMultiDocTemplate`除了建構函式。 此架構會處理`CMultiDocTemplate`內部物件。

如需詳細資訊`CMultiDocTemplate`，請參閱 <<c2> [ 文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate

建構 `CMultiDocTemplate` 物件。

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
指定文件類型所使用的資源的識別碼。 這可能包括功能表、 圖示、 快速鍵對應表和字串資源。

最多七個以 '\n' 字元分隔的子字串所組成的字串資源 （不包含子字串時，需要 '\n' 字元做為預留位置; 不過，不需要尾端的 '\n' 字元;）這些子字串會描述文件類型。 如需子字串的資訊，請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 應用程式的資源檔中找到此字串資源。 例如: 

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

請注意，字串開頭 '\n' 字元;這是因為第一個子字串不能用於 MDI 應用程式，因此就不會包含。 您可以編輯這個字串使用字串編輯器;整個字串會顯示為單一項目在字串編輯器中中,，不為七個不同的項目。

如需這些資源類型的詳細資訊，請參閱[資源編輯器](../../windows/resource-editors.md)。

*pDocClass*<br/>
指向`CRuntimeClass`文件類別的物件。 這個類別是`CDocument`-衍生的類別定義以代表您的文件。

*pFrameClass*<br/>
指向`CRuntimeClass`框架視窗類別的物件。 這個類別可以`CMDIChildWnd`-衍生的類別，或者它可以是`CMDIChildWnd`本身如果您想要為您的文件框架視窗的預設行為。

*pViewClass*<br/>
指向`CRuntimeClass`檢視類別的物件。 這個類別是`CView`-衍生的類別，您會定義顯示您的文件。

### <a name="remarks"></a>備註

以動態方式配置一個`CMultiDocTemplate`物件的每個文件類型支援您的應用程式，並傳遞至每個`CWinApp::AddDocTemplate`從`InitInstance`應用程式類別的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

以下是第二個範例。

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate 類別](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)
