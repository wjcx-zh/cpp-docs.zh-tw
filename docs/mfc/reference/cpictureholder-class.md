---
title: CPictureHolder 類別
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 067ea7238c48f2698d7bfe469e9c4be10129c065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364046"
---
# <a name="cpictureholder-class"></a>CPictureHolder 類別

實現圖片屬性,允許使用者在控件中顯示圖片。

## <a name="syntax"></a>語法

```
class CPictureHolder
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPicture持有人::CPictureHolder](#cpictureholder)|建構 `CPictureHolder` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPicture持有人:建立空](#createempty)|建立空的 `CPictureHolder` 物件。|
|[CPicture持有人::從位圖創建](#createfrombitmap)|從位`CPictureHolder`圖創建物件。|
|[CPicture持有人:從圖示建立](#createfromicon)|從圖示`CPictureHolder`創建物件。|
|[CPicture持有人::從Metafile創建](#createfrommetafile)|從元`CPictureHolder`檔案創建物件。|
|[CPicture 持有人:取得顯示字串](#getdisplaystring)|檢索控制容器的屬性瀏覽器中顯示的字串。|
|[CPicture持有人:獲取圖片調度](#getpicturedispatch)|返回`CPictureHolder`物件的`IDispatch`介面。|
|[CPicture 持有人:取得類型](#gettype)|告訴`CPictureHolder`對像是點陣圖、元檔還是圖示。|
|[CPicture持有人:呈現](#render)|渲染圖片。|
|[CPicture持有人::設置圖片調度](#setpicturedispatch)|設置`CPictureHolder`物件`IDispatch`的介面。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPicture持有人:m_pPict](#m_ppict)|指向圖片物件的指標。|

## <a name="remarks"></a>備註

`CPictureHolder`沒有基類。

使用「庫存圖片」屬性,開發人員可以指定用於顯示的點陣圖、圖示或元檔。

有關建立自訂圖片屬性的資訊,請參閱文章[MFC ActiveX 控制件:在 ActiveX 控制件中使用圖片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CPictureHolder`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPicture持有人::CPictureHolder

建構 `CPictureHolder` 物件。

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPicture持有人:建立空

建立空`CPictureHolder`物件並將其連接`IPicture`到介面。

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>傳回值

如果成功創建物件,則非零;否則 0。

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPicture持有人::從位圖創建

使用點陣圖在 中初始化`CPictureHolder`圖片物件 。

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>參數

*idResource*<br/>
位圖資源的資源 ID。

*pBitmap*<br/>
指向[CBitmap](../../mfc/reference/cbitmap-class.md)物件的指標。

*pPal*<br/>
指向[CPalette](../../mfc/reference/cpalette-class.md)物件的指標。

*b 轉讓擁有權*<br/>
指示圖片物件是否將取得位圖和調色板物件的擁有權。

*Hbm*<br/>
處理從中`CPictureHolder`創建物件的點陣圖。

*赫帕爾*<br/>
處理用於呈現點陣圖的調色板。

### <a name="return-value"></a>傳回值

如果成功創建物件,則非零;否則 0。

### <a name="remarks"></a>備註

如果*bTransport 擁有權*為 TRUE,則在此調用返回後,調用方不應以任何方式使用位圖或調色板物件。 如果*bTransport 擁有權*為 FALSE,則調用方負責確保位圖和調色板物件在圖片物件的生存期內保持有效。

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPicture持有人:從圖示建立

使用圖示在 中初始化圖片`CPictureHolder`物件 。

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>參數

*idResource*<br/>
位圖資源的資源 ID。

*hIcon*<br/>
處理從中`CPictureHolder`創建物件的圖示。

*b 轉讓擁有權*<br/>
指示圖片物件是否將取得圖示物件的擁有權。

### <a name="return-value"></a>傳回值

如果成功創建物件,則非零;否則 0。

### <a name="remarks"></a>備註

如果*bTransport 擁有權*為 TRUE,則在此調用返回後,調用方不應以任何方式使用圖示物件。 如果*bTransport 擁有權*為 FALSE,則調用方負責確保圖示物件在圖片物件的生存期內保持有效。

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPicture持有人::從Metafile創建

使用中繼媒體初始化 的`CPictureHolder`圖片物件 。

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>參數

*姆夫*<br/>
處理用於創建`CPictureHolder`物件的元檔。

*xExt*<br/>
圖片的 X 範圍。

*yExt*<br/>
圖片的 Y 範圍。

*b 轉讓擁有權*<br/>
指示圖片物件是否將取得元檔物件的擁有權。

### <a name="return-value"></a>傳回值

如果成功創建物件,則非零;否則 0。

### <a name="remarks"></a>備註

如果*bTransport 擁有權*為 TRUE,則調用方不應在此調用返回後以任何方式使用元檔物件。 如果*bTransport 擁有權*為 FALSE,則調用方負責確保元檔物件在圖片物件的生存期內保持有效。

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPicture 持有人:取得顯示字串

檢索容器的屬性瀏覽器中顯示的字串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>參數

*strValue*<br/>
引用用於保存顯示字串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="return-value"></a>傳回值

如果已成功檢索字串,則非零;否則 0。

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPicture持有人:獲取圖片調度

此函數返回指向`CPictureHolder`物件介面`IPictureDisp`的指標。

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>傳回值

指向`CPictureHolder`物件介面`IPictureDisp`的指標。

### <a name="remarks"></a>備註

調用方在完成此`Release`指標後必須調用它。

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPicture 持有人:取得類型

指示圖片是點陣圖、元文件還是圖示。

```
short GetType();
```

### <a name="return-value"></a>傳回值

指示圖片類型的值。 可能的值及其含義如下:

|值|意義|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`對像是統一的。|
|PICTYPE_NONE|`CPictureHolder`物件為空。|
|PICTYPE_BITMAP|圖片是位圖。|
|PICTYPE_METAFILE|圖片是一個元檔。|
|PICTYPE_ICON|圖片是一個圖示。|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPicture持有人:m_pPict

指向`CPictureHolder`物件介面`IPicture`的指標。

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPicture持有人:呈現

在*rcRender*引用的矩形中渲染圖片。

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要呈現圖片的顯示上下文。

*rcRender*<br/>
要在其中渲染圖片的矩形。

*rcWBounds*<br/>
表示呈現圖片的物件的邊界矩形的矩形。 對於控制項,此矩形是傳遞給[COleControl:::onDraw](../../mfc/reference/colecontrol-class.md#ondraw)的重寫的*rcBounds*參數。

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPicture持有人::設置圖片調度

將`CPictureHolder`物件連接`IPictureDisp`到介面。

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
指向新`IPictureDisp`介面的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder 類別](../../mfc/reference/cfontholder-class.md)
