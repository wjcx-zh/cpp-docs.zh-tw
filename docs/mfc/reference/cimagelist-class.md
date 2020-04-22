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
ms.openlocfilehash: 17cd2a94cb397e59e4622aea8ed7bb6fbe1eee43
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752693"
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
|[CImageList:CImageList](#cimagelist)|建構 `CImageList` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CImageList:新增](#add)|將圖像或圖像添加到圖像清單。|
|[CImage 清單::附加](#attach)|將圖像清單附加到`CImageList`物件。|
|[CImageList::開始拖動](#begindrag)|開始拖動圖像。|
|[CImageList:複製](#copy)|複製`CImageList`物件中的圖像。|
|[CImageList:建立](#create)|初始化圖像清單並將其附加到`CImageList`物件。|
|[CImageList::DeleteImageList](#deleteimagelist)|刪除圖像清單。|
|[CImageList::DeleteTempMap](#deletetempmap)|由[CWinApp](../../mfc/reference/cwinapp-class.md)空閒時間處理程式呼叫以`CImageList``FromHandle`刪除 由創建的任何臨時物件。|
|[CImageList::D埃塔奇](#detach)|從`CImageList`物件分離圖像清單物件,並將句柄返回到圖像清單。|
|[CImageList::D拉格輸入](#dragenter)|鎖定拖動操作期間的更新,並在指定位置顯示拖動圖像。|
|[CImageList::D拉格葉](#dragleave)|解除鎖定視窗並隱藏拖動影像,以便可以更新視窗。|
|[CImageList::D拉格移動](#dragmove)|移動拖放操作期間正在拖動的圖像。|
|[CImageList::D拉格秀諾洛克](#dragshownolock)|在拖動操作期間顯示或隱藏拖動圖像,而不鎖定視窗。|
|[CImageList::D原始](#draw)|繪製拖放操作期間正在拖動的圖像。|
|[CImageList::D原始](#drawex)|在指定的裝置上下文中繪製圖像清單項。 該函數使用指定的繪圖樣式,並將圖像與指定顏色混合。|
|[CImageList::D原始間接](#drawindirect)|從圖像清單中繪製圖像。|
|[CImageList:結束拖動](#enddrag)|結束拖動操作。|
|[CImage 清單::抽取圖示](#extracticon)|以圖像清單中的圖像和蒙版創建圖示。|
|[CImageList:從手處理](#fromhandle)|當為影像清單指定`CImageList`句柄時,傳回指向物件的指標。 如果 `CImageList` 物件沒有附加至控制代碼，會建立並附加暫存 `CImageList` 物件。|
|[CImageList::從永久處理](#fromhandlepermanent)|當為影像清單指定`CImageList`句柄時,傳回指向物件的指標。 如果物件`CImageList`未附加到句柄,則傳回 NULL。|
|[CImageList:取得BkColor](#getbkcolor)|檢索影像清單的當前背景顏色。|
|[CImage 清單::取得拖動影像](#getdragimage)|獲取用於拖動的臨時圖像清單。|
|[CImage 列表:抓取影像計數](#getimagecount)|檢索影像清單中的圖像數。|
|[CImageList:抓取圖片資訊](#getimageinfo)|檢索有關圖像的資訊。|
|[CImageList::取得安全處理](#getsafehandle)|檢索`m_hImageList`。|
|[CImageList:閱讀](#read)|從存檔中讀取影像清單。|
|[CImage 清單::刪除](#remove)|從影像清單中刪除圖像。|
|[CImageList:取代](#replace)|將圖像清單中的圖像替換為新圖像。|
|[CImageList:SetBkColor](#setbkcolor)|設定影像清單的背景顏色。|
|[CImageList::設定DragCursor圖像](#setdragcursorimage)|創建新的拖動圖像。|
|[CImage 清單::設定影像計數](#setimagecount)|重置影像清單中的影像計數。|
|[CImageList::設定疊加影像](#setoverlayimage)|將圖像的零基索引添加到要用作疊加蒙版的圖像清單中。|
|[CImageList:寫入](#write)|將映像清單寫入存檔。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImageList::操作員HIMAGELIST](#operator_himagelist)|返回附加到的`CImageList`HIMAGELIST。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CImageList:m_hImageList](#m_himagelist)|包含附加到此物件的圖像清單的句柄。|

## <a name="remarks"></a>備註

圖像清單"是相同大小的圖像的集合,每個圖像都可以由其零基索引引用。 影像清單用來有效管理大量圖示或點陣圖。 圖像清單中的所有圖像都包含在單個寬幅位圖中,螢幕設備格式為"寬" 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 Microsoft Win32 應用程式程式設計介面 (API) 提供影像清單功能,使您能夠繪製圖像、創建和銷毀影像清單、添加和刪除圖像、替換圖像、合併圖像和拖動影像。

此控制項(因此該`CImageList`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關`CImageList`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList:新增

呼叫此函數以向圖像清單添加一個或多個圖像或圖示。

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
指向包含圖像或圖像的位圖的指標。 圖像數從位圖的寬度推斷出來。

*pbmMask*<br/>
指向包含掩碼的位圖的指標。 如果影像清單不使用掩碼,則忽略此參數。

*crMask*<br/>
用於生成蒙版的顏色。 給定位圖中此顏色的每個圖元都更改為黑色,蒙版中的相應位設置為 1。

*hIcon*<br/>
包含新圖像的點陣圖和蒙版的圖示的句柄。

### <a name="return-value"></a>傳回值

第一個新圖像的零基索引(如果成功);否則 - 1。

### <a name="remarks"></a>備註

完成圖示句柄后,您有責任釋放它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImage 清單::附加

呼叫此函數以將圖像清單附加到`CImageList`物件。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*h 影像清單*<br/>
影像清單物件的句柄。

### <a name="return-value"></a>傳回值

附件成功時非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::開始拖動

調用此函數以開始拖動圖像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*n 影像*<br/>
要拖動的圖像的零索引。

*點熱點*<br/>
起始拖動位置的座標(通常為游標位置)。 坐標相對於圖像的左上角。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函數創建用於拖動的臨時圖像清單。 圖像將指定的圖像及其蒙版與當前游標合併。 為了回應後續WM_MOUSEMOVE消息,可以使用`DragMove`成員函數移動拖動圖像。 要結束拖動操作,可以使用`EndDrag`成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList:CImageList

建構 `CImageList` 物件。

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList:複製

此成員函數實現 Win32 函數[ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)的行為,如 Windows SDK 中所述。

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
用作複製操作目標的圖像的零基索引。

*伊斯爾克*<br/>
用作複製操作源的圖像的零基索引。

*uFlags*<br/>
指定要進行的複本操作類型的位標誌值。 這裡可以是以下值之一:

|值|意義|
|-----------|-------------|
|ILCF_MOVE|源圖像將複製到目標圖像的索引。 此操作會導致給定映射的多個實例。 ILCF_MOVE是預設值。|
|ILCF_SWAP|源圖像和目標圖像交換圖像清單中的位置。|

*pSrc*<br/>
指向`CImageList`物件作為複製操作目標的指標。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList:建立

初始化圖像清單並將其附加到[CImageList](../../mfc/reference/cimagelist-class.md)物件。

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

*殘雪*<br/>
每個圖像的尺寸(以像素為單位)。

*cy*<br/>
每個圖像的尺寸(以像素為單位)。

*nFlags*<br/>
指定要建立的影像清單的類型。 此參數可以是以下值的組合,但它只能包含其中一個`ILC_COLOR`值。

|值|意義|
|-----------|-------------|
|ILC_COLOR|如果未指定其他ILC_COLOR* 標誌,則使用默認行為。 通常,默認值為ILC_COLOR4;則為"ILC_COLOR4"但對於較舊的顯示驅動程式,預設值為ILC_COLORDDB。|
|ILC_COLOR4|使用 4 位元(16 種顏色)與設備無關的點陣圖 (DIB) 部分作為圖像清單的位圖。|
|ILC_COLOR8|使用 8 位元 DIB 部分。 用於顏色表的顏色與半色調調色板的顏色相同。|
|ILC_COLOR16|使用 16 位(32/64k 顏色)DIB 部分。|
|ILC_COLOR24|使用 24 位元 DIB 部分。|
|ILC_COLOR32|使用 32 位 DIB 部分。|
|ILC_COLORDDB|使用與設備相關的點陣圖。|
|ILC_MASK|使用掩碼。 圖像清單包含兩個位圖,其中一個是用作蒙版的單色位圖。 如果未包含此值,則圖像清單僅包含一個位圖。 有關遮罩影像的其他資訊[,請參閱從影像清單中繪製影像](../../mfc/drawing-images-from-an-image-list.md)。|

*n初始*<br/>
圖像清單最初包含的圖像數。

*n 增長*<br/>
當系統需要調整清單大小以為新圖像騰出空間時,圖像清單可以增長的圖像數。 此參數表示調整大小的圖像清單可以包含的新映射數。

*nBitmapID*<br/>
要與圖像清單關聯的位圖的資源指示。

*crMask*<br/>
用於生成蒙版的顏色。 指定點陣圖中此顏色的每個圖元都更改為黑色,蒙版中的相應位設置為 1。

*lpszBitmapID*<br/>
包含影像的資源指示的字串。

*影像清單1*<br/>
`CImageList` 物件的參考。

*nImage1*<br/>
第一個現有圖像的索引。

*影像清單2*<br/>
`CImageList` 物件的參考。

*nImage2*<br/>
第二個現有圖像的索引。

*Dx*<br/>
第二個圖像的 x 軸與第一個圖像(以像素為單位)的偏移。

*Dy*<br/>
第二個圖像的 y 軸與第一個圖像(以像素為單位)的偏移。

*pImageList*<br/>
`CImageList` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

在兩個步驟`CImageList`中構造 一個。 首先調用建構函數,然後調用`Create`,這將創建圖像清單並將其附加`CImageList`到 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

呼叫此函數以刪除影像清單。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

由`CWinApp`空閑時間處理程式自動調`DeleteTempMap`用 ,刪除[FromHandle](#fromhandle)創建`CImageList`的任何臨時物件,`ImageList`但不會銷毀與 物件`hImageList`臨時關聯的任何句柄 ()。

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::D埃塔奇

呼叫此函數以從`CImageList`物件分離圖像列表物件。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>傳回值

影像清單物件的句柄。

### <a name="remarks"></a>備註

此函數返回圖像清單物件的句柄。

### <a name="example"></a>範例

  請參考[CImageList 的範例:附加](#attach)。

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::D拉格輸入

在拖動操作期間,鎖定*pWndLock*指定的視窗的更新,並在*點*指定的位置顯示拖動圖像。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
指向擁有拖動圖像的視窗的指標。

*點*<br/>
要顯示拖動圖像的位置。 坐標相對於視窗的左上角(而不是工作區)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

坐標相對於視窗的左上角,因此在指定座標時,必須補償視窗元素(如邊框、標題列和菜單欄)的寬度。

如果*pWndLock*為 NULL,則此函數將在與桌面視窗關聯的顯示上下文中繪製圖像,座標相對於螢幕的左上角。

此函數在拖動操作期間鎖定給定視窗的所有其他更新。 如果需要在拖動操作期間執行任何繪圖(例如突出顯示拖放操作的目標),可以使用[CImageList::DragLeave](#dragleave)函數暫時隱藏拖動的圖像。

### <a name="example"></a>範例

  請參考[CImageList 的範例::開始拖動](#begindrag)。

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::D拉格葉

解鎖*pWndLock*指定的視窗並隱藏拖動圖像,從而允許更新該視窗。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>參數

*pWndLock*<br/>
指向擁有拖動圖像的視窗的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參考[CImageList::結束拖動的範例](#enddrag)。

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::D拉格移動

調用此函數以移動在拖放操作期間拖動的圖像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
新的拖動位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

通常調用此函數是為了回應WM_MOUSEMOVE消息。 要開始拖動操作,`BeginDrag`請使用成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::D拉格秀諾洛克

在拖動操作期間顯示或隱藏拖動圖像,而不鎖定視窗。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
指定是否顯示拖動圖像。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

[CImageList::DragEnter 函數](#dragenter)在拖動操作期間鎖定視窗的所有更新。 但是,此功能不會鎖定視窗。

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::D原始

調用此函數以繪製在拖放操作期間拖動的圖像。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向目標設備上下文的指標。

*n 影像*<br/>
要繪製的圖像的零基索引。

*pt*<br/>
在指定的設備上下文中繪製的位置。

*nStyle*<br/>
指定繪圖樣式的標誌。 它可以是以下一個或多個值:

|值|意義|
|-----------|-------------|
|ILD_BLEND25,ILD_FOCUS|繪製圖像,將 25% 與系統高光顏色混合。 如果圖像清單不包含蒙版,則此值無效。|
|ILD_BLEND50,ILD_SELECTED,ILD_BLEND|繪製圖像,將 50% 與系統高光顏色混合。 如果圖像清單不包含蒙版,則此值無效。|
|ILD_MASK|繪製蒙版。|
|ILD_NORMAL|使用圖像清單的背景顏色繪製圖像。 如果背景色為CLR_NONE值,則使用蒙版以透明方式繪製圖像。|
|ILD_TRANSPARENT|無論背景顏色如何,都使用蒙版透明地繪製圖像。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參考[CImageList 的範例::設定覆寫影像](#setoverlayimage)。

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::D原始

在指定的裝置上下文中繪製圖像清單項。

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
指向目標設備上下文的指標。

*n 影像*<br/>
要繪製的圖像的零基索引。

*pt*<br/>
在指定的設備上下文中繪製的位置。

*深圳*<br/>
圖像相對於圖像左上角繪製的部分的大小。 在 Windows SDK 中[檢視 ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*dx* *和 dy。*

*clrBk*<br/>
圖像的背景顏色。 在 Windows SDK 中查看[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbBk。*

*clrFg*<br/>
圖像的前景顏色。 在 Windows SDK 中[查看 ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbFg。*

*nStyle*<br/>
指定繪圖樣式的標誌。 請參閱 windows SDK 中[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)*中的 fStyle。*

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

該函數使用指定的繪圖樣式,並將圖像與指定顏色混合。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::D原始間接

呼叫此成員函數從圖像清單中繪製圖像。

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

*皮姆LDP*<br/>
指向[圖像清單DRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的指標,其中包含有關繪製操作的資訊。

*pDC*<br/>
指向目標設備上下文的指標。 完成此[CDC](../../mfc/reference/cdc-class.md)物件後,必須將其刪除。

*n 影像*<br/>
要繪製的圖像的零基索引。

*pt*<br/>
包含繪製影像的 x 和 y 座標的[POINT](/windows/win32/api/windef/ns-windef-point)結構。

*深圳*<br/>
指示要繪製的圖像大小的[SIZE](/windows/win32/api/windef/ns-windef-size)結構。

*ptOrigin*<br/>
包含 x 座標和 y 座標的[POINT](/windows/win32/api/windef/ns-windef-point)結構,用於指定繪圖操作相對於圖像本身的左上角。 不繪製 x 座標左側和 y 座標上方圖像的圖元。

*fStyle*<br/>
指定繪圖樣式的標誌,以及(可選)疊加圖像。 有關疊加圖像的資訊,請參閱備註部分。 MFC 預設實現ILD_NORMAL使用圖像清單的背景顏色繪製圖像。 如果背景色為CLR_NONE值,則使用蒙版以透明方式繪製圖像。

其他可能的樣式在[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的*fStyle*成員下描述。

*dwRop*<br/>
指定柵格操作代碼的值。 這些代碼定義如何將源矩形的顏色數據與目標矩形的顏色數據組合,以實現最終顏色。 MFC 的預設實現 SRCCOPY 將來源矩形直接複製到目標矩形。 如果*fStyle*參數不包含ILD_ROP標誌,則忽略此參數。

其他可能的值在[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)結構的*dwRop*成員下描述。

*rgbBack*<br/>
默認情況下,圖像背景顏色CLR_DEFAULT。 這裡可以是應用程式定義的 RGB 值或以下值之一:

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|預設背景顏色。 使用圖像清單背景顏色繪製圖像。|
|CLR_NONE|無背景顏色。 圖像以透明方式繪製。|

*rgbFore*<br/>
默認情況下,圖像前景顏色CLR_DEFAULT。 這裡可以是應用程式定義的 RGB 值或以下值之一:

|值|意義|
|-----------|-------------|
|CLR_DEFAULT|默認前景顏色。 使用系統高光顏色作為前景顏色繪製圖像。|
|CLR_NONE|無混合顏色。 圖像與目標設備上下文的顏色混合。|

僅當*fStyle*包含ILD_BLEND25或ILD_BLEND50標誌時,才使用此參數。

*f國家*<br/>
指定繪圖狀態的標誌。 此成員可以包含一個或多個圖像清單狀態標誌。

*Frame*<br/>
影響飽和和 α 混合效果的行為。

當與ILS_SATURATE一起使用時,此成員保留添加到圖示中每個圖元的 RGB 三重組件的值。

當與ILS_APLHA一起使用時,此成員保留 Alpha 通道的值。 此值可以是 0 到 255,0 是完全透明的,255 是完全不透明的。

*crEffect*<br/>
用於發光和陰影效果的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="return-value"></a>傳回值

如果圖像成功繪製,則為 TRUE;如果圖像已成功繪製,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

如果要自己填充 Win32 結構,請使用第一個版本。 如果要利用一個或多個 MFC 的預設參數,或避免管理結構,請使用第二個版本。

疊加圖像是在主圖像頂部繪製的圖像,由*nImage*參數在此成員函數中指定。 使用[「繪製](#draw)」成員函數使用使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏指定的疊加蒙版的單一索引繪製疊加蒙版。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList:結束拖動

調用此函數以結束拖動操作。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>備註

要開始拖動操作,`BeginDrag`請使用成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImage 清單::抽取圖示

呼叫此函式可根據影像及其相關蒙版在圖像清單中創建圖示。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>參數

*n 影像*<br/>
圖像的零基索引。

### <a name="return-value"></a>傳回值

如果成功,則處理圖示;否則 NULL。

### <a name="remarks"></a>備註

此方法依賴於[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏的行為來創建圖示。 有關圖示創建和清理的詳細資訊,請參閱[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList:從手處理

當為影像清單指定`CImageList`句柄時,傳回指向物件的指標。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*h 影像清單*<br/>
指定圖像清單。

### <a name="return-value"></a>傳回值

指向`CImageList`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

`CImageList`如果尚未附加到句柄 , 將建立`CImageList`並附加 臨時物件。 此臨時`CImageList`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::從永久處理

當為影像清單指定`CImageList`句柄時,傳回指向物件的指標。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>參數

*h 影像清單*<br/>
指定圖像清單。

### <a name="return-value"></a>傳回值

指向`CImageList`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果物件`CImageList`未附加到句柄,則傳回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList:取得BkColor

呼叫此函式以檢索影像清單的當前背景顏色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

物件背景顏色的`CImageList`RGB 顏色值。

### <a name="example"></a>範例

  請參考[CImageList 的範例:SetBkColor](#setbkcolor)。

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImage 清單::取得拖動影像

獲取用於拖動的臨時圖像清單。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>參數

*lpPoint*<br/>
接收目前拖動位置的[POINT](/windows/win32/api/windef/ns-windef-point)結構的位址。

*lpPointHotSpot*<br/>
`POINT`相對於拖動位置接收拖動圖像偏移的結構的位址。

### <a name="return-value"></a>傳回值

如果成功,則指向用於拖動的臨時圖像列表的指標;如果成功,則指向用於拖動的臨時圖像清單。否則,NULL。

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImage 列表:抓取影像計數

呼叫此函數以檢索影像清單中的圖像數。

```
int GetImageCount() const;
```

### <a name="return-value"></a>傳回值

圖像數。

### <a name="example"></a>範例

  請參考[CImageList 的範例::摘要圖示](#extracticon)。

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList:抓取圖片資訊

調用此函數以檢索有關圖像的資訊。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>參數

*n 影像*<br/>
圖像的零基索引。

*pImageInfo*<br/>
指向接收圖像資訊的[IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo)結構的指標。 此結構中的資訊可用於直接操作圖像的點陣圖。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

結構`IMAGEINFO`包含有關圖像清單中圖像的資訊。

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::取得安全處理

調用此函數以檢索`m_hImageList`數據成員。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>傳回值

附加影像清單的句柄;句柄否則 NULL,如果沒有附加任何物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList:m_hImageList

附加到此物件的圖像清單的句柄。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>備註

數據`m_hImageList`成員是 HIMAGELIST 類型的公共變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::操作員HIMAGELIST

使用此運算元獲取`CImageList`物件的附加句柄。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的圖像清單的句柄;`CImageList`如果成功,則對物件表示的圖像清單的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算符是強制轉換運算符,支援直接使用 HIMAGELIST 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList:閱讀

呼叫此函數從存檔中讀取圖像清單。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*p 封存檔*<br/>
指向要讀取圖像`CArchive`列表的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImage 清單::刪除

呼叫此函數以從影像清單物件中刪除圖像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>參數

*n 影像*<br/>
要刪除的圖像的零索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*nImage*之後的所有項目現在向下移動一個位置。 例如,如果圖像清單包含兩個項目,刪除第一個項將導致其餘項現在位於第一個位置。 *nImage*#0 表示第一個位置中的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList:取代

呼叫此函數以將圖像清單中的圖像替換為新映射。

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

*n 影像*<br/>
要替換的圖像的零基索引。

*pbmImage*<br/>
指向包含圖像的位圖的指標。

*pbmMask*<br/>
指向包含掩碼的位圖的指標。 如果影像清單不使用掩碼,則忽略此參數。

*hIcon*<br/>
包含新圖像的點陣圖和蒙版的圖示的句柄。

### <a name="return-value"></a>傳回值

返回 BOOL 的版本返回非零(如果成功);否則 0。

返回**int**的版本返回圖像的零基索引(如果成功);否則 - 1。

### <a name="remarks"></a>備註

呼叫[SetImageCount](#setimagecount)後呼叫此成員函數,將新的有效影像分配給占位符影像索引號。

### <a name="example"></a>範例

  請參考[CImageList 的範例::設定影像計數](#setimagecount)。

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList:SetBkColor

呼叫此函數以設定影像清單的背景顏色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>參數

*鉻*<br/>
要設置的背景顏色。 它可以是CLR_NONE。 在這種情況下,使用蒙版透明地繪製圖像。

### <a name="return-value"></a>傳回值

如果成功,則上一個背景顏色;否則CLR_NONE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::設定DragCursor圖像

通過將給定圖像(通常是滑鼠游標圖像)與當前拖動圖像相結合,創建新的拖動圖像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>參數

*nDrag*<br/>
要與拖動圖像組合的新圖像的索引。

*點熱點*<br/>
新圖像中熱點的位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

由於拖動函數在拖動操作期間使用新圖像,因此應在調用`CImageList::SetDragCursorImage`後使用 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor)函數隱藏實際滑鼠游標。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImage 清單::設定影像計數

調用此成員函數以重置`CImageList`物件中的圖像數。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>參數

*uNew( U) Count*<br/>
指定影像清單中的新圖像總數的值。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果調用此成員函數以增加圖像清單中的圖像數,則調用每個附加圖像的[Replace](#replace)以將新索引分配給有效圖像。 如果無法將索引分配給有效圖像,則繪製創建新圖像的操作將不可預測。

如果使用此功能減小圖像清單的大小,則釋放截斷的圖像。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::設定疊加影像

呼叫此函數將圖像的零基索引添加到要用作疊加蒙版的圖像清單中。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>參數

*n 影像*<br/>
圖像的零索引,用作疊加蒙版。

*內弗萊*<br/>
疊加蒙版的單基索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

最多可以向清單中添加四個索引。

疊加蒙版是在另一個圖像上透明繪製的圖像。 使用[CImageList::Draw](#draw)成員函數使用使用 INDEXTOOVERLAYMASK 宏指定的覆蓋蒙版的單一索引在圖像上繪製疊加蒙版。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList:寫入

呼叫此函數將圖像清單物件寫入檔。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>參數

*p 封存檔*<br/>
指向要存儲圖像`CArchive`清單的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)
