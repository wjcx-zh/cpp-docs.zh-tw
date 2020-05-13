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
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319736"
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
|[C 多文件樣本:C 多文件樣本](#cmultidoctemplate)|建構 `CMultiDocTemplate` 物件。|

## <a name="remarks"></a>備註

MDI 應用程式使用主框架視窗作為工作區,用戶可以在其中打開零個或多個文檔框架視窗,每個視窗都顯示一個文檔。 有關 MDI 的詳細說明,請參閱*軟體設計的 Windows 介面指南*。

文件樣本定義三種類型的類之間的關係:

- 從[CDocument](../../mfc/reference/cdocument-class.md)派生的文件類。

- 視圖類,它顯示來自上面列出的文檔類的數據。 可以從[CView](../../mfc/reference/cview-class.md)`CScrollView`的不`CFormView`用`CEditView`, 或 。 ( 您也可以直接`CEditView`使用 。

- 包含檢視的框架視窗類。 對於 MDI 文件範本,可以從`CMDIChildWnd`派生此類 ,或者,如果您不需要自定義文檔框架視窗的行為,則可以直接使用[CMDIChildWnd,](../../mfc/reference/cmdichildwnd-class.md)而無需派生自己的類。

MDI 應用程式可以支援多種類型的文件,並且不同類型的文檔可以同時打開。 應用程式對於它支援的每個文件類型都有一個文檔範本。 例如,如果您的 MDI 應用程式同時支援電子表格和文本文件,則應用程式`CMultiDocTemplate`有兩 個物件。

當使用者創建新文檔時,應用程式將使用文檔範本。 如果應用程式支援多種類型的文件,則框架將從文檔範本中取得受支援的文件類型的名稱,並在「檔案新建」對話框中的清單中顯示它們。 使用者選擇文件類型後,應用程式將創建文檔類物件、框架視窗物件和檢視物件,並將其附加到彼此。

除了構造函數之外,您不需要調用 的`CMultiDocTemplate`任何成員函數。 框架在內部`CMultiDocTemplate`處理物件。

有關的詳細資訊`CMultiDocTemplate`,請參考[文件樣本與文件/檢視建立過程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>C 多文件樣本:C 多文件樣本

建構 `CMultiDocTemplate` 物件。

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>參數

*nID資源*<br/>
指定與文件類型一起使用的資源的識別碼。 這可能包括功能表、圖示、快速鍵表和字串資源。

字串資源由最多七個子字串組成,由"\n"字元分隔(如果不包括子字串,則需要"\n"字元作為佔位元;但是,尾隨的"\n"字元是不需要的);這些子字串描述文件類型。 有關子字串的資訊,請參閱[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 此字串資源位於應用程式的資源檔中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

請注意,字串以「\n」字元開頭;這是因為第一個子字串不用於 MDI 應用程式,因此不包括。 您可以使用字串編輯器編輯此字串;但是,使用字串編輯器可以編輯此字串。整個字串在字串編輯器中顯示為單個條目,而不是七個單獨的條目。

關於這些資源類型的詳細資訊,請參考[資源編輯器](../../windows/resource-editors.md)。

*pDocClass*<br/>
指向文檔`CRuntimeClass`類的物件。 此類是您定義的`CDocument`表示文檔的派生類。

*pFrame 類別*<br/>
指向框架視窗`CRuntimeClass`類的物件。 此類可以是`CMDIChildWnd`派生類,也可以`CMDIChildWnd`是 自己的類,如果希望文檔框架視窗的默認行為。

*pView 類別*<br/>
指向視圖類`CRuntimeClass`的物件。 此類是您為`CView`顯示文檔而定義的派生類。

### <a name="remarks"></a>備註

為應用程式支援的每個`CMultiDocTemplate`文件類型動態分配一個物件,並將每個`CWinApp::AddDocTemplate`物件 從`InitInstance`應用程式類的成員函數傳遞給。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

下面是第二個示例。

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate 類別](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)
