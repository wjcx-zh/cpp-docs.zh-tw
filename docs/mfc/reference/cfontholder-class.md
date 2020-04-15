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
ms.openlocfilehash: 6a053f127123a9ca21853189b9458738b217ee2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373819"
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
|[CFontHolder:C方霍爾德](#cfontholder)|建構 `CFontHolder` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFontHolder::獲取顯示字串](#getdisplaystring)|檢索容器屬性瀏覽器中顯示的字串。|
|[CFontHolder:獲取方調度](#getfontdispatch)|返回字體的`IDispatch`介面。|
|[CFontHolder::獲取方瑟柄](#getfonthandle)|將句柄返回到 Windows 字體。|
|[CFontHolder::初始化字體](#initializefont)|初始化 `CFontHolder` 物件。|
|[CFontHolder::查詢文字參數](#querytextmetrics)|檢索相關字體的資訊。|
|[CFont持有人::釋放字體](#releasefont)|斷開`CFontHolder`物件與`IFont``IFontNotification`和介面的連接。|
|[CFontHolder::選擇](#select)|在設備上下文中選擇字體資源。|
|[CFontHolder::設置字體](#setfont)|將`CFontHolder`物件連接`IFont`到介面。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|指向`CFontHolder`物件介面`IFont`的指標。|

## <a name="remarks"></a>備註

`CFontHolder`沒有基類。

使用此類可實現控制項的自訂字體屬性。 有關創建此類屬性的資訊,請參閱[「ActiveX 控件:使用字體](../../mfc/mfc-activex-controls-using-fonts.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CFontHolder`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder:C方霍爾德

建構 `CFontHolder` 物件。

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>參數

*p 通知*<br/>
指向字體介面的`IPropertyNotifySink`指標。

### <a name="remarks"></a>備註

在使用結果`InitializeFont`物件之前,必須調用它來初始化結果物件。

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::獲取顯示字串

檢索可在容器的屬性瀏覽器中顯示的字串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>參數

*strValue*<br/>
引用用於保存顯示字串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="return-value"></a>傳回值

如果已成功檢索字串,則非零;否則 0。

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder:獲取方調度

呼叫此功能以檢索指向字體調度介面的指標。

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>傳回值

指向`CFontHolder`物件介面`IFontDisp`的指標。 請注意,調用`GetFontDispatch`的函數在使用此`IUnknown::Release`介面指標時必須調用它。

### <a name="remarks"></a>備註

通話`InitializeFont`前通`GetFontDispatch`話 。

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::獲取方瑟柄

調用此函數以獲取 Windows 字體的句柄。

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>參數

*cyLogic*<br/>
以邏輯單位表示繪製控制件的矩形的高度。

*環測量*<br/>
控件的高度(以MM_HIMETRIC單位為單位)。

### <a name="return-value"></a>傳回值

字體物件的句柄;否則 NULL。

### <a name="remarks"></a>備註

*cyLogic*和*cyHimetric*的比率用於計算以MM_HIMETRIC為單位表示的字體點大小的正確顯示大小:

顯示大小 = ( *cyLogic* / *cyhimetric*) X 字型大小

沒有參數的版本會為螢幕返回正確大小的字體的句柄。

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::初始化字體

初始化 `CFontHolder` 物件。

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>參數

*普豐德斯茨*<br/>
指向指定字型特徵的字型描述結構 ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) 的指標。

*pFontDisp 環境*<br/>
指向容器的環境字體屬性的指標。

### <a name="remarks"></a>備註

如果*pFontDispAmbient*不是 NULL,則`CFontHolder`物件將連接到容器`IFont`的環境字型 屬性使用的介面的複製。

如果*pFontDispAmbient*為 NULL,則從*pFontDesc*指向的字型說明創建新的字體物件,或者從預設說明創建*pFontDesc(如果 pFontDesc*為 NULL)。

構造`CFontHolder`物件後調用此函數。

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

指向`CFontHolder`物件介面`IFont`的指標。

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::查詢文字參數

檢索`CFontHolder`物件表示的物理字體的資訊。

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>參數

*lptm*<br/>
指向將接收資訊的[TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw)結構的指標。

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFont持有人::釋放字體

此函數斷開`CFontHolder`物件`IFont`與其介面的連接。

```
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::選擇

呼叫此功能以在指定的裝置上下文中選擇控制項的字型。

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>參數

*pDC*<br/>
選擇字型的設備上下文。

*cyLogic*<br/>
以邏輯單位表示繪製控制件的矩形的高度。

*環測量*<br/>
控件的高度(以MM_HIMETRIC單位為單位)。

### <a name="return-value"></a>傳回值

指向要替換的字體的指標。

### <a name="remarks"></a>備註

有關*cyLogic*和*cyHimetric*參數的討論,請參閱[GetFontHandle。](#getfonthandle)

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::設置字體

釋放任何現有字體並將`CFontHolder`物件連接`IFont`到介面。

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>參數

*P 紐豐特*<br/>
指向新`IFont`介面的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 類別](../../mfc/reference/cpropexchange-class.md)
