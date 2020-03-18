---
title: CImageList 類別
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420355"
---
# <a name="cimagelist-class"></a>CImageList 類別

提供 Windows 通用影像清單控制項的功能。

## <a name="syntax"></a>語法

```
class CImageList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CImageList：： CImageList](#cimagelist)|建構 `CImageList` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CImageList：： Add](#add)|將影像或影像新增至影像清單。|
|[CImageList：： Attach](#attach)|將影像清單附加至 `CImageList` 物件。|
|[CImageList：： BeginDrag](#begindrag)|開始拖曳影像。|
|[CImageList：： Copy](#copy)|複製 `CImageList` 物件內的影像。|
|[CImageList：： Create](#create)|初始化影像清單，並將它附加至 `CImageList` 物件。|
|[CImageList：:D eleteImageList](#deleteimagelist)|刪除影像清單。|
|[CImageList：:D eleteTempMap](#deletetempmap)|由[CWinApp](../../mfc/reference/cwinapp-class.md)的閒置時間處理常式呼叫，以刪除 `FromHandle`所建立的任何暫存 `CImageList` 物件。|
|[CImageList：:D etach](#detach)|從 `CImageList` 物件卸離影像清單物件，並將控制碼傳回影像清單。|
|[CImageList：:D ragEnter](#dragenter)|在拖曳作業期間鎖定更新，並在指定的位置顯示拖曳影像。|
|[CImageList：:D ragLeave](#dragleave)|解除鎖定視窗並隱藏拖曳影像，讓視窗可以更新。|
|[CImageList：:D ragMove](#dragmove)|移動在拖放作業期間所拖曳的影像。|
|[CImageList：:D ragShowNolock](#dragshownolock)|在拖曳作業期間顯示或隱藏拖曳影像，而不會鎖定視窗。|
|[CImageList：:D raw](#draw)|繪製在拖放作業期間所拖曳的影像。|
|[CImageList：:D rawEx](#drawex)|在指定的裝置內容中繪製影像清單專案。 函式會使用指定的繪製樣式，並將影像與指定的色彩混合。|
|[CImageList：:D rawIndirect](#drawindirect)|繪製影像清單中的影像。|
|[CImageList：： EndDrag](#enddrag)|結束拖曳作業。|
|[CImageList：： ExtractIcon](#extracticon)|根據影像清單中的影像和遮罩來建立圖示。|
|[CImageList：： FromHandle](#fromhandle)|當提供影像清單的控制碼時，傳回 `CImageList` 物件的指標。 如果 `CImageList` 物件沒有附加至控制代碼，會建立並附加暫存 `CImageList` 物件。|
|[CImageList：： FromHandlePermanent](#fromhandlepermanent)|當提供影像清單的控制碼時，傳回 `CImageList` 物件的指標。 如果 `CImageList` 物件未附加至控制碼，則會傳回 Null。|
|[CImageList：： GetBkColor](#getbkcolor)|抓取影像清單目前的背景色彩。|
|[CImageList：： GetDragImage](#getdragimage)|取得用於拖曳的暫存影像清單。|
|[CImageList：： GetImageCount](#getimagecount)|抓取影像清單中的影像數目。|
|[CImageList：： GetImageInfo](#getimageinfo)|抓取影像的相關資訊。|
|[CImageList：： GetSafeHandle](#getsafehandle)|抓取 `m_hImageList`。|
|[CImageList：： Read](#read)|從封存讀取影像清單。|
|[CImageList：： Remove](#remove)|從影像清單中移除影像。|
|[CImageList：： Replace](#replace)|以新的影像取代影像清單中的影像。|
|[CImageList：： SetBkColor](#setbkcolor)|設定影像清單的背景色彩。|
|[CImageList：： SetDragCursorImage](#setdragcursorimage)|建立新的拖曳影像。|
|[CImageList：： SetImageCount](#setimagecount)|重設影像清單中的影像計數。|
|[CImageList：： SetOverlayImage](#setoverlayimage)|將影像以零為基底的索引新增至要當做覆迭遮罩使用的影像清單。|
|[CImageList：： Write](#write)|將影像清單寫入封存。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImageList：： operator HIMAGELIST](#operator_himagelist)|傳回附加至 `CImageList`的 HIMAGELIST。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CImageList：： m_hImageList](#m_himagelist)|包含附加至此物件之影像清單的控制碼。|

## <a name="remarks"></a>備註

「影像清單」是大小相同影像的集合，其中每一個都可以透過其以零為基底的索引來參考。 影像清單用來有效管理大量圖示或點陣圖。 影像清單中的所有影像都包含在螢幕裝置格式的單一寬點陣圖中。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 Microsoft Win32 應用程式開發介面（API）提供影像清單功能，可讓您繪製影像、建立和終結影像清單、新增和移除影像、取代影像、合併影像，以及拖曳影像。

這個控制項（因此 `CImageList` 類別）僅適用于在 Windows 95/98 和 Windows NT 3.51 版和更新版本下執行的程式。

如需使用 `CImageList`的詳細資訊，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="add"></a>CImageList：： Add

呼叫此函式可將一或多個影像或圖示新增至影像清單。

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>參數

*pbmImage*<br/>
包含影像或影像之點陣圖的指標。 影像的數目是從點陣圖的寬度推斷而來。

*pbmMask*<br/>
包含遮罩之點陣圖的指標。 如果沒有與影像清單搭配使用的遮罩，則會忽略這個參數。

*crMask*<br/>
用來產生遮罩的色彩。 在給定點陣圖中，此色彩的每個圖元都會變更為黑色，且遮罩中的對應位會設定為一。

*hIcon*<br/>
圖示的控制碼，其中包含新影像的點陣圖和遮罩。

### <a name="return-value"></a>傳回值

如果成功，則為第一個新影像以零為基底的索引;否則為-1。

### <a name="remarks"></a>備註

當您完成時，您必須負責釋放圖示控制碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>CImageList：： Attach

呼叫此函式可將影像清單附加至 `CImageList` 物件。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
影像清單物件的控制碼。

### <a name="return-value"></a>傳回值

如果附件成功，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>CImageList：： BeginDrag

呼叫此函式以開始拖曳影像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要拖曳的影像之以零為基底的索引。

*ptHotSpot*<br/>
開始拖曳位置（通常是游標位置）的座標。 座標相對於影像的左上角。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式會建立用來拖曳的暫存影像清單。 影像會結合指定的影像及其遮罩與目前的資料指標。 為了回應後續 WM_MOUSEMOVE 訊息，您可以使用 `DragMove` 成員函式移動拖曳影像。 若要結束拖曳作業，您可以使用 `EndDrag` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>CImageList：： CImageList

建構 `CImageList` 物件。

```
CImageList();
```

##  <a name="copy"></a>CImageList：： Copy

此成員函式會依照 Windows SDK 中的說明，實作用[ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)的 Win32 函式行為。

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>參數

*iDst*<br/>
影像的以零為基底的索引，用來做為複製作業的目的地。

*iSrc*<br/>
要做為複製作業來源之影像的以零為起始的索引。

*uFlags*<br/>
位旗標值，指定要進行的複製作業類型。 這個參數可以是下列其中一個值：

|值|意義|
|-----------|-------------|
|ILCF_MOVE|來源映射會複製到目的地映射的索引。 這項作業會產生指定影像的多個實例。 預設值為 ILCF_MOVE。|
|ILCF_SWAP|來源和目的地影像會交換影像清單中的位置。|

*.Psrc*<br/>
做為複製作業目標之 `CImageList` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>CImageList：： Create

初始化影像清單，並將它附加至[CImageList](../../mfc/reference/cimagelist-class.md)物件。

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*cx*<br/>
每個影像的維度（以圖元為單位）。

*cy*<br/>
每個影像的維度（以圖元為單位）。

*nFlags*<br/>
指定要建立之影像清單的類型。 這個參數可以是下列值的組合，但只能包含其中一個 `ILC_COLOR` 值。

|值|意義|
|-----------|-------------|
|ILC_COLOR|如果未指定任何其他 ILC_COLOR * 旗標，請使用預設行為。 一般來說，預設值是 ILC_COLOR4。但是對於較舊的顯示器驅動程式，預設值是 ILC_COLORDDB。|
|ILC_COLOR4|使用4位（16色）與裝置無關的點陣圖（DIB）區段做為影像清單的點陣圖。|
|ILC_COLOR8|使用8位 DIB 區段。 色彩表所使用的色彩與半色調調色板的色彩相同。|
|ILC_COLOR16|使用16位（32/64k 色彩） DIB 區段。|
|ILC_COLOR24|使用24位 DIB 區段。|
|ILC_COLOR32|使用32位 DIB 區段。|
|ILC_COLORDDB|使用裝置相依點陣圖。|
|ILC_MASK|使用遮罩。 影像清單包含兩個位圖，其中一個是用來做為遮罩的單色點陣圖。 如果未包含此值，則影像清單只會包含一個點陣圖。 如需遮罩影像的詳細資訊，請參閱[從影像清單繪製影像](../../mfc/drawing-images-from-an-image-list.md)。|

*nInitial*<br/>
影像清單一開始所包含的影像數目。

*nGrow*<br/>
當系統需要調整清單大小以騰出空間給新影像時，影像清單可成長的影像數目。 此參數代表已調整大小之影像清單可包含的新映射數目。

*nBitmapID*<br/>
要與影像清單相關聯之點陣圖的資源識別碼。

*crMask*<br/>
用來產生遮罩的色彩。 此色彩在指定點陣圖中的每個圖元都會變更為黑色，且遮罩中的對應位會設定為一。

*lpszBitmapID*<br/>
包含影像資源識別碼的字串。

*imagelist1*<br/>
`CImageList` 物件的參考。

*nImage1*<br/>
第一個現有影像的索引。

*imagelist2*<br/>
`CImageList` 物件的參考。

*nImage2*<br/>
第二個現有影像的索引。

*dx*<br/>
第二個影像 X 軸與第一個影像之間的位移（以圖元為單位）。

*dy*<br/>
第二個影像 y 軸與第一個影像之間的位移（以圖元為單位）。

*pImageList*<br/>
`CImageList` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用兩個步驟來建立 `CImageList`。 首先，呼叫此函式，然後呼叫 `Create`，它會建立影像清單，並將它附加至 `CImageList` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>CImageList：:D eleteImageList

呼叫此函式可刪除影像清單。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>CImageList：:D eleteTempMap

由 `CWinApp` 閒置時間處理常式自動呼叫，`DeleteTempMap` 會刪除[FromHandle](#fromhandle)所建立的任何暫存 `CImageList` 物件，但不會損毀任何與 `ImageList` 物件暫時關聯的控制碼（`hImageList`）。

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>CImageList：:D etach

呼叫此函式可從 `CImageList` 物件卸離影像清單物件。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>傳回值

影像清單物件的控制碼。

### <a name="remarks"></a>備註

此函式會傳回影像清單物件的控制碼。

### <a name="example"></a>範例

  請參閱[CImageList：： Attach](#attach)的範例。

##  <a name="dragenter"></a>CImageList：:D ragEnter

在拖曳作業期間，會鎖定*pWndLock*指定之視窗的更新，並在*point*指定的位置顯示拖曳影像。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
擁有拖曳影像之視窗的指標。

*此處*<br/>
要顯示拖曳影像的位置。 座標相對於視窗的左上角（而非工作區）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

座標相對於視窗的左上角，因此在指定座標時，您必須補償視窗元素的寬度，例如框線、標題列和功能表列。

如果*pWndLock*為 Null，則此函式會在與桌面視窗相關聯的顯示內容中繪製影像，而座標則是相對於螢幕的左上角。

此函式會在拖曳作業期間鎖定指定之視窗的所有其他更新。 如果您需要在拖曳作業期間執行任何繪圖，例如反白顯示拖放作業的目標，您可以使用[CImageList：:D ragleave](#dragleave)函式，暫時隱藏拖曳的影像。

### <a name="example"></a>範例

  請參閱[CImageList：： BeginDrag](#begindrag)的範例。

##  <a name="dragleave"></a>CImageList：:D ragLeave

解除鎖定*pWndLock*所指定的視窗，並隱藏拖曳影像，允許更新視窗。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
擁有拖曳影像之視窗的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CImageList：： EndDrag](#enddrag)的範例。

##  <a name="dragmove"></a>CImageList：:D ragMove

呼叫此函式可在拖放作業期間移動正在拖曳的影像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
新的拖曳位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

通常會呼叫這個函式來回應 WM_MOUSEMOVE 訊息。 若要開始拖曳作業，請使用 `BeginDrag` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>CImageList：:D ragShowNolock

在拖曳作業期間顯示或隱藏拖曳影像，而不會鎖定視窗。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定是否要顯示拖曳影像。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

[CImageList：:D ragenter](#dragenter)函式會在拖曳作業期間鎖定視窗的所有更新。 不過，此函數不會鎖定視窗。

##  <a name="draw"></a>CImageList：:D raw

呼叫此函式可繪製在拖放作業期間所拖曳的影像。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*pDC*<br/>
目的地裝置內容的指標。

*nImage*<br/>
要繪製之影像的以零為基底的索引。

*pt*<br/>
要在指定的裝置內容中繪製的位置。

*nStyle*<br/>
指定繪製樣式的旗標。 它可以是下列其中一個或多個值：

|值|意義|
|-----------|-------------|
|ILD_BLEND25，ILD_FOCUS|繪製影像，並以系統醒目提示色彩來混合25%。 如果影像清單不包含遮罩，此值就不會有任何作用。|
|ILD_BLEND50、ILD_SELECTED、ILD_BLEND|繪製影像，並以系統醒目提示色彩來混合50%。 如果影像清單不包含遮罩，此值就不會有任何作用。|
|ILD_MASK|繪製遮罩。|
|ILD_NORMAL|使用影像清單的背景色彩繪製影像。 如果背景色彩是 CLR_NONE 值，則會使用遮罩以透明的方式繪製影像。|
|ILD_TRANSPARENT|使用遮罩以透明方式繪製影像，而不論背景色彩為何。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CImageList：： SetOverlayImage](#setoverlayimage)的範例。

##  <a name="drawex"></a>CImageList：:D rawEx

在指定的裝置內容中繪製影像清單專案。

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*pDC*<br/>
目的地裝置內容的指標。

*nImage*<br/>
要繪製之影像的以零為基底的索引。

*pt*<br/>
要在指定的裝置內容中繪製的位置。

*sz*<br/>
相對於影像左上角繪製之影像部分的大小。 請參閱 Windows SDK 中[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)的*dx*和*dy* 。

*clrBk*<br/>
影像的背景色彩。 請參閱 Windows SDK [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbBk* 。

*clrFg*<br/>
影像的前景色彩。 請參閱 Windows SDK [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbFg* 。

*nStyle*<br/>
指定繪製樣式的旗標。 請參閱 Windows SDK [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*fStyle* 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

函式會使用指定的繪製樣式，並將影像與指定的色彩混合。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>CImageList：:D rawIndirect

呼叫這個成員函式，從影像清單中繪製影像。

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>參數

*pimldp*<br/>
[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的指標，其中包含繪製作業的相關資訊。

*pDC*<br/>
目的地裝置內容的指標。 當您完成此[CDC](../../mfc/reference/cdc-class.md)物件時，必須將其刪除。

*nImage*<br/>
要繪製之影像的以零為起始的索引。

*pt*<br/>
包含將繪製影像之 x 和 y 座標的[點](/previous-versions/dd162805\(v=vs.85\))結構。

*sz*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)結構，指出要繪製的影像大小。

*ptOrigin*<br/>
包含 x 和 y 座標的[POINT](/previous-versions/dd162805\(v=vs.85\))結構，指定相對於影像本身的繪圖作業的左上角。 不會繪製位於 x 座標左邊且高於 y 座標的影像圖元。

*fStyle*<br/>
指定繪製樣式的旗標，並可選擇是否要重迭影像。 如需覆迭影像的詳細資訊，請參閱備註一節。 MFC 預設實作為 ILD_NORMAL，會使用影像清單的背景色彩繪製影像。 如果背景色彩是 CLR_NONE 值，則會使用遮罩以透明的方式繪製影像。

[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的*fStyle*成員底下會描述其他可能的樣式。

*dwRop*<br/>
指定點陣操作程式碼的值。 這些程式碼會定義來源矩形的色彩資料如何與目的地矩形的色彩資料結合，以達到最終色彩。 MFC 的預設實 SRCCOPY 會將來源矩形直接複製到目的地矩形。 如果*fStyle*參數不包含 ILD_ROP 旗標，則會忽略這個參數。

[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的*dwRop*成員底下會描述其他可能的值。

*rgbBack*<br/>
預設 CLR_DEFAULT 影像背景色彩。 這個參數可以是應用程式定義的 RGB 值或下列其中一個值：

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|預設背景色彩。 影像會使用影像清單背景色彩繪製。|
|CLR_NONE|無背景色彩。 影像會以透明的方式繪製。|

*rgbFore*<br/>
影像前景色彩，預設為 CLR_DEFAULT。 這個參數可以是應用程式定義的 RGB 值或下列其中一個值：

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|預設的前景色彩。 影像會使用系統反白顯示色彩做為前景色彩來繪製。|
|CLR_NONE|無 blend 色彩。 影像會與目的地裝置內容的色彩混合。|

只有在*fStyle*包含 ILD_BLEND25 或 ILD_BLEND50 旗標時，才會使用這個參數。

*fState*<br/>
指定繪製狀態的旗標。 這個成員可以包含一或多個影像清單狀態旗標。

*Frame*<br/>
會影響飽和和 Alpha 混合效果的行為。

與 ILS_SATURATE 搭配使用時，這個成員會保留新增至圖示中每個圖元之 RGB 三元的每個色彩元件的值。

與 ILS_APLHA 搭配使用時，這個成員會保存 Alpha 色板的值。 這個值可以是0到255，0是完全透明，而255則完全不透明。

*crEffect*<br/>
用於發光和陰影效果的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="return-value"></a>傳回值

如果成功繪製影像，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果您想要自行填入 Win32 結構，請使用第一個版本。 如果您想要利用 MFC 的一或多個預設引數，或避免管理結構，請使用第二個版本。

重迭影像是在主要影像之上繪製的影像，由*nImage*參數在此成員函式中指定。 使用[draw](#draw)成員函式，搭配使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏指定之覆迭遮罩的以一為基的索引，繪製覆迭遮罩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>CImageList：： EndDrag

呼叫此函式以結束拖曳作業。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>備註

若要開始拖曳作業，請使用 `BeginDrag` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>CImageList：： ExtractIcon

呼叫此函式可根據影像清單中的影像和其相關遮罩來建立圖示。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>參數

*nImage*<br/>
以零為基底的影像索引。

### <a name="return-value"></a>傳回值

如果成功，則為圖示的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個方法會依賴[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏的行為來建立圖示。 如需有關建立和清除圖示的詳細資訊，請參閱[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>CImageList：： FromHandle

當提供影像清單的控制碼時，傳回 `CImageList` 物件的指標。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
指定影像清單。

### <a name="return-value"></a>傳回值

如果成功，則為 `CImageList` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CImageList` 尚未附加至控制碼，則會建立並附加暫存 `CImageList` 物件。 只有在下一次應用程式的事件迴圈中有閒置時間時，才會將此暫存 `CImageList` 物件有效，此時所有暫存物件都會遭到刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>CImageList：： FromHandlePermanent

當提供影像清單的控制碼時，傳回 `CImageList` 物件的指標。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
指定影像清單。

### <a name="return-value"></a>傳回值

如果成功，則為 `CImageList` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CImageList` 物件未附加至控制碼，則會傳回 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>CImageList：： GetBkColor

呼叫此函式可取得影像清單的目前背景色彩。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

`CImageList` 物件背景色彩的 RGB 色彩值。

### <a name="example"></a>範例

  請參閱[CImageList：： SetBkColor](#setbkcolor)的範例。

##  <a name="getdragimage"></a>CImageList：： GetDragImage

取得用於拖曳的暫存影像清單。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>參數

*lpPoint*<br/>
接收目前拖曳位置之[點](/previous-versions/dd162805\(v=vs.85\))結構的位址。

*lpPointHotSpot*<br/>
接收相對於拖曳位置之拖曳影像位移的 `POINT` 結構的位址。

### <a name="return-value"></a>傳回值

如果成功，則為用於拖曳之暫存影像清單的指標;否則為 Null。

##  <a name="getimagecount"></a>CImageList：： GetImageCount

呼叫此函式可取得影像清單中的影像數目。

```
int GetImageCount() const;
```

### <a name="return-value"></a>傳回值

影像的數目。

### <a name="example"></a>範例

  請參閱[CImageList：： ExtractIcon](#extracticon)的範例。

##  <a name="getimageinfo"></a>CImageList：： GetImageInfo

呼叫此函式可取得影像的相關資訊。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>參數

*nImage*<br/>
以零為基底的影像索引。

*pImageInfo*<br/>
接收影像相關資訊之[IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo)結構的指標。 此結構中的資訊可以用來直接操作影像的點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`IMAGEINFO` 結構包含影像清單中影像的相關資訊。

##  <a name="getsafehandle"></a>CImageList：： GetSafeHandle

呼叫此函式可抓取 `m_hImageList` 的資料成員。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>傳回值

附加影像清單的控制碼;如果未附加任何物件，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>CImageList：： m_hImageList

附加至此物件之影像清單的控制碼。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>備註

`m_hImageList` 資料成員是 HIMAGELIST 類型的公用變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>CImageList：： operator HIMAGELIST

使用這個運算子來取得 `CImageList` 物件的附加控制碼。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為 `CImageList` 物件所表示之影像清單的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子，可支援直接使用 HIMAGELIST 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>CImageList：： Read

呼叫此函式可從封存讀取影像清單。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*pArchive*<br/>
要從中讀取影像清單之 `CArchive` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>CImageList：： Remove

呼叫此函式可從影像清單物件移除影像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要移除之影像的以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*NImage*之後的所有專案現在會向下移動一個位置。 例如，如果影像清單包含兩個專案，刪除第一個專案會使其餘專案現在位於第一個位置。 *nImage*= 0，代表第一個位置的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>CImageList：： Replace

呼叫此函式，以新的影像取代影像清單中的影像。

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要取代之影像的以零為基底的索引。

*pbmImage*<br/>
包含影像之點陣圖的指標。

*pbmMask*<br/>
包含遮罩之點陣圖的指標。 如果沒有與影像清單搭配使用的遮罩，則會忽略這個參數。

*hIcon*<br/>
圖示的控制碼，其中包含新影像的點陣圖和遮罩。

### <a name="return-value"></a>傳回值

傳回 BOOL 的版本會在成功時傳回非零值;否則為0。

傳回**int**的版本會在成功時傳回影像以零為起始的索引;否則為-1。

### <a name="remarks"></a>備註

呼叫[SetImageCount](#setimagecount)將新的有效影像指派給預留位置影像索引編號之後，呼叫這個成員函式。

### <a name="example"></a>範例

  請參閱[CImageList：： SetImageCount](#setimagecount)的範例。

##  <a name="setbkcolor"></a>CImageList：： SetBkColor

呼叫此函式可設定影像清單的背景色彩。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>參數

*符*<br/>
要設定的背景色彩。 它可以 CLR_NONE。 在此情況下，會使用遮罩以透明的方式繪製影像。

### <a name="return-value"></a>傳回值

如果成功，則為先前的背景色彩;否則 CLR_NONE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>CImageList：： SetDragCursorImage

藉由結合指定的影像（通常是滑鼠游標影像）與目前的拖曳影像，建立新的拖曳影像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*nDrag*<br/>
要與拖曳影像合併之新影像的索引。

*ptHotSpot*<br/>
新影像中的作用點位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

因為拖曳函式會在拖曳作業期間使用新的影像，所以您應該在呼叫 `CImageList::SetDragCursorImage`之後，使用 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor)函式來隱藏實際的滑鼠游標。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。

##  <a name="setimagecount"></a>CImageList：： SetImageCount

呼叫這個成員函式，以重設 `CImageList` 物件中的影像數目。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>參數

*uNewCount*<br/>
值，指定影像清單中新的影像總數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果您呼叫此成員函式來增加影像清單中的影像數目，則請針對每個額外的映射呼叫[Replace](#replace) ，將新的索引指派給有效的影像。 如果您無法將索引指派給有效的影像，則建立新映射的繪製作業將會無法預測。

如果您使用此函式減少影像清單的大小，則會釋放截斷的影像。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>CImageList：： SetOverlayImage

呼叫此函式可將影像以零為基底的索引新增至要當做覆迭遮罩使用的影像清單。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>參數

*nImage*<br/>
影像的以零為基底的索引，用來做為覆迭遮罩。

*nOverlay*<br/>
覆迭遮罩的以一為基的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

最多可以將四個索引加入至清單中。

覆迭遮罩是以透明方式繪製在另一個影像上的影像。 藉由使用[CImageList：:D raw](#draw)成員函式，以及使用 INDEXTOOVERLAYMASK 宏指定之覆迭遮罩的以一為基的索引，在影像上繪製覆迭遮罩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>CImageList：： Write

呼叫此函式可將影像清單物件寫入封存。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*pArchive*<br/>
要儲存影像清單的 `CArchive` 物件指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)
