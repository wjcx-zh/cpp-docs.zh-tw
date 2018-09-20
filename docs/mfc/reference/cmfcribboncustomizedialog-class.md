---
title: CMFCRibbonCustomizeDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a51fe21594bc900923b7d8d0ff30e8599a378da8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409346"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 類別

顯示功能區**自訂**頁面。

## <a name="syntax"></a>語法

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|建構 `CMFCRibbonCustomizeDialog` 物件。|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|

## <a name="remarks"></a>備註

MFC 會自動產生這個類別，如果您不會處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息，或如果您從訊息處理常式傳回 0。

如果您想要在您的應用程式中使用這個類別，以顯示功能區**自訂**對話方塊方塊中，只要它具現化，並呼叫`DoModal`方法。

因為這個類別衍生自[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)，您可以使用，以新增自訂頁面`CMFCPropertySheet`API。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribboncustomizedialog.h

##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

建構 `CMFCRibbonCustomizeDialog` 物件。

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]父視窗 （通常是主要畫面格） 的指標。

*pRibbon*<br/>
[in]指標`CMFCRibbonBar`要進行自訂。

### <a name="example"></a>範例

下列範例示範如何建構`CMFCRibbonCustomizeDialog`物件。

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>備註

建構函式具現化[CMFCRibbonCustomizePropertyPage 類別](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)物件，並將它加入至屬性工作表頁的集合。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
