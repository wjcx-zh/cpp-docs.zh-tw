---
title: CD2DBitmap 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: a3cabb00ded7dbc5f9c396a1de767058443a4436
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754215"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap 類別

ID2D1Bitmap 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap:CD2DBitmap](#cd2dbitmap)|已多載。 從 HBITMAP 構造 CD2DBitmap 物件。|
|[CD2DBitmap:*CD2DBitmap](#_dtorcd2dbitmap)|解構函式。 銷毀 D2D 位圖物件時調用。|

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap:CD2DBitmap](#cd2dbitmap)|已多載。 構造 CD2DBitmap 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::附加](#attach)|將現有資源介面附加到物件|
|[CD2DBitmap::從位圖複製](#copyfrombitmap)|將指定區域從指定點陣圖複製到目前的點陣圖|
|[CD2DBitmap::從記憶體複製](#copyfrommemory)|將指定區域從記憶體複製到目前的點陣圖|
|[CD2DBitmap::從成成成目標](#copyfromrendertarget)|將指定區域從指定的渲染目標複製到目前的點陣圖|
|[CD2DBitmap:建立](#create)|創建 CD2DBitmap。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::D](#destroy)|銷毀 CD2DBitmap 物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DBitmap::Detach](#detach)|從物件分離資源介面|
|[CD2DBitmap:取得](#get)|傳回 ID2D1 位元圖介面|
|[CD2DBitmap:GetDPI](#getdpi)|傳回點陣圖每英吋 (DPI) 的點|
|[CD2DBitmap::取得像素格式](#getpixelformat)|以索點圖的像素格式和 Alpha 模式|
|[CD2DBitmap::取得圖元大小](#getpixelsize)|傳回點圖的大小(以與裝置相關的單位(像素)|
|[CD2DBitmap:取得大小](#getsize)|傳回點陣圖大小(以與裝置無關的圖元 (DIP)|
|[CD2DBitmap:有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::共同資訊](#commoninit)|初始化物件|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap::操作員 ID2D1 位圖*](#operator_id2d1bitmap_star)|傳回 ID2D1 位元圖介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DBitmap:m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|如果m_hBmpSrc應銷毀,則為 TRUE;否則 FALSE。|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|源點陣圖句柄。|
|[CD2DBitmap:m_lpszType](#m_lpsztype)|資源類型。|
|[CD2DBitmap:m_pBitmap](#m_pbitmap)|存儲指向 ID2D1Bitmap 物件的指標。|
|[CD2DBitmap:m_sizeDest](#m_sizedest)|位圖目標大小。|
|[CD2DBitmap:m_strPath](#m_strpath)|機器人對應文件路徑。|
|[CD2DBitmap:m_uiResID](#m_uiresid)|位圖資源識別碼。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap:*CD2DBitmap

解構函式。 銷毀 D2D 位圖物件時調用。

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap::附加

將現有資源介面附加到物件。

```cpp
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 不能是 NULL。

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap:CD2DBitmap

從資源構造 CD2DBitmap 物件。

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

*p 父目標*<br/>
指向渲染目標的指標。

*uiResID*<br/>
資源的資源識別碼。

*lpszType*<br/>
指向包含資源類型的空端字串的指標。

*大小 D 最大*<br/>
位圖的目標大小。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

*lpszPath*<br/>
包含檔案名稱的 null 中斷字串的指標。

*赫布普斯克*<br/>
處理點陣圖。

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap::共同資訊

初始化物件。

```cpp
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap::從位圖複製

將指定區域從指定的點陣圖複製到當前位圖中。

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
在當前點陣圖中,複製 srcRect 指定的區域的左上角。

*斯克拉特*<br/>
要複製的點陣圖區域。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap::從記憶體複製

將指定區域從記憶體複製到當前位圖中。

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>參數

*srcData*<br/>
要複製的資料。

*瀝青*<br/>
存儲在 srcData 中的來源點陣圖的步長或間距。 步長是掃描線的位元組計數(記憶體中的一行圖元)。 可以從以下公式計算步長:圖元寬\*度 位元組/圖元 = 記憶體填充。

*destRect*<br/>
在當前點陣圖中,複製 srcRect 指定的區域的左上角。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap::從成成成目標

將指定的區域從指定的渲染目標複製到當前位圖中。

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
包含要複製的區域的渲染目標。

*destPoint*<br/>
在當前點陣圖中,複製 srcRect 指定的區域的左上角。

*斯克拉特*<br/>
要複製的渲染目標區域。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap:建立

創建 CD2DBitmap。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap::D

銷毀 CD2DBitmap 物件。

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap::Detach

從物件分離資源介面。

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap:取得

返回 ID2D1 位圖介面。

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Bitmap 介面或 NULL 的指標。

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap:GetDPI

返回點陣圖每英吋 (DPI) 的點。

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>傳回值

位圖的水準和垂直 DPI。

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap::取得像素格式

以索點圖的像素格式和 Alpha 模式

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>傳回值

點陣圖的圖元格式和 Alpha 模式。

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap::取得圖元大小

返回位圖的大小(以與設備相關的單位(圖元)。

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>傳回值

位圖的大小(以像素為單位)。

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap:取得大小

返回點陣圖的大小(以與設備無關的圖元 (DIP)。

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>傳回值

位圖的大小(以 DIP 表示)。

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap:有效

檢查資源有效性。

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap:m_bAutoDestroyHBMP

如果m_hBmpSrc應銷毀,則為 TRUE;否則 FALSE。

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc

源點陣圖句柄。

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap:m_lpszType

資源類型。

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap:m_pBitmap

存儲指向 ID2D1Bitmap 物件的指標。

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap:m_sizeDest

位圖目標大小。

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap:m_strPath

機器人對應文件路徑。

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap:m_uiResID

位圖資源識別碼。

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap::操作員 ID2D1 位圖*

傳回 ID2D1 位元圖介面

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Bitmap 介面或 NULL 的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
