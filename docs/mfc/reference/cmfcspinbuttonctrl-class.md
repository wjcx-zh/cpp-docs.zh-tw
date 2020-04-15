---
title: CMFCSpinButtonCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376181"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 類別

類`CMFCSpinButtonCtrl`支援繪製旋轉按鈕控制項的可視化管理員。

## <a name="syntax"></a>語法

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|預設建構函式。|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCSpinButtonCtrl::在畫上](#ondraw)|重新繪製當前旋轉按鈕控制項。|

## <a name="remarks"></a>備註

要使用視覺化管理程式在應用程式中繪製旋轉按鈕控制項,請將`CSpinButtonCtrl`類的所有實例替換為`CMFCSpinButtonCtrl`類。

## <a name="example"></a>範例

下面的範例展示如何創建`CMFCSpinButtonCtrl`類的物件並使用其`Create`方法。

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::在畫上

重新繪製當前旋轉按鈕控制項。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

### <a name="remarks"></a>備註

框架呼叫`CMFCSpinButtonCtrl::OnPaint`方法來處理[CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)訊息,該方法反過來呼`CMFCSpinButtonCtrl::OnDraw`叫此方法 。 重寫此方法以自定義框架繪製旋轉按鈕控制項的方式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)
