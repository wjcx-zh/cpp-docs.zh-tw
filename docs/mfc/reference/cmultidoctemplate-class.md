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
ms.openlocfilehash: af950d188c4e02a38a39ed3c672f0f8c4161bee8
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737488"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 類別

定義實作多重文件介面 (MDI) 的文件範本。

## <a name="syntax"></a>語法

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>成員

這個類別的成員函式是虛擬的。 如需相關檔，請參閱[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)和[CCmdTarget](../../mfc/reference/ccmdtarget-class.md) 。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMultiDocTemplate：： CMultiDocTemplate](#cmultidoctemplate)|建構 `CMultiDocTemplate` 物件。|

## <a name="remarks"></a>備註

MDI 應用程式會使用主框架視窗做為工作區，使用者可以在其中開啟零或多個檔框架視窗，其中每個都顯示一份檔。 如需 MDI 的詳細說明，請參閱*軟體設計的 Windows 介面方針*。

檔範本會定義三種類別類型之間的關聯性：

- 您從[CDocument](../../mfc/reference/cdocument-class.md)衍生的檔類別。

- View 類別，它會顯示上列檔類別中所列的資料。 您可以從[CView](../../mfc/reference/cview-class.md)、、或衍生這個類別 `CScrollView` `CFormView` `CEditView` 。 （您也可以 `CEditView` 直接使用）。

- 包含視圖的框架視窗類別。 針對 MDI 檔範本，您可以從衍生這個類別 `CMDIChildWnd` ，或者，如果您不需要自訂檔框架視窗的行為，您可以直接使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) ，而不需衍生您自己的類別。

MDI 應用程式可以支援一種以上的檔案類型，而且可以同時開啟不同類型的檔。 您的應用程式針對其支援的每種檔案類型，都有一個檔範本。 例如，如果您的 MDI 應用程式同時支援試算表和文字檔，則應用程式會有兩個 `CMultiDocTemplate` 物件。

當使用者建立新檔時，應用程式會使用檔範本。 如果應用程式支援一種以上的檔案類型，則架構會從檔範本中取得支援之檔案類型的名稱，並將其顯示在 [新增檔案] 對話方塊的清單中。 當使用者選取檔案類型之後，應用程式會建立檔類別物件、框架視窗物件和 view 物件，並將它們附加至彼此。

除了函式之外，您不需要呼叫任何成員函式 `CMultiDocTemplate` 。 架構會 `CMultiDocTemplate` 在內部處理物件。

如需有關的詳細資訊 `CMultiDocTemplate` ，請參閱[檔範本和檔/視圖建立](../../mfc/document-templates-and-the-document-view-creation-process.md)程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate：： CMultiDocTemplate

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
指定與檔案類型搭配使用之資源的識別碼。 這可能包括功能表、圖示、快速鍵對應表和字串資源。

字串資源包含最多七個以 ' \n ' 字元分隔的子字串（如果不包含子字串，則需要 ' \n ' 字元做為預留位置，但不需要尾端 ' \n ' 字元）;這些子字串描述檔案類型。 如需子字串的詳細資訊，請參閱[CDocTemplate：： GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 這個字串資源會在應用程式的資源檔中找到。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

字串的開頭為 ' \n ' 字元，因為第一個子字串不會用於 MDI 應用程式，因此不會包含。 您可以使用 [字串編輯器] 來編輯此字串;整個字串在字串編輯器中會顯示為單一專案，而不是七個不同的專案。

如需這些資源類型的詳細資訊，請參閱[資源編輯器](../../windows/resource-editors.md)。

*pDocClass*<br/>
指向 `CRuntimeClass` document 類別的物件。 這個類別是 `CDocument` 您定義來代表您的檔的衍生類別。

*pFrameClass*<br/>
指向 `CRuntimeClass` 框架視窗類別的物件。 這個類別可以是 `CMDIChildWnd` 衍生類別， `CMDIChildWnd` 如果您想要檔框架視窗的預設行為，它可以是本身。

*pViewClass*<br/>
指向 `CRuntimeClass` view 類別的物件。 這個類別是 `CView` 您定義用來顯示檔的衍生類別。

### <a name="remarks"></a>備註

`CMultiDocTemplate`針對您的應用程式支援的每種檔案類型，動態配置一個物件，並 `CWinApp::AddDocTemplate` 從 `InitInstance` 應用程式類別的成員函式將每個物件傳遞給。

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
