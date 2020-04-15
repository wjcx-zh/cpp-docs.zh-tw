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
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318352"
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
|[CSingleDoc 範本:C單文件範本](#csingledoctemplate)|建構 `CSingleDocTemplate` 物件。|

## <a name="remarks"></a>備註

SDI 應用程式使用主框架視窗來顯示文檔;一次只能打開一個文檔。

文件樣本定義三種類型的類之間的關係:

- 從 派生的`CDocument`文檔類。

- 視圖類,它顯示來自上面列出的文檔類的數據。 可以從`CView`派生此類`CScrollView`,`CFormView``CEditView`或 。 ( 您也可以直接`CEditView`使用 。

- 包含檢視的框架視窗類。 對於 SDI 文件範本,可以從`CFrameWnd`派生 此類。如果不需要自定義主框架視窗的行為,則可以直接使用`CFrameWnd`,而無需派生自己的類。

SDI 應用程式通常支援一種類型的文檔,因此它只有`CSingleDocTemplate`一個 物件。 一次只能打開一個文檔。

除了構造函數之外,您不需要調用 的`CSingleDocTemplate`任何成員函數。 框架在內部`CSingleDocTemplate`處理物件。

有關`CSingleDocTemplate`使用的詳細資訊,請參考[文件樣本與文件/檢視建立過程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDoc 範本:C單文件範本

建構 `CSingleDocTemplate` 物件。

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nID資源*<br/>
指定與文件類型一起使用的資源的識別碼。 這可能包括功能表、圖示、快速鍵表和字串資源。

字串資源由最多七個子字串組成,由"\n"字元分隔(如果未包含子字串,則需要"\n"字元作為佔位元;但是,尾隨的"\n"字元是不需要的);這些子字串描述文件類型。 有關子字串的資訊,請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 此字串資源位於應用程式的資源檔中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

您可以使用字串編輯器編輯此字串;但是,使用字串編輯器可以編輯此字串。整個字串在字串編輯器中顯示為單個條目,而不是七個單獨的條目。

關於這些資源型態的詳細資訊,請參考[字串編輯器](../../windows/string-editor.md)。

*pDocClass*<br/>
指向文檔`CRuntimeClass`類的物件。 此類是您定義的`CDocument`表示文檔的派生類。

*pFrame 類別*<br/>
指向框架視窗`CRuntimeClass`類的物件。 類可以是`CFrameWnd`派生類,也可以`CFrameWnd`是自己的,如果您想要主框架視窗的默認行為。

*pView 類別*<br/>
指向視圖類`CRuntimeClass`的物件。 此類是您為`CView`顯示文檔而定義的派生類。

### <a name="remarks"></a>備註

動態分配`CSingleDocTemplate`物件,並將`CWinApp::AddDocTemplate`其 從`InitInstance`應用程式類的成員函數傳遞給物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品對接](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate 類別](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)
