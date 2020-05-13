---
title: CBitmap 類別
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352736"
---
# <a name="cbitmap-class"></a>CBitmap 類別

封裝 Windows 繪圖裝置介面 (GDI) 點陣圖，並提供操作點陣圖的成員函式。

## <a name="syntax"></a>語法

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 點陣圖::C 位圖](#cbitmap)|建構 `CBitmap` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 點陣圖::建立點陣圖](#createbitmap)|使用具有指定寬度、高度和位模式的與設備相關的記憶體位圖初始化物件。|
|[C 位映射::創建點陣圖間接](#createbitmapindirect)|使用在`BITMAP`結構中給出的寬度、高度和位模式(如果指定)的位圖初始化物件。|
|[C 位映射::建立相容點陣圖](#createcompatiblebitmap)|使用點陣圖初始化物件,使其與指定的設備相容。|
|[C 位映射::建立可丟棄的點陣圖](#creatediscardablebitmap)|使用與指定設備相容的可丟棄位圖初始化物件。|
|[CBitmap::從手處理](#fromhandle)|當為 Windows`CBitmap``HBITMAP`位圖指定句柄時,返回指向物件的指標。|
|[C 點陣圖::取得點陣圖](#getbitmap)|使用有關位`BITMAP`圖的資訊填充結構。|
|[C 位映射::取得點陣陣](#getbitmapbits)|將指定點陣圖的位數複製到指定的緩衝區中。|
|[C 位映射::取得點陣圖維度](#getbitmapdimension)|返回位圖的寬度和高度。 假定高度和寬度以前由[SetBitmapDimension 成員](#setbitmapdimension)函數設置。|
|[C 位映射::載入點陣圖](#loadbitmap)|通過從應用程式的可執行檔載入指定的點陣圖資源並將位映射附加到物件來初始化物件。|
|[C 位映射::載入對應的點陣圖](#loadmappedbitmap)|載入點陣圖並將顏色映射到目前系統顏色。|
|[C 點陣圖::載入OEM比特圖](#loadoembitmap)|通過載入預定義的 Windows 位圖並將點陣圖附加到物件來初始化物件。|
|[C 位映射::設定點陣圖位](#setbitmapbits)|將位圖的位位設置到指定的位值。|
|[C 位映射::設定點陣圖維度](#setbitmapdimension)|以 0.1 毫米單位為單位將寬度和高度分配給位圖。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmap::運算符 HBITMAP](#operator_hbitmap)|返回附加到`CBitmap`物件的 Windows 句柄。|

## <a name="remarks"></a>備註

要使用`CBitmap`物件,建構物件,使用初始化成員函數之一將位圖句柄附加到物件,然後調用對象的成員函數。

有關使用圖形物件的詳細資訊,請參閱`CBitmap`圖形[物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>C 點陣圖::C 位圖

建構 `CBitmap` 物件。

```
CBitmap();
```

### <a name="remarks"></a>備註

生成的物件必須使用初始化成員函數之一進行初始化。

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>C 點陣圖::建立點陣圖

初始化具有指定寬度、高度和位元模式之因裝置而異的記憶體點陣圖。

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

*N飛機*<br/>
指定點陣圖中色彩平面的數目。

*nBitcount*<br/>
指定每個顯示像素的色彩位元數目。

*lpBits*<br/>
指向位元組陣列，其中包含初始點陣圖位元值。 如果為 NULL，則不會初始化新的點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

對於顏色位圖,應將*nPlanes*或*nBitcount*參數設置為 1。 如果這兩個參數都設為 1， `CreateBitmap` 會建立單色點陣圖。

雖然您無法直接選取用於顯示裝置的點陣圖，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 選取一個點陣圖作為「記憶體裝置內容」的目前點陣圖，再使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函式將該點陣圖複製到任何相容裝置內容。

當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。

有關詳細資訊,請參閱`bmBits``BITMAP`結構中欄位的說明。 [CBitmap::CreateBitmapIndirect](/windows/win32/api/wingdi/ns-wingdi-bitmap) 成員函式下提供 [BITMAP](#createbitmapindirect) 結構的說明。

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>C 位映射::創建點陣圖間接

初始化具有*lpBitmap*指向的結構中給出的寬度、高度和位模式的位圖(如果指定了)。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>參數

*lpBitmap*<br/>
指向包含位圖資訊的[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

儘管無法直接為顯示設備選擇位圖,但可以使用[CDC::選擇 Object,](../../mfc/reference/cdc-class.md#selectobject)並使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函數將其作為記憶體設備上下文的當前位圖選擇。 [(CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函數可以將當前畫筆的位圖直接複製到顯示設備上下文。

如果使用`BITMAP``GetObject`*函數填充了 lpBitmap*參數指向的結構,則不會指定位圖位位,並且位圖未初始化。 要初始化點陣圖,應用程式可以使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits)等`CGdiObject::GetObject``CreateBitmapIndirect`函數將位從

完成使用`CBitmap``CreateBitmapIndirect`函數創建的物件後,首先從設備上下文中選擇位圖,然後刪除`CBitmap`該物件。

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>C 位映射::建立相容點陣圖

初始化與*pDC*指定的設備相容的點陣圖。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指定設備上下文。

*n 寬度*<br/>
指定點陣圖的寬度 (以像素為單位)。

*nHeight*<br/>
指定點陣圖的高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖的顏色平面數或每圖元格式與指定設備上下文相同。 它可以選擇作為當前位圖的任何記憶體設備,相容*pDC*指定的。

如果*pDC*是記憶體裝置上下文,則傳回的點陣圖的格式與該裝置上下文中當前選擇的點陣圖相同。 "記憶體裝置上下文"是表示顯示表面的記憶體塊。 它可用於在將圖像複製到相容設備的實際顯示表面之前在記憶體中準備圖像。

創建記憶體裝置上下文時,GDI 會自動為其選擇單色股票位圖。

由於顏色儲存器裝置上下文可以選擇顏色或單色位圖,`CreateCompatibleBitmap`因此函數返回的位圖格式並不總是相同的;因此,該函數返回的位圖格式並不總是相同的。否則,該函數返回的位圖格式將始終相同。但是,非記憶體裝置上下文的相容位圖的格式始終採用設備的格式。

完成使用`CBitmap``CreateCompatibleBitmap`函數創建的物件後,首先從設備上下文中選擇位圖,然後刪除`CBitmap`該物件。

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>C 位映射::建立可丟棄的點陣圖

初始化可丟棄的位圖,該位圖與*pDC*標識的設備上下文相容。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指定設備上下文。

*n 寬度*<br/>
指定位圖的寬度(以位錶示)。

*nHeight*<br/>
指定位圖的高度(以位錶示)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

點陣圖的顏色平面數或每圖元格式與指定設備上下文相同。 應用程式可以選擇此位圖作為與*pDC*指定的記憶體設備的當前位圖。

僅當應用程式未將其選擇到顯示上下文中時,Windows 才能丟棄由此函數創建的位圖。 如果 Windows 在未選擇的圖時丟棄點陣圖,並且應用程式以後嘗試選擇它,[則 CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函數將傳回 NULL。

完成使用`CBitmap``CreateDiscardableBitmap`函數創建的物件後,首先從設備上下文中選擇位圖,然後刪除`CBitmap`該物件。

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::從手處理

當為 Windows `CBitmap` GDI 位圖指定句柄時,返回指向物件的指標。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
指定 Windows GDI 位圖。

### <a name="return-value"></a>傳回值

指向`CBitmap`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果物件`CBitmap`尚未附加到句柄,則創建並附加`CBitmap`臨時 物件。 此臨時`CBitmap`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 另一種說法是臨時物件僅在處理一個視窗消息期間有效。

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>C 點陣圖::取得點陣圖

檢索附加點陣圖的圖像屬性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>參數

*pBitMap*<br/>
指向將接收圖像屬性的[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)結構的指標。 此參數不能為 NULL。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>C 位映射::取得點陣陣

將附加點陣圖的位模式複製到指定的緩衝區中。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>參數

*dw( Dw) Count*<br/>
要複製到緩衝區的位元組數目。

*lpBits*<br/>
指向將接收位圖的緩衝區的指標。

### <a name="return-value"></a>傳回值

如果方法成功,則複製到緩衝區的位元組數;否則 0。

### <a name="remarks"></a>備註

使用[CBitmap::GetBitmap](#getbitmap)確定所需的緩衝區大小。

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>C 位映射::取得點陣圖維度

返回位圖的寬度和高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>傳回值

位圖的寬度和高度,以 0.1 毫米為單位測量。 高度位於物件`cy`的成員`CSize`中,寬度位於成員中`cx`。 如果未使用`SetBitmapDimension`設置位圖寬度和高度,則返回值為 0。

### <a name="remarks"></a>備註

使用[SetBitmapDimension 成員](#setbitmapdimension)函數假定高度和寬度以前已設置。

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>C 位映射::載入點陣圖

從應用程式的執行檔載入由*lpszResourceName*命名的位式圖資源,或由*nIDResource*中的 ID 號識別。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpsz 資源名稱*<br/>
包含點陣圖資源名稱的 null 連接字串。

*nID資源*<br/>
指定點陣圖資源的資源 ID 號。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

載入的點陣圖附加`CBitmap`到 物件。

如果*lpszResourceName*標誌的點陣圖不存在,或者記憶體不足以載入位圖,則函數傳回 0。

您可以使用[CGdiObject::DeleteObject 函數](../../mfc/reference/cgdiobject-class.md#deleteobject)刪除函數`LoadBitmap`載入的點`CBitmap`陣圖,否則析構函數將為您刪除物件。

> [!CAUTION]
> 在刪除物件之前,請確保未將其選擇到設備上下文中。

以下點陣圖已新增到 Windows 版本 3.1 及更高版本:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

這些點陣圖在 Windows 版本 3.0 和更早版本的設備驅動程式中找不到。 有關點陣圖的完整清單及其外觀的顯示,請參閱 Windows SDK。

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>C 位映射::載入對應的點陣圖

呼叫此成員函數以載入點陣圖並將顏色映射到當前系統顏色。

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
位圖資源的 ID。

*nFlags*<br/>
位圖的標誌。 可以是零或CMB_MASKED。

*lpColorMap*<br/>
指向包含映射點`COLORMAP`圖所需的顏色資訊的結構的指標。 如果此參數為 NULL,則函數使用預設顏色映射。

*nMapSize*<br/>
由 lpColorMap 指向的顏色*貼圖的數量*。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

預設情況下,`LoadMappedBitmap`將映射按鈕字形中常用的顏色。

有關創建映射點圖的資訊,請參閱 Windows 函數[創建映射的雙邊地圖](https://go.microsoft.com/fwlink/p/?linkid=230562)和 Windows SDK 中的[COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap)結構。

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>C 點陣圖::載入OEM比特圖

載入 Windows 使用的預先定義點陣圖。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>參數

*nIDBitmap*<br/>
預定義的 Windows 位圖的 ID 號。 以下 WINDOWS 列出了可能的值。H:

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

以OBM_OLD開頭的位圖名稱表示 Windows 版本在 3.0 之前使用的位圖。

請注意,在包括 WINDOWS 之前,必須定義常量 OEM 資源。H 以便使用**OBM_常量**中的任何一個。

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::運算符 HBITMAP

使用此運算元獲取`CBitmap`物件的附加 Windows GDI 句柄。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的 Windows`CBitmap`GDI 物件的句柄;如果成功,則對物件表示的 Windows GDI 物件的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算元是強制轉換運算符,支援直接使用`HBITMAP`物件。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[圖形物件](/windows/win32/gdi/graphic-objects)。

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>C 位映射::設定點陣圖位

將位圖的位位設置到*lpBits*給出的位值。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>參數

*dw( Dw) Count*<br/>
指定*lpBits*指向的位元組數。

*lpBits*<br/>
指向包含要複製到`CBitmap`物件的圖元值的 BYTE 陣列。 為了使位圖能夠正確呈現其圖像,應設置這些值的格式,使其與創建 CBitmap 實例時指定的高度、寬度和顏色深度值一致。 有關詳細資訊,請參閱[CBitmap::建立位圖](#createbitmap)。

### <a name="return-value"></a>傳回值

用於設置位圖位的位元組;如果函數失敗,為 0。

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>C 位映射::設定點陣圖維度

以 0.1 毫米單位為單位將寬度和高度分配給位圖。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
指定位圖的寬度(以 0.1 毫米為單位)。

*nHeight*<br/>
指定位圖的高度(以 0.1 毫米為單位)。

### <a name="return-value"></a>傳回值

前面的點陣圖尺寸。 高度位於物件`cy`的成員變數中`CSize`,寬度位於成員變數中。 `cx`

### <a name="remarks"></a>備註

GDI 不使用這些值,除非在應用程式呼叫[GetBitmapDimension 成員](#getbitmapdimension)函數時返回它們。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
