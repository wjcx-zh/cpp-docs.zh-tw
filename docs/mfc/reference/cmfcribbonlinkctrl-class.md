---
title: CMFCRibbonLinkCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 12a83e45176f7fc6020da1f0d0ee5923ef0f466c
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866151"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 類別

實作放置在功能區上的超連結。 當您按一下時，超連結會開啟網頁。
如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|建構並初始化 `CMFCRibbonLinkCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(覆寫 `CMFCRibbonButton::CopyFrom`。)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(覆寫[CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|傳回超連結的值。|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(覆寫[CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(覆寫[CMFCRibbonButton:: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)。)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(覆寫[CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(覆寫 `CMFCRibbonButton::OnMouseMove`。)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|開啟超連結中指定的網頁。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|設定超連結的值。|

## <a name="remarks"></a>備註

建立超連結之後, 藉由呼叫[CMFCRibbonPanel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)將它新增至面板。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp; [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>需求

**標頭:** afxRibbonLinkCtrl。h

##  <a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

建立[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)物件的結構並加以初始化。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>參數

*nID*<br/>
在指定按一下連結控制項時所執行之命令的命令識別碼。

*lpszText*<br/>
在指定要在連結控制項上顯示的標籤。

*lpszLink*<br/>
在指定與連結控制項相關聯的超連結。

### <a name="example"></a>範例

下列範例示範如何使用`CMFCRibbonLinkCtrl`類別的函式。 此程式碼片段是[功能區小工具範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl:: CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

[in] *src*<br/>

### <a name="remarks"></a>備註

##  <a name="getcompactsize"></a>CMFCRibbonLinkCtrl:: GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink

傳回超連結的值。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>傳回值

超連結的目前值。

### <a name="remarks"></a>備註

##  <a name="getregularsize"></a>CMFCRibbonLinkCtrl:: GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="gettooltiptext"></a>CMFCRibbonLinkCtrl:: GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl:: OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>參數

在*CDC&#42;*<br/>
在*CRect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>

### <a name="remarks"></a>備註

##  <a name="onmousemove"></a>CMFCRibbonLinkCtrl:: OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>參數

在*點*<br/>

### <a name="remarks"></a>備註

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>備註

##  <a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink

開啟超連結中指定的網頁。

```
BOOL OpenLink();
```

### <a name="return-value"></a>傳回值

如果已成功開啟相關聯的網頁, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用與`CMFCRibbonLinkCtrl`物件相關聯的超連結, 開啟網頁。

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

設定超連結的值。

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>參數

*lpszLink*<br/>
在指定超連結文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
