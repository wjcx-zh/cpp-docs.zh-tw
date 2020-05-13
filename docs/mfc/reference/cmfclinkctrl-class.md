---
title: CMFCLinkCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 79edff8be6e2c37baa938fc5b624253932609e17
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754254"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 類別

類`CMFCLinkCtrl`將顯示一個按鈕作為超連結,並在單擊按鈕時調用連結的目標。

## <a name="syntax"></a>語法

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|將指定的網址 顯示為按鈕文字。|
|[CMFCLinkCtrl::設定URL首綴](#seturlprefix)|設置 URL 的隱式協定(例如"HTTP:")。|
|[CMFClinkctrl::大小到內容](#sizetocontent)|調整按鈕的大小以包含按鈕文本或位圖。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFClinkCtrl:在Draw焦點上](#ondrawfocusrect)|在繪製按鈕的焦點矩形之前由框架調用。|

## <a name="remarks"></a>備註

按下派生自類的`CMFCLinkCtrl`按鈕時,框架將按鈕的 URL 作為`ShellExecute`參數傳遞給 方法。 然後,`ShellExecute`該方法將打開 URL 的目標。

## <a name="example"></a>範例

下面的範例展示如何設定`CMFCLinkCtrl`物件的大小,以及如何`CMFCLinkCtrl`在物件中設置網址和工具提示。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFClinkCtrl:在Draw焦點上

在繪製按鈕的焦點矩形之前由框架調用。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectClient*<br/>
[在]綁定連結控制件的矩形。

### <a name="remarks"></a>備註

如果要使用自己的代碼繪製按鈕的焦點矩形,請重寫此方法。

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

將指定的網址 顯示為按鈕文字。

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
[在]要顯示的按鈕文字。

### <a name="remarks"></a>備註

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::設定URL首綴

設置 URL 的隱式協定(例如"HTTP:")。

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>參數

*lpszPrefix*<br/>
[在]URL 協定的前置碼。

### <a name="remarks"></a>備註

使用此方法設定 URL 首碼。 首碼不顯示在按鈕的表面上,但您可以使用它説明瀏覽到 URL 的目標。

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFClinkctrl::大小到內容

調整按鈕的大小以包含按鈕文本或位圖。

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>參數

*bV中心*<br/>
[在]TRUE 將按鈕文本和位圖垂直居中,在連結控制件的頂部和底部之間;否則,FALSE。 預設值為 FALSE。

*bH中心*<br/>
[在]TRUE 將按鈕文本和位圖水準居中,水平位於連結控制件的左右兩側;否則,FALSE。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

包含連結控制件的新大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl 類別](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
