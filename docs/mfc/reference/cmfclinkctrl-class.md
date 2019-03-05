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
ms.openlocfilehash: a4324fad7668907600cbaebeb5c9de4ad0e7c1e4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302713"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 類別

`CMFCLinkCtrl`類別顯示為超連結的按鈕，並按一下按鈕時叫用連結的目標。

## <a name="syntax"></a>語法

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|顯示指定的 URL 做為按鈕文字。|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|設定隱含的通訊協定 (例如，"http:") 的 URL。|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|調整包含按鈕的文字或點陣圖按鈕。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|繪製焦點矩形的按鈕前，由架構呼叫。|

## <a name="remarks"></a>備註

當您按一下按鈕，衍生自`CMFCLinkCtrl`類別，架構就會將按鈕的 URL 傳遞做為參數`ShellExecute`方法。 則`ShellExecute`方法開啟的 URL 目標。

## <a name="example"></a>範例

下列範例示範如何設定的大小`CMFCLinkCtrl`物件，以及如何設定 url 和中的工具提示`CMFCLinkCtrl`物件。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

繪製焦點矩形的按鈕前，由架構呼叫。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rectClient*<br/>
[in]之界限的連結控制項的矩形。

### <a name="remarks"></a>備註

當您想要使用自己的程式碼繪製按鈕的焦點矩形，請覆寫這個方法。

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

顯示指定的 URL 做為按鈕文字。

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
[in]要顯示的按鈕文字。

### <a name="remarks"></a>備註

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

設定隱含的通訊協定 (例如，"http:") 的 URL。

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>參數

*lpszPrefix*<br/>
[in]URL 通訊協定前置詞。

### <a name="remarks"></a>備註

這個方法可用於設定 URL 前置詞。 前置詞不會顯示在按鈕的臉部，但您可以使用它來瀏覽至的 URL 目標。

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

調整包含按鈕的文字或點陣圖按鈕。

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>參數

*bVCenter*<br/>
[in]為 true，則按鈕文字和點陣圖的頂端和底部的連結控制中; 之間的垂直置中對齊否則為 FALSE。 預設值為 FALSE。

*bHCenter*<br/>
[in]為 true，則按鈕文字和點陣圖的左邊和右邊的連結控制中; 之間的水平置中對齊否則為 FALSE。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含連結控制項的新大小。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl 類別](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
