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
ms.openlocfilehash: 2fc92858f84826e2b953fcbc9de020741e97b007
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346362"
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
|[CImageList::CImageList](#cimagelist)|建構 `CImageList` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CImageList::Add](#add)|將映像或映像加入至影像清單中。|
|[CImageList::Attach](#attach)|附加至影像清單`CImageList`物件。|
|[CImageList::BeginDrag](#begindrag)|開始拖曳影像。|
|[CImageList::Copy](#copy)|將映像內複製`CImageList`物件。|
|[CImageList::Create](#create)|初始化的映像清單，並將它附加至`CImageList`物件。|
|[CImageList::DeleteImageList](#deleteimagelist)|刪除映像清單。|
|[CImageList::DeleteTempMap](#deletetempmap)|由呼叫[CWinApp](../../mfc/reference/cwinapp-class.md)閒置時間處理常式，以刪除任何暫存`CImageList`所建立的物件`FromHandle`。|
|[CImageList::Detach](#detach)|從影像清單物件中斷連結`CImageList`物件，並傳回影像清單的控制代碼。|
|[CImageList::DragEnter](#dragenter)|在拖曳作業期間鎖定更新，並顯示拖曳影像的指定位置。|
|[CImageList::DragLeave](#dragleave)|解除鎖定 視窗，並隱藏拖曳影像，以便可以更新  視窗。|
|[CImageList::DragMove](#dragmove)|將拖放作業期間被拖曳的影像。|
|[CImageList::DragShowNolock](#dragshownolock)|顯示或隱藏在拖曳作業時，拖曳影像，而不需要鎖定的視窗。|
|[CImageList::Draw](#draw)|繪製拖放作業期間被拖曳的影像。|
|[CImageList::DrawEx](#drawex)|在指定的裝置內容中繪製的映像清單項目。 函式會使用指定的繪製樣式，並混合的映像，以指定的色彩。|
|[CImageList::DrawIndirect](#drawindirect)|從影像清單中繪製影像。|
|[CImageList::EndDrag](#enddrag)|結束拖曳作業。|
|[CImageList::ExtractIcon](#extracticon)|會建立為基礎的影像和遮罩影像清單中的圖示。|
|[CImageList::FromHandle](#fromhandle)|將指標傳回至`CImageList`物件時指定映像清單的控制代碼。 如果 `CImageList` 物件沒有附加至控制代碼，會建立並附加暫存 `CImageList` 物件。|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|將指標傳回至`CImageList`物件時指定映像清單的控制代碼。 如果`CImageList`物件沒有附加至控制代碼，則會傳回 NULL。|
|[CImageList::GetBkColor](#getbkcolor)|擷取目前的背景色彩，影像清單。|
|[CImageList::GetDragImage](#getdragimage)|取得用於拖曳的暫存影像清單。|
|[CImageList::GetImageCount](#getimagecount)|擷取映像清單中的映像數目。|
|[CImageList::GetImageInfo](#getimageinfo)|擷取映像的相關資訊。|
|[CImageList::GetSafeHandle](#getsafehandle)|擷取`m_hImageList`。|
|[CImageList::Read](#read)|從封存讀取影像清單。|
|[CImageList::Remove](#remove)|從影像清單中移除映像。|
|[CImageList::Replace](#replace)|利用新影像取代影像清單中的映像。|
|[CImageList::SetBkColor](#setbkcolor)|設定影像清單的背景色彩。|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|建立新的拖曳影像。|
|[CImageList::SetImageCount](#setimagecount)|重設影像清單中的映像的計數。|
|[CImageList::SetOverlayImage](#setoverlayimage)|將映像當做覆疊遮罩清單中的影像之以零為起始的索引。|
|[CImageList::Write](#write)|寫入封存中的影像清單。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|傳回 HIMAGELIST 附加至`CImageList`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|包含附加至這個物件的影像清單控制代碼。|

## <a name="remarks"></a>備註

「 映像清單 」 是相同大小的影像，其中每一個可以參考其以零為起始的索引集合。 影像清單用來有效管理大量圖示或點陣圖。 影像清單中的所有映像都包含在單一的寬點陣圖螢幕裝置格式。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 Microsoft Win32 應用程式發展介面 (API) 提供可讓您繪製影像、 建立和終結影像清單、 加入和移除映像、 取代影像、 合併映像，以及拖曳影像的影像清單函式。

這個控制項 (並因此`CImageList`類別) 僅適用於 Windows 95/98 和 Windows NT 版 3.51 下執行的程式和更新版本。

如需有關使用`CImageList`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="add"></a>  CImageList::Add

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
包含的映像或映像的點陣圖的指標。 從點陣圖的寬度推斷的映像數目。

*pbmMask*<br/>
包含遮罩點陣圖的指標。 如果沒有遮罩搭配使用影像清單中，會忽略這個參數。

*crMask*<br/>
用來產生遮罩的色彩。 此色彩在指定的點陣圖中的每個像素會變更為黑色，且對應的位元遮罩中設為其中一個。

*hIcon*<br/>
包含點陣圖和新的映像的遮罩之圖示的控制代碼。

### <a name="return-value"></a>傳回值

如果成功，第一個新影像的以零起始的索引否則為-1。

### <a name="remarks"></a>備註

您必須負責與它完成時釋放圖示控制代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

呼叫此函式來附加至影像清單`CImageList`物件。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
影像清單物件的控制代碼。

### <a name="return-value"></a>傳回值

如果附件已成功則為非零否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

呼叫此函式以開始拖曳影像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要拖曳之影像的以零為起始的索引。

*ptHotSpot*<br/>
開始拖曳位置 （通常，資料指標位置） 座標。 座標是相對於映像的左上角。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式建立暫存的映像清單，其中用於拖曳。 映像會將指定的映像和其遮罩結合目前的游標。 在後續的 WM_MOUSEMOVE 訊息回應，您可以利用移動拖曳影像`DragMove`成員函式。 若要結束拖曳作業，您可以使用`EndDrag`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

建構 `CImageList` 物件。

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

此成員函式實作的 Win32 函式行為[ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy)、 Windows SDK 中所述。

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
要做為複製作業的目的地使用之影像的以零為起始的索引。

*iSrc*<br/>
要做為複製作業的來源映像的以零為起始的索引。

*uFlags*<br/>
位元旗標值，指定要進行複製作業的類型。 這個參數可以是下列值之一：

|值|意義|
|-----------|-------------|
|ILCF_MOVE|來源影像會複製到目的端影像的索引。 這項作業會產生指定之影像的多個執行個體。 預設值為 ILCF_MOVE。|
|ILCF_SWAP|來源和目的地影像交換內的影像清單的位置。|

*pSrc*<br/>
指標`CImageList`複製作業的目標物件。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

初始化的映像清單，並將它附加至[CImageList](../../mfc/reference/cimagelist-class.md)物件。

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
每個影像，像素為單位的維度。

*cy*<br/>
每個影像，像素為單位的維度。

*nFlags*<br/>
指定要建立的映像清單的類型。 這個參數可以是下列值的組合，但它可以包含的其中之一`ILC_COLOR`值。

|值|意義|
|-----------|-------------|
|ILC_COLOR|如果不指定任何其他 ILC_COLOR * 旗標，請使用預設的行為。 一般而言，預設值是 ILC_COLOR4;但是舊版的顯示驅動程式的預設值是 ILC_COLORDDB。|
|ILC_COLOR4|點陣圖的 4 位元 （16 個色彩） 與裝置無關點陣圖 (DIB) 區段用於映像清單。|
|ILC_COLOR8|使用 8 位元 DIB 區段。 Color 資料表所用的色彩會是相同的色彩為半色調調色盤。|
|ILC_COLOR16|使用 16 位元 (32/64 k 色彩) DIB 區段。|
|ILC_COLOR24|使用 24 位元 DIB 區段。|
|ILC_COLOR32|使用 32 位元 DIB 區段。|
|ILC_COLORDDB|使用裝置相關點陣圖。|
|ILC_MASK|會使用遮罩。 影像清單包含兩個點陣圖，其中之一就是當做遮罩的單色點陣圖。 如果這個值就不會包含，映像清單會包含只有一個點陣圖。 請參閱[繪圖映像，從影像清單](../../mfc/drawing-images-from-an-image-list.md)的遮罩的映像上的其他資訊。|

*nInitial*<br/>
一開始包含影像清單的影像數目。

*nGrow*<br/>
供系統需要調整大小的清單，以騰出空間給新的映像時所能成長的影像清單的映像數目。 此參數表示新的映像調整大小的影像清單可包含的數目。

*nBitmapID*<br/>
點陣圖的資源識別碼相關聯的映像清單。

*crMask*<br/>
用來產生遮罩的色彩。 每個像素中指定的點陣圖這個色彩變更為黑色，以及對應的位元遮罩中設為其中一個。

*lpszBitmapID*<br/>
字串，包含資源的映像的識別碼。

*imagelist1*<br/>
對 `CImageList` 物件的參考。

*nImage1*<br/>
第一個現有的映像的索引。

*imagelist2*<br/>
對 `CImageList` 物件的參考。

*nImage2*<br/>
第二個現有的映像的索引。

*dx*<br/>
第二個影像像素為單位中的第一個映像的關聯性中的 x 軸的位移。

*dy*<br/>
第二個影像像素為單位中的第一個映像的關聯性中的 y 軸的位移。

*pImageList*<br/>
`CImageList` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您建構`CImageList`兩個步驟。 首先，呼叫建構函式，然後呼叫`Create`，這會建立映像清單，並將它附加至`CImageList`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

呼叫此函式來刪除影像清單。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

會自動呼叫`CWinApp`閒置時間處理常式中，`DeleteTempMap`刪除暫時`CImageList`所建立的物件[FromHandle](#fromhandle)，但不會終結任何控制代碼 ( `hImageList`) 暫時相關聯使用`ImageList`物件。

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

呼叫此函式可卸離從影像清單物件`CImageList`物件。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>傳回值

影像清單物件的控制代碼。

### <a name="remarks"></a>備註

此函式傳回的控制代碼的影像清單物件。

### <a name="example"></a>範例

  映像的背景色彩，根據預設[CImageList::Attach](#attach)。

##  <a name="dragenter"></a>  CImageList::DragEnter

在拖曳作業時，會鎖定更新所指定視窗*pWndLock* ，並顯示所指定的位置拖曳影像*點*。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
主控視窗的拖曳影像的指標。

*point*<br/>
用來顯示拖曳影像的位置。 座標是相對於視窗 （而非工作區） 的左上角。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

座標是相對於視窗左上角，因此您必須在指定座標時補償視窗項目，例如框線、 標題列和功能表列的寬度。

如果*pWndLock*是 NULL，此函式與桌面視窗中，相關聯的顯示內容中繪製的影像，而且座標是相對於螢幕左上角。

此函式在拖曳作業期間鎖定特定視窗的所有其他更新。 如果您需要在拖曳作業期間進行繪圖，例如反白顯示拖放作業的目標，您可以使用 [CImageList::DragLeave](#dragleave) 成員函式暫時隱藏被拖曳的影像。

### <a name="example"></a>範例

  範例，請參閱[CImageList::BeginDrag](#begindrag)。

##  <a name="dragleave"></a>  CImageList::DragLeave

解除鎖定所指定視窗*pWndLock*並隱藏拖曳影像，讓 [更新] 視窗。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
主控視窗的拖曳影像的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CImageList::EndDrag](#enddrag)。

##  <a name="dragmove"></a>  CImageList::DragMove

呼叫此函式將拖放作業期間被拖曳的影像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
新的拖曳位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

回應 WM_MOUSEMOVE 訊息通常會呼叫此函數。 若要開始拖曳作業，請使用`BeginDrag`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

顯示或隱藏在拖曳作業時，拖曳影像，而不需要鎖定的視窗。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定是否要顯示的拖曳影像。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

[CImageList::DragEnter](#dragenter)函式在拖曳作業期間會鎖定至視窗的所有更新。 不過，此函式，不會鎖定視窗。

##  <a name="draw"></a>  CImageList::Draw

呼叫此函式可繪製拖放作業期間被拖曳的影像。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*pDC*<br/>
目的地裝置內容指標。

*nImage*<br/>
要繪製影像的以零為起始索引。

*pt*<br/>
在其中繪製指定的裝置內容中的位置。

*nStyle*<br/>
旗標，指定繪製樣式。 它可以是下列其中一個或多個這些值：

|值|意義|
|-----------|-------------|
|ILD_BLEND25 ILD_FOCUS|繪製影像，混合使用系統醒目提示色彩的 25%。 如果影像清單不包含遮罩，這個值會有任何作用。|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|繪製影像，混用 50%的系統反白顯示色彩。 如果影像清單不包含遮罩，這個值會有任何作用。|
|ILD_MASK|繪製遮罩。|
|ILD_NORMAL|繪製影像的影像清單中使用的背景色彩。 如果背景色彩為 CLR_NONE 值，以透明的方式使用遮罩繪製影像。|
|ILD_TRANSPARENT|使用影像繪製無障礙地遮罩，不論的背景色彩。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  範例，請參閱[cimagelist:: Setoverlayimage](#setoverlayimage)。

##  <a name="drawex"></a>  CImageList::DrawEx

在指定的裝置內容中繪製的映像清單項目。

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
目的地裝置內容指標。

*nImage*<br/>
要繪製影像的以零為起始索引。

*pt*<br/>
在其中繪製指定的裝置內容中的位置。

*sz*<br/>
要繪製影像左上角相對的影像部分的大小。 請參閱*dx*並*dy*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*clrBk*<br/>
映像的背景色彩。 請參閱*rgbBk*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*clrFg*<br/>
映像的前景色彩。 請參閱*rgbFg*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*nStyle*<br/>
旗標，指定繪製樣式。 請參閱*fStyle*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

函式會使用指定的繪製樣式，並混合的映像，以指定的色彩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

呼叫此成員函式，從影像清單中繪製影像。

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
指標[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)結構，其中包含繪製作業的相關資訊。

*pDC*<br/>
目的地裝置內容指標。 您必須刪除這[CDC](../../mfc/reference/cdc-class.md)物件時完成它。

*nImage*<br/>
要繪製之影像的以零為起始的索引。

*pt*<br/>
A[點](/previous-versions/dd162805\(v=vs.85\))結構，包含 x 和 y 座標會繪製影像的位置。

*sz*<br/>
A[大小](/windows/desktop/api/windef/ns-windef-tagsize)結構表示要繪製影像的大小。

*ptOrigin*<br/>
A[點](/previous-versions/dd162805\(v=vs.85\))結構，包含 x 和 y 座標指定相對於映像本身繪圖作業的左上的角。 不會繪製像素的影像左側的 x 座標和 y 軸上方。

*fStyle*<br/>
旗標，指定繪製樣式，並選擇性地覆疊影像。 在覆疊影像，請參閱 < 備註 > 小節，以取得資訊。 MFC 的預設實作，ILD_NORMAL，繪製影像的影像清單中使用的背景色彩。 如果背景色彩為 CLR_NONE 值，以透明的方式使用遮罩繪製影像。

其他可能的樣式會下所述*fStyle*隸屬[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)結構。

*dwRop*<br/>
值，指定的點陣作業程式碼。 這些程式碼會定義來源矩形的色彩資料以達到完稿色彩的目的矩形的色彩資料的合併方式。 MFC 的預設實作，SRCCOPY，會將來源矩形複製直接到目的地矩形。 如果這個參數就會忽略*fStyle*參數不包含 ILD_ROP 旗標。

其他可能的值會描述於*dwRop*隸屬[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)結構。

*rgbBack*<br/>
影像背景色彩，依預設 CLR_DEFAULT。 這個參數可以是應用程式定義的 RGB 值，或下列值之一：

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|預設背景色彩。 使用影像清單的背景色彩繪製影像。|
|CLR_NONE|沒有背景色彩。 以透明方式繪製影像。|

*rgbFore*<br/>
映像前景色彩，依預設 CLR_DEFAULT。 這個參數可以是應用程式定義的 RGB 值，或下列值之一：

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|預設前景色彩。 使用系統醒目提示色彩為前景色彩來繪製影像。|
|CLR_NONE|無 blend 色彩。 映像會與目的地裝置內容的色彩混合。|

使用這個參數才*fStyle*包含了 ILD_BLEND25 或 ILD_BLEND50 旗標。

*fState*<br/>
旗標，指定繪製的狀態。 這個成員可以包含一或多個映像清單狀態旗標。

*Frame*<br/>
會影響 saturate 和 alpha 透明混色效果的行為。

ILS_SATURATE 搭配使用時，此成員會包含加入至 RGB 三物件組，每個像素圖示中每個色彩元件的值。

ILS_APLHA 搭配使用時，這個成員會保留 alpha 色頻值。 這個值可以從 0 到 255 之間，與 0 完全透明，而 255 是完全不透明。

*crEffect*<br/>
A [COLORREF](/windows/desktop/gdi/colorref)光暈和陰影效果所使用的值。

### <a name="return-value"></a>傳回值

如果成功繪製影像，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

如果您想要自行填入 Win32 結構，請使用第一個版本。 如果您想要利用一或多個 MFC 的預設引數，或避免管理結構，請使用第二個版本。

覆疊影像是繪製主要映像，此成員函式中指定的映像*n*參數。 藉由繪製覆疊遮罩[繪製](#draw)成員函式，以一起始的索引，使用指定的覆疊遮罩[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

呼叫此函式來結束拖曳作業。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>備註

若要開始拖曳作業，請使用`BeginDrag`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

呼叫此函式可建立基礎的映像和其相關的遮罩影像清單中的圖示。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>參數

*nImage*<br/>
影像的以零為起始的索引。

### <a name="return-value"></a>傳回值

如果成功則之圖示的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

這個方法依賴的行為[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)巨集來建立圖示。 請參閱[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)巨集，如需有關圖示建立和清除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

將指標傳回至`CImageList`物件時指定映像清單的控制代碼。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
指定映像清單。

### <a name="return-value"></a>傳回值

指標`CImageList`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果`CImageList`尚未附加至控制代碼，暫存`CImageList`建立物件並將其連結。 此暫存`CImageList`物件是否有效，僅直到下一次應用程式在其事件迴圈中有閒置的時間，屆時所有暫存物件已刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

將指標傳回至`CImageList`物件時指定映像清單的控制代碼。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*hImageList*<br/>
指定映像清單。

### <a name="return-value"></a>傳回值

指標`CImageList`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果`CImageList`物件沒有附加至控制代碼，則會傳回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

呼叫此函式可擷取目前的背景色彩，影像清單。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

RGB 色彩值`CImageList`物件背景色彩。

### <a name="example"></a>範例

  範例，請參閱[CImageList::SetBkColor](#setbkcolor)。

##  <a name="getdragimage"></a>  CImageList::GetDragImage

取得用於拖曳的暫存影像清單。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>參數

*lpPoint*<br/>
位址[點](/previous-versions/dd162805\(v=vs.85\))結構會接收目前拖曳位置。

*lpPointHotSpot*<br/>
位址`POINT`結構會接收拖曳影像相對於拖曳位置的位移。

### <a name="return-value"></a>傳回值

如果成功，指向暫存的映像的清單，用於拖曳;否則為 NULL。

##  <a name="getimagecount"></a>  CImageList::GetImageCount

呼叫此函式可擷取的映像清單中的映像數目。

```
int GetImageCount() const;
```

### <a name="return-value"></a>傳回值

映像數目。

### <a name="example"></a>範例

  範例，請參閱[CImageList::ExtractIcon](#extracticon)。

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

呼叫此函式來擷取映像的相關資訊。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>參數

*nImage*<br/>
影像的以零為起始的索引。

*pImageInfo*<br/>
指標[IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo)接收映像的相關資訊的結構。 在此結構中的資訊可用來直接操作影像的點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`IMAGEINFO`結構包含影像清單中的映像的相關資訊。

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

呼叫此函式可擷取`m_hImageList`資料成員。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>傳回值

附加的影像清單控制代碼如果附加的物件，否則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

影像清單附加到這個物件的控制代碼。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>備註

`m_hImageList`資料成員是型別 HIMAGELIST 的公用變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

若要取得的連接控制代碼使用這個運算子`CImageList`物件。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>傳回值

如果成功，影像清單的控制代碼所表示`CImageList`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用 HIMAGELIST 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

呼叫此函式可從封存讀取影像清單。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*pArchive*<br/>
指標`CArchive`從中影像清單是要讀取的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

呼叫此函式來移除映像清單物件中的映像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要移除之影像的以零為起始的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

之後的所有項目*n*現在向下移動一個位置。 比方說，如果影像清單包含兩個項目，刪除第一個項目會導致要現在是在第一個位置中的其餘項目。 *n*= 0 中的第一個位置的項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

呼叫此函式可利用新影像取代影像清單中的映像。

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
要取代之影像的以零為起始的索引。

*pbmImage*<br/>
指標，包含影像的點陣圖。

*pbmMask*<br/>
包含遮罩點陣圖指標。 如果沒有遮罩搭配使用影像清單中，會忽略這個參數。

*hIcon*<br/>
包含點陣圖和新的映像的遮罩之圖示的控制代碼。

### <a name="return-value"></a>傳回值

版本傳回 BOOL 傳回非零值，如果登錄成功。否則為 0。

傳回的版本**int**傳回之影像的以零為起始的索引，如果成功，否則為-1。

### <a name="remarks"></a>備註

呼叫此成員函式之後呼叫[SetImageCount](#setimagecount)若要指派新項目，有效的映像以預留位置映像索引編號。

### <a name="example"></a>範例

  範例，請參閱[CImageList::SetImageCount](#setimagecount)。

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

呼叫此函式來設定影像清單的背景色彩。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>參數

*cr*<br/>
若要設定的背景色彩。 它可以是 CLR_NONE。 在此情況下，映像會繪製無障礙地使用遮罩。

### <a name="return-value"></a>傳回值

如果成功則前一個背景色彩否則 CLR_NONE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

藉由結合特定的映像 （通常是滑鼠游標影像） 與目前拖曳影像建立新的拖曳影像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*nDrag*<br/>
新的映像，以結合拖曳影像的索引。

*ptHotSpot*<br/>
新的映像中的作用點的位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

由於拖曳函式會使用新的映像，在拖曳作業期間，您應該使用 Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor)函式來呼叫之後隱藏實際滑鼠游標`CImageList::SetDragCursorImage`。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。

##  <a name="setimagecount"></a>  CImageList::SetImageCount

呼叫此成員函式中的映像的數目歸`CImageList`物件。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>參數

*uNewCount*<br/>
指定影像清單中的新映像總數的值。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果您呼叫此成員函式，以增加影像清單中的映像數目，然後呼叫[取代](#replace)將新的索引指派給有效的映像的每一個其他映像。 如果您無法將索引指派給有效的映像，建立新的映像的繪製作業將無法預測。

如果您使用此函式來減少映像清單的大小，會釋放已截斷的映像。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

呼叫此函式可用於覆疊遮罩的映像清單中加入影像之以零為起始的索引。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要使用作為覆疊遮罩的影像的以零為起始索引。

*nOverlay*<br/>
一個基礎覆疊遮罩的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

最多四個索引可以新增至清單。

覆疊遮罩是透過另一個映像以透明方式繪製的映像。 使用影像繪製覆疊遮罩[cimagelist:: Draw](#draw)以一起始的索引，使用 INDEXTOOVERLAYMASK 巨集來指定覆疊遮罩的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

呼叫此函式來寫入封存中的影像清單物件。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*pArchive*<br/>
指標`CArchive`影像清單是要儲存所在的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)
