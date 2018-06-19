---
title: CD2DPathGeometry 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs:
- C++
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3afe8efa5730c3ef0f4448b1c548724b56b7cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353412"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 類別
ID2D1PathGeometry 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|建構 CD2DPathGeometry 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](#attach)|將現有的資源物件的介面|  
|[CD2DPathGeometry::Create](#create)|建立 CD2DPathGeometry。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DPathGeometry::Destroy](#destroy)|CD2DPathGeometry 物件已遭終結。 (覆寫[CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy)。)|  
|[CD2DPathGeometry::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|擷取之路徑幾何中的數字的數目。|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|擷取之路徑幾何中的區段數目。|  
|[CD2DPathGeometry::Open](#open)|擷取用來填入以數字和區段之路徑幾何的幾何接收。|  
|[CD2DPathGeometry::Stream](#stream)|將之路徑幾何的內容複製到指定 ID2D1GeometrySink。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|ID2D1PathGeometry 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="attach"></a>  CD2DPathGeometry::Attach  
 將現有的資源物件的介面  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有資源的介面。 不能是 NULL  
  
##  <a name="cd2dpathgeometry"></a>  CD2DPathGeometry::CD2DPathGeometry  
 建構 CD2DPathGeometry 物件。  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>  CD2DPathGeometry::Create  
 建立 CD2DPathGeometry。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>  CD2DPathGeometry::Destroy  
 CD2DPathGeometry 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DPathGeometry::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源的介面指標。  
  
##  <a name="getfigurecount"></a>  CD2DPathGeometry::GetFigureCount  
 擷取之路徑幾何中的數字的數目。  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回之路徑幾何中的數字的數目。  
  
##  <a name="getsegmentcount"></a>  CD2DPathGeometry::GetSegmentCount  
 擷取之路徑幾何中的區段數目。  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回之路徑幾何中的區段數目。  
  
##  <a name="m_ppathgeometry"></a>  CD2DPathGeometry::m_pPathGeometry  
 ID2D1PathGeometry 指標。  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>  CD2DPathGeometry::Open  
 擷取用來填入以數字和區段之路徑幾何的幾何接收。  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>傳回值  
 用來填入以數字和區段之路徑幾何 ID2D1GeometrySink 指標。  
  
##  <a name="stream"></a>  CD2DPathGeometry::Stream  
 將之路徑幾何的內容複製到指定 ID2D1GeometrySink。  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>參數  
 `geometrySink`  
 接收之路徑幾何的內容複製到其中。 修改這個接收不會變更此路徑幾何的內容。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
