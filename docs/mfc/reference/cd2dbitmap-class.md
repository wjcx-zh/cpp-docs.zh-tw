---
title: CD2DBitmap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d232eec6593e0daafb31461847e8d481e60f80ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374348"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap 類別

ID2D1Bitmap 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|多載。 建構 HBITMAP CD2DBitmap 物件。|
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|解構函式。 D2D 點陣圖物件正在被終結時呼叫。|

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|多載。 建構 CD2DBitmap 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|將現有的資源物件的介面|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|將指定的區域從指定的點陣圖複製到目前的點陣圖|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|指定的區域複製到目前的點陣圖的記憶體|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|複製指定的區域，從指定呈現目標的目前點陣圖|
|[CD2DBitmap::Create](#create)|建立 CD2DBitmap。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|
|[CD2DBitmap::Destroy](#destroy)|終結 CD2DBitmap 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DBitmap::Detach](#detach)|中斷連結物件中的資源介面|
|[CD2DBitmap::Get](#get)|傳回 ID2D1Bitmap 介面|
|[CD2DBitmap::GetDPI](#getdpi)|傳回的 dots per inch (DPI) 的點陣圖|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|擷取點陣圖的像素格式和 alpha 模式|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|點陣圖的傳回大小，單位為裝置而異 （像素）|
|[CD2DBitmap::GetSize](#getsize)|傳回點陣圖的大小，以裝置獨立畫素 (Dip)，|
|[CD2DBitmap::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|初始化物件|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|傳回 ID2D1Bitmap 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|如果應終結 m_hBmpSrc;，則為 TRUE。否則為 FALSE。|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|來源點陣圖的控制代碼。|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|資源類型。|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|儲存 ID2D1Bitmap 物件的指標。|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|點陣圖目的大小。|
|[CD2DBitmap::m_strPath](#m_strpath)|Botmap 檔案路徑。|
|[CD2DBitmap::m_uiResID](#m_uiresid)|點陣圖的資源識別碼。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap:: ~ CD2DBitmap

解構函式。 D2D 點陣圖物件正在被終結時呼叫。

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

將現有的資源物件的介面。

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>參數

*pResource*<br/>
現有的資源介面。 不可以是 NULL。

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

CD2DBitmap 從建構物件資源。

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);


CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);


CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);


CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*pParentTarget*<br/>
到轉譯目標的指標。

*uiResID*<br/>
資源的資源識別碼號碼。

*lpszType*<br/>
以 null 終止的字串，其中包含的資源類型的指標。

*sizeDest*<br/>
點陣圖的目的大小。

*bAutoDestroy*<br/>
表示擁有者 (pParentTarget) 將會終結物件。

*lpszPath*<br/>
以 null 終止的字串，其中包含檔案名稱的指標。

*hbmpSrc*<br/>
點陣圖的控制代碼。

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

初始化物件。

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

將指定的區域從指定的點陣圖複製到目前的點陣圖。

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
要複製的點陣圖。

*destPoint*<br/>
在目前的點陣圖，會複製的區域則是 srcRect 所指定的區域的左上角。

*srcRect*<br/>
若要複製的點陣圖的區域。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

將指定的區域從記憶體中複製到目前的點陣圖。

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>參數

*srcData*<br/>
要複製的資料。

*音調*<br/>
分散的音調、 儲存在 srcData 來源點陣圖。 分散是掃瞄線 （在記憶體中的像素為單位的一個資料列） 的位元組計數。 Stride 可以從下列公式計算： 像素寬度\*每像素 + 記憶體填補位元組。

*destRect*<br/>
在目前的點陣圖，會複製的區域則是 srcRect 所指定的區域的左上角。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

複製指定的區域，指定從呈現目標到目前的點陣圖。

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>參數

*pRenderTarget*<br/>
呈現目標，其中包含要複製的區域。

*destPoint*<br/>
在目前的點陣圖，會複製的區域則是 srcRect 所指定的區域的左上角。

*srcRect*<br/>
若要複製的 renderTarget 區域。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="create"></a>  CD2DBitmap::Create

建立 CD2DBitmap。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRenderTarget*<br/>
到轉譯目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="destroy"></a>  CD2DBitmap::Destroy

終結 CD2DBitmap 物件。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::Detach

中斷連結物件中的資源介面。

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>傳回值

中斷連結的資源介面指標。

##  <a name="get"></a>  CD2DBitmap::Get

傳回 ID2D1Bitmap 介面。

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1Bitmap 介面的指標。

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

傳回的 dots per inch (DPI) 的點陣圖。

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>傳回值

點陣圖的水平和垂直 DPI。

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

擷取點陣圖的像素格式和 alpha 模式

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>傳回值

點陣圖的像素格式和 alpha 模式。

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

點陣圖的傳回大小，單位為裝置而異 （像素）。

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>傳回值

單位為像素點陣圖的大小...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

傳回的大小，以裝置獨立畫素 (Dip)，點陣圖。

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>傳回值

Dip，點陣圖的大小。

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

檢查資源的有效性。

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源無效，則為 TRUE否則為 FALSE。

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

如果應終結 m_hBmpSrc;，則為 TRUE。否則為 FALSE。

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

來源點陣圖的控制代碼。

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

資源類型。

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

儲存 ID2D1Bitmap 物件的指標。

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

點陣圖目的大小。

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

Botmap 檔案路徑。

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

點陣圖的資源識別碼。

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::operator ID2D1Bitmap *

傳回 ID2D1Bitmap 介面

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1Bitmap 介面的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
