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
ms.openlocfilehash: 5d00c17b2ede654b9bdd214a8649f1237b9d9fdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375107"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 類別

實作放置在功能區上的超連結。 當您按一下時，超連結會開啟網頁。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|建構並初始化 `CMFCRibbonLinkCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(覆寫 `CMFCRibbonButton::CopyFrom`。)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|( 覆寫[CMFC 功能按鈕:取得壓縮大小](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|傳回超連結的值。|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(覆寫[CMFC 功能按鈕:取得一般大小](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|( 覆寫[CMFC 功能化按鈕:抓取工具提示文字](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(覆寫[CMFC 功能按鈕:onDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[CMFC 功能基礎元素:在DrawMenuImage.)](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(覆寫 `CMFCRibbonButton::OnMouseMove`。)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|開啟超連結中指定的網頁。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|設定超連結的值。|

## <a name="remarks"></a>備註

創建超連結後,請透過調用[CMFC 功能程式:::添加](../../mfc/reference/cmfcribbonpanel-class.md#add)將其添加到面板中。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMFC 功能基礎元素](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFC 功能按鈕](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFC剪連結Ctrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonLinkCtrl.h

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a>CMFC 剪線連結Ctrl::CMFC 剪線連結Ctrl

建構並初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)物件。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]指定按一下連結控制項時執行的命令的命令 ID。

*lpszText*<br/>
[在]指定要顯示在連結控制件上的標籤。

*lpszLink*<br/>
[在]指定與連結控制件關聯的超連結。

### <a name="example"></a>範例

下面的範例展示如何使用`CMFCRibbonLinkCtrl`類的構造函數。 此代碼段是[功能區小工具示例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a>CMFC剪髮連結Ctrl::從複製

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

[在]*斯爾克*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能連結Ctrl:取得壓縮尺寸

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a>CMFC 剪連結Ctrl:取得連結

傳回超連結的值。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>傳回值

超連結的當前值。

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a>CMFC 功能連結Ctrl:取得一般大小

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a>CMFC 功能連結Ctrl:取得工具提示文字

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFC功能連結Ctrl:在DrawMenu圖像

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>參數

[在]*CDC&#42;*<br/>
[在]*CRect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFC 剪貼連結Ctrl::正在繪製工具提示影像

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a>CMFC里賽林Ctrl:在畫上

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a>CMFC里塞林克Ctrl:在滑鼠移動

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>參數

[在]*點*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a>CMFC剪連結Ctrl:onSeticon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>備註

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a>CMFC剪連結Ctrl::打開連結

開啟超連結中指定的網頁。

```
BOOL OpenLink();
```

### <a name="return-value"></a>傳回值

如果關聯的網頁已成功打開,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

使用與`CMFCRibbonLinkCtrl`物件關聯的超鏈接打開網頁。

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a>CMFC 剪線連結::設定連結

設定超連結的值。

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>參數

*lpszLink*<br/>
[在]指定超連結文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
