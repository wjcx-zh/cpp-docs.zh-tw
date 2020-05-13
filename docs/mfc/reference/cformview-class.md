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
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373806"
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

表單檢視基本上是包含控制項的檢視。 這些控制項根據對話方塊範本資源而佈置。 如果您想要應用程式中有表單，請使用 `CFormView`。 這些檢視支援根據需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能進行滾動。

創建[基於表單的應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)時,可以將其檢視類`CFormView`基於,使其成為基於窗體的應用程式。

您還可以將新的[「表單主題」](../../mfc/form-views-mfc.md)插入到基於文檔檢視的應用程式中。 即使您的應用程式一開始不支援表單，Visual C++ 也會在您插入新表單時加入這項支援。

MFC 應用程式精靈和 [加入類別] 命令是建立表單架構應用程式的慣用方法。 如果需要建立式裝置的應用程式而不使用這些方法,請參閱[建立新應用程式 。](../../mfc/reference/creating-a-forms-based-mfc-application.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CForm查看:CForm檢視

建構 `CFormView` 物件。

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

### <a name="remarks"></a>備註

創建派生自`CFormView`的類型的物件時,請調用其中一個構造函數來創建視圖物件並標識視圖所基於的對話框資源。 您可以按名稱(將字串作為參數傳遞給建構函數)或通過其 ID(傳遞未簽名的整數作為參數)標識資源。

在調用表單視窗和子控制項之前`CWnd::Create`,不會創建窗體檢視視窗和子控制件。 `CWnd::Create`框架呼叫該框架作為文件和檢視創建過程的一部分,該過程由文檔範本驅動。

> [!NOTE]
> 派生類*必須*提供其自己的構造函數。 在建構函數中,調用建構函數,`CFormView::CFormView`將資源名稱或 ID 作為參數,如前面的類概述所示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView:IsinitDlg 完成

MFC 用來確保完成初始化後再執行其他作業。

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>傳回值

如果這個對話方塊的初始化函式已完成，則為 true。

## <a name="see-also"></a>另請參閱

[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品檢視](../../overview/visual-cpp-samples.md)<br/>
[CScrollView 類別](../../mfc/reference/cscrollview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView 類別](../../mfc/reference/cscrollview-class.md)
