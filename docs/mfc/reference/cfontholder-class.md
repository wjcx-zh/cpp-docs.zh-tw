---
title: CFontHolder 類別
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 04de8141469f82bdd1fbb6adc1bae94d6026324c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506450"
---
# <a name="cfontholder-class"></a>CFontHolder 類別

實作內建字型屬性，並封裝 Windows 字型物件和 `IFont` 介面的功能。

## <a name="syntax"></a>語法

```
class CFontHolder
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|建構 `CFontHolder` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|抓取容器的屬性瀏覽器中顯示的字串。|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|傳回字型的`IDispatch`介面。|
|[CFontHolder::GetFontHandle](#getfonthandle)|傳回 Windows 字型的控制碼。|
|[CFontHolder::InitializeFont](#initializefont)|`CFontHolder`初始化物件。|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|抓取相關字型的資訊。|
|[CFontHolder::ReleaseFont](#releasefont)|`CFontHolder`中斷物件`IFont`與和`IFontNotification`介面的連接。|
|[CFontHolder::Select](#select)|在裝置內容中選取字型資源。|
|[CFontHolder::SetFont](#setfont)|將物件連接至`IFont`介面。 `CFontHolder`|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|`CFontHolder`物件介面的指標。`IFont`|

## <a name="remarks"></a>備註

`CFontHolder`沒有基類。

使用此類別來為您的控制項執行自訂字型屬性。 如需建立這類屬性的相關資訊, [請參閱 ActiveX 控制項:使用字型](../../mfc/mfc-activex-controls-using-fonts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CFontHolder`

## <a name="requirements"></a>需求

**標頭:** afxctl.h。h

##  <a name="cfontholder"></a>CFontHolder::CFontHolder

建構 `CFontHolder` 物件。

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>參數

*pNotify*<br/>
字型`IPropertyNotifySink`介面的指標。

### <a name="remarks"></a>備註

您必須先`InitializeFont`呼叫來初始化產生的物件, 才能使用它。

##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString

抓取可在容器的屬性瀏覽器中顯示的字串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>參數

*strValue*<br/>
用來存放顯示字串之[CString](../../atl-mfc-shared/reference/cstringt-class.md)的參考。

### <a name="return-value"></a>傳回值

如果成功取出字串, 則為非零;否則為0。

##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

呼叫此函式可抓取字型分派介面的指標。

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>傳回值

`CFontHolder`物件介面的指標。`IFontDisp` 請注意, 呼叫`GetFontDispatch`的函式必須在此介面指標上呼叫`IUnknown::Release` , 才能使用它。

### <a name="remarks"></a>備註

在`InitializeFont` 呼叫`GetFontDispatch`之前呼叫。

##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle

呼叫此函式可取得 Windows 字型的控制碼。

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>參數

*cyLogical*<br/>
繪製控制項之矩形的高度 (以邏輯單位表示)。

*cyHimetric*<br/>
控制項的高度 (以 MM_HIMETRIC 為單位)。

### <a name="return-value"></a>傳回值

字型物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

*CyLogical*和*cyHimetric*的比率是用來針對以 MM_HIMETRIC 單位表示的字型點大小, 計算適當的顯示大小 (以邏輯單位):

顯示大小 = ( *cyLogical*  /  *cyHimetric*) X 字型大小

沒有參數的版本, 會針對螢幕正確地傳回字型大小的控制碼。

##  <a name="initializefont"></a>CFontHolder::InitializeFont

`CFontHolder`初始化物件。

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>參數

*pFontDesc*<br/>
字型描述結構 ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) 的指標, 指定字型的特性。

*pFontDispAmbient*<br/>
容器之環境字型屬性的指標。

### <a name="remarks"></a>備註

如果*pFontDispAmbient*不是 Null, `CFontHolder`物件就會連接到容器的環境字型屬性所`IFont`使用之介面的複製。

如果*pFontDispAmbient*為 Null, 則會從*pFontDesc*所指向的字型描述建立新的字型物件, 或從預設的描述中*pFontDesc*為 Null。

在建立`CFontHolder`物件之後, 呼叫這個函式。

##  <a name="m_pfont"></a>CFontHolder::m_pFont

`CFontHolder`物件介面的指標。`IFont`

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

抓取`CFontHolder`物件所代表之實體字型的資訊。

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>參數

*lptm*<br/>
將接收資訊之[TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw)結構的指標。

##  <a name="releasefont"></a>CFontHolder::ReleaseFont

此函式會`CFontHolder`中斷物件與其`IFont`介面的連接。

```
void ReleaseFont();
```

##  <a name="select"></a>CFontHolder:: Select

呼叫此函式可在指定的裝置內容中選取您的控制項字型。

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要在其中選取字型的裝置內容。

*cyLogical*<br/>
繪製控制項之矩形的高度 (以邏輯單位表示)。

*cyHimetric*<br/>
控制項的高度 (以 MM_HIMETRIC 為單位)。

### <a name="return-value"></a>傳回值

要被取代之字型的指標。

### <a name="remarks"></a>備註

如需*cyLogical*和*cyHimetric*參數的討論, 請參閱[GetFontHandle](#getfonthandle) 。

##  <a name="setfont"></a>CFontHolder::SetFont

釋放任何現有的字型, 並`CFontHolder`將物件連接`IFont`至介面。

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>參數

*pNewFont*<br/>
新`IFont`介面的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 類別](../../mfc/reference/cpropexchange-class.md)
