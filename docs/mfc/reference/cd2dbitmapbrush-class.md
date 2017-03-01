---
title: "CD2DBitmapBrush 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- afxrendertarget/CD2DBitmapBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmapBrush class
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a9ab15dcae8715b98cc9f723a710b64e83649bf9
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 類別
ID2D1BitmapBrush 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|多載。 建構 CD2DBitmapBrush 物件從檔案。|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|解構函式。 D2D 點陣圖 brush 物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|會附加至現有的資源物件的介面|  
|[CD2DBitmapBrush::Create](#create)|建立 CD2DBitmapBrush。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DBitmapBrush::Destroy](#destroy)|終結 CD2DBitmapBrush 物件。 (覆寫[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
|[CD2DBitmapBrush::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DBitmapBrush::Get](#get)|傳回 ID2D1BitmapBrush 介面|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|取得這個筆刷用來繪製的點陣圖來源|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|取得這筆刷水平並排超過其點陣圖之區域的方法|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|取得這筆刷垂直並排超過其點陣圖之區域的方法|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|取得筆刷點陣圖是縮放或旋轉時所使用的插補方法|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|指定這個筆刷用來繪製的點陣圖來源|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|指定如何筆刷水平並排超過其點陣圖的區域|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|指定如何筆刷垂直重疊顯示超過其點陣圖的區域|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|指定使用縮放或旋轉筆刷點陣圖時的插補模式|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|初始化物件|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|傳回 ID2D1BitmapBrush 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|儲存 CD2DBitmap 物件的指標。|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|儲存 ID2D1BitmapBrush 物件的指標。|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|點陣圖 筆刷屬性。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-namedtora--cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 解構函式。 D2D 點陣圖 brush 物件終結時呼叫。  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="a-nameattacha--cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::Attach  
 會附加至現有的資源物件的介面  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有的資源介面。 不能是 NULL  
  
##  <a name="a-namecd2dbitmapbrusha--cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush  
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
 將延伸模式和插補模式點陣圖的筆刷的指標。  
  
 `pBrushProperties`  
 指標的不透明度和筆刷轉換。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
 `uiResID`  
 資源的資源 ID 編號。  
  
 `lpszType`  
 以 null 終止的字串，其中包含的資源類型的指標。  
  
 `sizeDest`  
 目的地點陣圖的大小。  
  
 `lpszImagePath`  
 以 null 終止的字串，其中包含檔案名稱的指標。  
  
##  <a name="a-namecommoninita--cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit  
 初始化物件  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>參數  
 `pBitmapBrushProperties`  
 指向點陣圖筆刷屬性。  
  
##  <a name="a-namecreatea--cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush::Create  
 建立 CD2DBitmapBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="a-namedestroya--cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy  
 終結 CD2DBitmapBrush 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namedetacha--cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源介面指標。  
  
##  <a name="a-namegeta--cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Get  
 傳回 ID2D1BitmapBrush 介面  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1BitmapBrush 介面的指標。  
  
##  <a name="a-namegetbitmapa--cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap  
 取得這個筆刷用來繪製的點陣圖來源  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 CD2DBitmap 物件的指標。  
  
##  <a name="a-namegetextendmodexa--cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX  
 取得這筆刷水平並排超過其點陣圖之區域的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指定如何筆刷水平並排超過其點陣圖的區域  
  
##  <a name="a-namegetextendmodeya--cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY  
 取得這筆刷垂直並排超過其點陣圖之區域的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指定如何筆刷垂直重疊顯示超過其點陣圖的區域  
  
##  <a name="a-namegetinterpolationmodea--cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode  
 取得筆刷點陣圖是縮放或旋轉時所使用的插補方法  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用縮放或旋轉筆刷點陣圖時的插補方法  
  
##  <a name="a-namempbitmapa--cd2dbitmapbrushmpbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap  
 儲存 CD2DBitmap 物件的指標。  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="a-namempbitmapbrusha--cd2dbitmapbrushmpbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush  
 儲存 ID2D1BitmapBrush 物件的指標。  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="a-namempbitmapbrushpropertiesa--cd2dbitmapbrushmpbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties  
 點陣圖 筆刷屬性。  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="a-nameoperatorid2d1bitmapbrushstara--cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 傳回 ID2D1BitmapBrush 介面  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1BitmapBrush 介面的指標。  
  
##  <a name="a-namesetbitmapa--cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap  
 指定這個筆刷用來繪製的點陣圖來源  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `pBitmap`  
 使用筆刷的點陣圖來源  
  
##  <a name="a-namesetextendmodexa--cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX  
 指定如何筆刷水平並排超過其點陣圖的區域  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>參數  
 `extendModeX`  
 值，指定如何筆刷水平並排超過其點陣圖的區域  
  
##  <a name="a-namesetextendmodeya--cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY  
 指定如何筆刷垂直重疊顯示超過其點陣圖的區域  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>參數  
 `extendModeY`  
 值，指定如何筆刷垂直重疊顯示超過其點陣圖的區域  
  
##  <a name="a-namesetinterpolationmodea--cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode  
 指定使用縮放或旋轉筆刷點陣圖時的插補模式  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>參數  
 `interpolationMode`  
 筆刷點陣圖是縮放或旋轉時使用的插補模式  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

