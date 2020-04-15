---
title: CMFCRibbonCustomizeDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375199"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 類別

顯示功能區 **「自訂**」頁。

## <a name="syntax"></a>語法

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 功能定製對話::CMFC 功能定製對話](#cmfcribboncustomizedialog)|建構 `CMFCRibbonCustomizeDialog` 物件。|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|

## <a name="remarks"></a>備註

如果您不處理AFX_WM_ON_RIBBON_CUSTOMIZE消息,或者從消息處理程式返回 0,MFC 會自動實例化此類。

如果要在應用程式中使用此類來顯示功能區**自定義**對話框,只需實例化它並`DoModal`調用 方法。

由於此類派生自[CMFC 屬性表類](../../mfc/reference/cmfcpropertysheet-class.md),`CMFCPropertySheet`因此可以使用 API 添加自定義頁面。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFC 功能定製對話](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbon自定義對話框.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFC 功能定製對話::CMFC 功能定製對話

建構 `CMFCRibbonCustomizeDialog` 物件。

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向父視窗(通常是主框架)的指標。

*pRibbon*<br/>
[在]要自定義的`CMFCRibbonBar`指標。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCRibbonCustomizeDialog`物件。

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>備註

建構函數實例化[了 CMFCRibbon 自定義屬性頁類](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)物件,並將其添加到屬性工作表頁的集合中。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
