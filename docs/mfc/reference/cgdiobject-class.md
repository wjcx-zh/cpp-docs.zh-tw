---
title: CGdiObject 類別
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506260"
---
# <a name="cgdiobject-class"></a>CGdiObject 類別

為各種 Windows 繪圖裝置介面 (GDI) 物件 (例如點陣圖、區域、筆刷、畫筆、調色盤和字型) 提供基底類別。

## <a name="syntax"></a>語法

```
class CGdiObject : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|建構 `CGdiObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|將 Windows GDI 物件附加至`CGdiObject`物件。|
|[CGdiObject::CreateStockObject](#createstockobject)|抓取其中一個 Windows 預先定義的股票畫筆、筆刷或字型的控制碼。|
|[CGdiObject::DeleteObject](#deleteobject)|藉由釋放與物件相關聯的`CGdiObject`所有系統存放區, 從記憶體中刪除附加至物件的 Windows GDI 物件。|
|[CGdiObject::DeleteTempMap](#deletetempmap)|刪除所建立`CGdiObject`的`FromHandle`任何暫存物件。|
|[CGdiObject::Detach](#detach)|從`CGdiObject`物件卸離 windows gdi 物件, 並將控制碼傳回到 windows gdi 物件。|
|[CGdiObject::FromHandle](#fromhandle)|傳回`CGdiObject`物件的指標, 指定 Windows GDI 物件的控制碼。|
|[CGdiObject::GetObject](#getobject)|填入緩衝區, 其中包含描述附加至`CGdiObject`物件之 Windows GDI 物件的資料。|
|[CGdiObject::GetObjectType](#getobjecttype)|抓取 GDI 物件的型別。|
|[CGdiObject::GetSafeHandle](#getsafehandle)|除非此為 null, 否則會傳回 null。 `m_hObject`|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重設筆刷的原點, 或重設邏輯調色板。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CGdiObject::operator !=](#operator_neq)|判斷兩個 GDI 物件在邏輯上是否不相等。|
|[CGdiObject::operator ==](#operator_eq_eq)|判斷兩個 GDI 物件在邏輯上是否相等。|
|[CGdiObject:: operator HGDIOBJ](#operator_hgdiobj)|抓取附加的 Windows GDI 物件的控制碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|包含 HBITMAP、HPALETTE、HRGN、HBRUSH、HPEN 或 HFONT 附加至此物件的控制碼。|

## <a name="remarks"></a>備註

您永遠不會`CGdiObject`直接建立。 相反地`CPen` , 您會從它的其中一個衍生類別 (例如或`CBrush`) 建立物件。

如需的詳細`CGdiObject`資訊, 請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="attach"></a>CGdiObject:: Attach

將 Windows GDI 物件附加至`CGdiObject`物件。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>參數

*hObject*<br/>
Windows GDI 物件的控制碼 (例如, HPEN 或 HBRUSH)。

### <a name="return-value"></a>傳回值

如果附件成功, 則為非零;否則為0。

##  <a name="cgdiobject"></a>CGdiObject::CGdiObject

建構 `CGdiObject` 物件。

```
CGdiObject();
```

### <a name="remarks"></a>備註

您永遠不會`CGdiObject`直接建立。 相反地`CPen` , 您會從它的其中一個衍生類別 (例如或`Cbrush`) 建立物件。

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

抓取其中一個預先定義的內建 Windows GDI 畫筆、筆刷或字型的控制碼, 並將 GDI 物件附加`CGdiObject`至物件。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
常數, 指定所需的股票物件類型。 如需適當值的描述, 請參閱 Windows SDK 中[GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject)的參數*fnObject* 。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

使用對應至 Windows GDI 物件類型的其中一個衍生類別來呼叫此函式, `CPen`例如股票畫筆。

##  <a name="deleteobject"></a>CGdiObject::D eleteObject

釋放與 Windows GDI 物件相關聯的所有系統存放裝置, 以從記憶體中刪除附加的 Windows GDI 物件。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>傳回值

如果已成功刪除 GDI 物件, 則為非零;否則為0。

### <a name="remarks"></a>備註

與`CGdiObject`物件相關聯的儲存體不會受到此呼叫的影響。 應用程式不應該`DeleteObject` `CGdiObject`在目前選取為裝置內容的物件上呼叫。

刪除模式筆刷時, 不會刪除與筆刷相關聯的點陣圖。 必須獨立刪除點陣圖。

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

由`CWinApp`閒置時間處理常式自動呼叫, `DeleteTempMap`會刪除所建立`CGdiObject`的`FromHandle`任何暫存物件。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>備註

`DeleteTempMap`先卸離附加至暫存`CGdiObject`物件的 Windows GDI 物件, 然後再`CGdiObject`刪除物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

從`CGdiObject`物件卸離 windows gdi 物件, 並將控制碼傳回到 windows gdi 物件。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>傳回值

已`HANDLE`卸離之 Windows GDI 物件的; 如果未附加任何 GDI 物件, 則為 Null。

##  <a name="fromhandle"></a>CGdiObject:: FromHandle

傳回`CGdiObject`物件的指標, 指定 Windows GDI 物件的控制碼。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>參數

*hObject*<br/>
Windows GDI 物件的控制碼。

### <a name="return-value"></a>傳回值

`CGdiObject`的指標, 可能是暫時性或永久的。

### <a name="remarks"></a>備註

如果物件尚未附加至 Windows GDI 物件, 則會建立並附加暫存`CGdiObject`物件。 `CGdiObject`

在下`CGdiObject`一次應用程式的事件迴圈中有閒置時間時, 這個暫存物件才有效, 此時所有的暫存繪圖物件都會被刪除。 另一個指出這種情況的方法是, 暫存物件只在處理一個視窗訊息期間有效。

##  <a name="getobject"></a>  CGdiObject::GetObject

以定義指定物件的資料填滿緩衝區。

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>參數

*nCount*<br/>
指定要複製到*lpObject*緩衝區的位元組數目。

*lpObject*<br/>
指向用來接收資訊的使用者提供緩衝區。

### <a name="return-value"></a>傳回值

已抓取的位元組數目;如果發生錯誤, 則為0。

### <a name="remarks"></a>備註

函式會抓取其類型取決於繪圖物件類型的資料結構, 如下列清單所示:

|Object|緩衝區類型|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|不支援|

如果物件是`CBitmap`物件, `GetObject`則只會傳回點陣圖的寬度、高度和色彩格式資訊。 您可以使用[CBitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)來抓取實際的位。

如果物件是`CPalette`物件, `GetObject`則會抓取指定色板中專案數目的單字。 函式不會取得定義調色板的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構。 應用程式可以藉由呼叫[CPalette:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)來取得有關調色板專案的資訊。

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

抓取 GDI 物件的型別。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>傳回值

如果成功, 則為物件的類型;否則為0。 值可以是下列其中一項：

- OBJ_BITMAP 點陣圖

- OBJ_BRUSH 筆刷

- OBJ_FONT 字型

- OBJ_PAL 調色板

- OBJ_PEN 畫筆

- OBJ_EXTPEN 擴充畫筆

- OBJ_REGION 區域

- OBJ_DC 裝置內容

- OBJ_MEMDC Memory 裝置內容

- OBJ_METAFILE 中繼檔

- OBJ_METADC 中繼檔裝置內容

- OBJ_ENHMETAFILE 增強型中繼檔

- OBJ_ENHMETADC 增強-中繼檔裝置內容

##  <a name="getsafehandle"></a>CGdiObject:: GetSafeHandle

除非此為 null, 否則會傳回 null。 `m_hObject`

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>傳回值

附加的 Windows GDI 物件的控制碼。如果未附加任何物件, 則為 Null。

### <a name="remarks"></a>備註

這是一般控制碼介面架構的一部分, 當 Null 是控制碼的有效或特殊值時很有用。

### <a name="example"></a>範例

  請參閱[CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)的範例。

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

包含 HBITMAP、HRGN、HBRUSH、HPEN、HPALETTE 或 HFONT 附加至此物件的控制碼。

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: operator! =

判斷兩個 GDI 物件在邏輯上是否不相等。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>參數

*obj*<br/>
現有`CGdiObject`的指標。

### <a name="remarks"></a>備註

判斷左側的 GDI 物件是否不等於右邊的 GDI 物件。

##  <a name="operator_eq_eq"></a>CGdiObject:: operator = =

判斷兩個 GDI 物件在邏輯上是否相等。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>參數

*obj*<br/>
現有`CGdiObject`的參考。

### <a name="remarks"></a>備註

判斷左側的 GDI 物件是否等於右邊的 GDI 物件。

##  <a name="operator_hgdiobj"></a>CGdiObject:: operator HGDIOBJ

抓取附加的 Windows GDI 物件的控制碼。如果未附加任何物件, 則為 Null。

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject

重設筆刷的原點, 或重設邏輯調色板。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

雖然`UnrealizeObject`是`CGdiObject`類別的成員函式, 但只能在或`CPalette`物件上`CBrush`叫用。

對於`CBrush`物件, `UnrealizeObject`會引導系統在下一次將指定的筆刷選取為裝置內容時, 重設其原點。 如果物件是`CPalette`物件, `UnrealizeObject`則會指示系統實現此調色板, 就好像先前尚未實現此元件一樣。 下次應用程式針對指定的色板呼叫[CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函數時, 系統會將邏輯調色板完全重新對應到系統調色板。

`UnrealizeObject`函式不應與內建物件搭配使用。 每當`UnrealizeObject`設定新的筆刷來源 (藉由[CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函數) 時, 就必須呼叫函式。 `UnrealizeObject`不得針對目前選取的筆刷或任何顯示內容的目前選取的調色板呼叫函式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 類別](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush 類別](../../mfc/reference/cbrush-class.md)<br/>
[CFont 類別](../../mfc/reference/cfont-class.md)<br/>
[CPalette 類別](../../mfc/reference/cpalette-class.md)<br/>
[CPen 類別](../../mfc/reference/cpen-class.md)<br/>
[CRgn 類別](../../mfc/reference/crgn-class.md)
