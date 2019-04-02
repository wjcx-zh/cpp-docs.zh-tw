---
title: CSingleDocTemplate 類別
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 4d1361734f38d903e2171839b95888863126974a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771693"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate 類別

定義實作單一文件介面 (SDI) 的文件範本。

## <a name="syntax"></a>語法

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|建構 `CSingleDocTemplate` 物件。|

## <a name="remarks"></a>備註

SDI 應用程式使用的主框架視窗來顯示文件只有一次可以開啟一份文件。

文件範本會定義三種類型的類別之間的關聯性：

- 文件類別，衍生自`CDocument`。

- 檢視類別，會顯示上面所列的文件類別的資料。 您可以衍生此類別`CView`， `CScrollView`， `CFormView`，或`CEditView`。 (您也可以使用`CEditView`直接。)

- 框架視窗類別，其中包含檢視。 為 SDI 文件範本，您可以衍生此類別`CFrameWnd`; 如果您不需要自訂行為的主框架視窗中，您可以使用`CFrameWnd`直接而不需衍生您自己的類別。

SDI 應用程式通常支援一種類型的文件，因此只有一個`CSingleDocTemplate`物件。 只有一次可以開啟一份文件。

您不需要呼叫任何成員函式`CSingleDocTemplate`除了建構函式。 此架構會處理`CSingleDocTemplate`內部物件。

如需有關使用`CSingleDocTemplate`，請參閱 <<c2> [ 文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate

建構 `CSingleDocTemplate` 物件。

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nIDResource*<br/>
指定文件類型所使用的資源的識別碼。 這可能包括功能表、 圖示、 快速鍵對應表和字串資源。

最多七個以 '\n' 字元分隔的子字串所組成的字串資源 （不包含子字串時，需要 '\n' 字元做為預留位置; 不過，不需要尾端的 '\n' 字元;）這些子字串會描述文件類型。 子字串的相關資訊，請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 應用程式的資源檔中找到此字串資源。 例如: 

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

您可以編輯這個字串使用字串編輯器;整個字串會顯示為單一項目在字串編輯器中中,，不為七個不同的項目。

如需這些資源類型的詳細資訊，請參閱[字串值編輯器](../../windows/string-editor.md)。

*pDocClass*<br/>
指向`CRuntimeClass`文件類別的物件。 這個類別是`CDocument`-衍生的類別定義以代表您的文件。

*pFrameClass*<br/>
指向`CRuntimeClass`框架視窗類別的物件。 這個類別可以`CFrameWnd`-衍生的類別，或者它可以是`CFrameWnd`本身如果您想要為您的主框架視窗的預設行為。

*pViewClass*<br/>
指向`CRuntimeClass`檢視類別的物件。 這個類別是`CView`-衍生的類別，您會定義顯示您的文件。

### <a name="remarks"></a>備註

以動態方式配置`CSingleDocTemplate`物件，並將它傳遞給`CWinApp::AddDocTemplate`從`InitInstance`應用程式類別的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate 類別](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)
