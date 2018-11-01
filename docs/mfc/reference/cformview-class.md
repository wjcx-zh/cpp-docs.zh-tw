---
title: CFormView 類別
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 37ae7ca2efeb579cba388e22cf0fe450a068e721
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651954"
---
# <a name="cformview-class"></a>CFormView 類別

用於表單檢視的基底類別。

## <a name="syntax"></a>語法

```
class CFormView : public CScrollView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|建構 `CFormView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用於初始化期間同步處理。|

## <a name="remarks"></a>備註

表單檢視基本上是包含控制項的檢視。 這些控制項根據對話方塊範本資源而佈置。 如果您想要應用程式中有表單，請使用 `CFormView`。 這些檢視支援捲動，如有需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能。

當您準備[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)，您可以根據其檢視類別`CFormView`，讓表單為基礎的應用程式。

您也可以新增插入[表單主題](../../mfc/form-views-mfc.md)到文件檢視架構的應用程式。 即使您的應用程式一開始不支援表單，Visual C++ 也會在您插入新表單時加入這項支援。

MFC 應用程式精靈和 [加入類別] 命令是建立表單架構應用程式的慣用方法。 如果您需要建立表單架構應用程式，而不需使用這些方法，請參閱[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

建構 `CFormView` 物件。

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含以 null 結束的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

### <a name="remarks"></a>備註

當您建立的物件型別的衍生自`CFormView`，叫用其中一個建構函式建立的檢視物件，並找出檢視所依據的對話方塊資源。 您可以依名稱 (pass 字串做為引數的建構函式) 或依識別碼 (pass 不帶正負號的整數做為引數) 來識別資源。

表單檢視 視窗和子控制項不會建立直到`CWnd::Create`呼叫。 `CWnd::Create` 由文件和檢視建立程序的一部分，其中的文件範本由架構呼叫。

> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 建構函式，在叫用建構函式， `CFormView::CFormView`、 資源名稱或識別碼做為引數，如上述的類別概觀中所示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

MFC 用來確保完成初始化後再執行其他作業。

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>傳回值

如果這個對話方塊的初始化函式已完成，則為 true。

## <a name="see-also"></a>另請參閱

[MFC 範例 SNAPVW](../../visual-cpp-samples.md)<br/>
[MFC 範例 VIEWEX](../../visual-cpp-samples.md)<br/>
[CScrollView 類別](../../mfc/reference/cscrollview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView 類別](../../mfc/reference/cscrollview-class.md)
