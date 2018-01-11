---
title: "CD2DBitmapBrush 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs: C++
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dd588a26b73fb6e5f1b205b20f21aab8272c439
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 類別
ID2D1BitmapBrush 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|多載。 建構 CD2DBitmapBrush 物件檔案。|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|解構函式。 D2D 點陣圖筆刷物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|將現有的資源物件的介面|  
|[CD2DBitmapBrush::Create](#create)|建立 CD2DBitmapBrush。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DBitmapBrush::Destroy](#destroy)|CD2DBitmapBrush 物件已遭終結。 (覆寫[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
|[CD2DBitmapBrush::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DBitmapBrush::Get](#get)|傳回 ID2D1BitmapBrush 介面|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|取得這個筆刷用來繪製點陣圖來源|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|取得這筆刷水平並排延伸超過其點陣圖之區域的方法|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|取得這筆刷垂直並排延伸超過其點陣圖之區域的方法|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|取得筆刷點陣圖是縮放或旋轉時使用的內插補點方法|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|指定這個筆刷用來繪製點陣圖來源|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|指定如何筆刷水平並排延伸超過其點陣圖的區域|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|指定如何筆刷垂直並排延伸超過其點陣圖的區域|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|指定使用筆刷點陣圖縮放或旋轉時的插補模式|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|初始化物件|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|傳回 ID2D1BitmapBrush 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|儲存 CD2DBitmap 物件的指標。|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|儲存 ID2D1BitmapBrush 物件的指標。|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|點陣圖筆刷屬性。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="dtor"></a>CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 解構函式。 D2D 點陣圖筆刷物件終結時呼叫。  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>CD2DBitmapBrush::Attach  
 將現有的資源物件的介面  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有資源的介面。 不能是 NULL  
  
##  <a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush  
 建構 CD2DBitmapBrush 物件。  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `pBitmapBrushProperties`  
 擴充模式和插補模式點陣圖的筆刷的指標。  
  
 `pBrushProperties`  
 指標的不透明度和筆刷的轉換。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
 `uiResID`  
 資源的資源 ID 編號。  
  
 `lpszType`  
 以 null 終止的字串，其中包含的資源類型的指標。  
  
 `sizeDest`  
 目的地點陣圖的大小。  
  
 `lpszImagePath`  
 以 null 終止的字串，其中包含檔案名稱的指標。  
  
##  <a name="commoninit"></a>CD2DBitmapBrush::CommonInit  
 初始化物件  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>參數  
 `pBitmapBrushProperties`  
 指向點陣圖筆刷屬性。  
  
##  <a name="create"></a>CD2DBitmapBrush::Create  
 建立 CD2DBitmapBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>CD2DBitmapBrush::Destroy  
 CD2DBitmapBrush 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmapBrush::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源的介面指標。  
  
##  <a name="get"></a>CD2DBitmapBrush::Get  
 傳回 ID2D1BitmapBrush 介面  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1BitmapBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap  
 取得這個筆刷用來繪製點陣圖來源  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>傳回值  
 CD2DBitmap 物件或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX  
 取得這筆刷水平並排延伸超過其點陣圖之區域的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指定如何筆刷水平並排延伸超過其點陣圖的區域  
  
##  <a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY  
 取得這筆刷垂直並排延伸超過其點陣圖之區域的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指定如何筆刷垂直並排延伸超過其點陣圖的區域  
  
##  <a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode  
 取得筆刷點陣圖是縮放或旋轉時使用的內插補點方法  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 筆刷點陣圖是縮放或旋轉時使用的內插補點方法  
  
##  <a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap  
 儲存 CD2DBitmap 物件的指標。  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush  
 儲存 ID2D1BitmapBrush 物件的指標。  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties  
 點陣圖筆刷屬性。  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 傳回 ID2D1BitmapBrush 介面  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>傳回值  
 ID2D1BitmapBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap  
 指定這個筆刷用來繪製點陣圖來源  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `pBitmap`  
 使用筆刷的點陣圖來源  
  
##  <a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX  
 指定如何筆刷水平並排延伸超過其點陣圖的區域  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>參數  
 `extendModeX`  
 值，指定如何筆刷水平並排延伸超過其點陣圖的區域  
  
##  <a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY  
 指定如何筆刷垂直並排延伸超過其點陣圖的區域  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>參數  
 `extendModeY`  
 值，指定如何筆刷垂直並排延伸超過其點陣圖的區域  
  
##  <a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode  
 指定使用筆刷點陣圖縮放或旋轉時的插補模式  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>參數  
 `interpolationMode`  
 筆刷點陣圖是縮放或旋轉時使用的插補模式  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
