---
title: CPictureHolder 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
dev_langs:
- C++
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e00a1da7aeffd07e19b58437bda2c8631af9158a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852857"
---
# <a name="cpictureholder-class"></a>CPictureHolder 類別
實作 [圖片] 屬性，可讓使用者在控制項中顯示圖片。  
  
## <a name="syntax"></a>語法  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|建構 `CPictureHolder` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|建立空的 `CPictureHolder` 物件。|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|建立`CPictureHolder`從點陣圖物件。|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|建立`CPictureHolder`從圖示的物件。|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|建立`CPictureHolder`中繼檔中的物件。|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|擷取控制項容器的屬性瀏覽器中顯示的字串。|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|傳回`CPictureHolder`物件的`IDispatch`介面。|  
|[CPictureHolder::GetType](#gettype)|會告知是否`CPictureHolder`物件是點陣圖、 中繼檔或圖示。|  
|[Cpictureholder:: Render](#render)|呈現圖片。|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|設定組`CPictureHolder`物件的`IDispatch`介面。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|圖片物件指標。|  
  
## <a name="remarks"></a>備註  
 `CPictureHolder` 沒有基底類別。  
  
 使用內建的 [圖片] 屬性中，開發人員可以指定點陣圖、 圖示或顯示的中繼檔。  
  
 如需建立自訂圖片屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項： 使用 ActiveX 控制項中的圖片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPictureHolder`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxctl.h  
  
##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder  
 建構 `CPictureHolder` 物件。  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>  CPictureHolder::CreateEmpty  
 建立空`CPictureHolder`物件，並將它連接到`IPicture`介面。  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>傳回值  
 已成功建立該物件; 如果為非零否則為 0。  
  
##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap  
 利用點陣圖來初始化中的圖片物件`CPictureHolder`。  
  
```  
BOOL CreateFromBitmap(
    UINT idResource);

 
BOOL CreateFromBitmap(
    CBitmap* pBitmap,  
    CPalette* pPal = NULL,  
    BOOL bTransferOwnership = TRUE);

 
BOOL CreateFromBitmap(
    HBITMAP hbm,  
    HPALETTE hpal = NULL,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *idResource*  
 點陣圖資源的資源識別碼。  
  
 *pBitmap*  
 指標[CBitmap](../../mfc/reference/cbitmap-class.md)物件。  
  
 *pPal*  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件。  
  
 *bTransferOwnership*  
 指出圖片物件是否會採取點陣圖和調色盤物件的擁有權。  
  
 *hbm*  
 從中的點陣圖控制代碼`CPictureHolder`建立物件。  
  
 *hpal*  
 用於轉譯點陣圖的調色盤的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 已成功建立該物件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果*bTransferOwnership*為 TRUE、 呼叫端不應該使用點陣圖或以任何方式在這個呼叫之後的調色盤物件傳回。 如果*bTransferOwnership*為 FALSE 時，呼叫端會負責確保圖片物件的存留期內保持有效的點陣圖和調色盤的物件。  
  
##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon  
 使用圖示來初始化中的圖片物件`CPictureHolder`。  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *idResource*  
 點陣圖資源的資源識別碼。  
  
 *hIcon*  
 從其控制代碼，以圖示`CPictureHolder`建立物件。  
  
 *bTransferOwnership*  
 指出圖片物件是否會採取圖示物件的擁有權。  
  
### <a name="return-value"></a>傳回值  
 已成功建立該物件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果*bTransferOwnership*為 TRUE 時，呼叫端不應該使用的圖示物件以任何方式之後這個呼叫會傳回。 如果*bTransferOwnership*為 FALSE 時，呼叫端會負責確保圖示物件圖片物件的存留期內維持有效。  
  
##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile  
 使用中繼檔圖片物件初始化在`CPictureHolder`。  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *hmf*  
 用來建立中繼檔案的控制代碼`CPictureHolder`物件。  
  
 *xExt*  
 X 圖片的範圍。  
  
 *yExt*  
 圖片的 Y 範圍。  
  
 *bTransferOwnership*  
 指出圖片物件是否需要中繼檔物件的擁有權。  
  
### <a name="return-value"></a>傳回值  
 已成功建立該物件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果*bTransferOwnership*為 TRUE 時，呼叫端不應該使用中繼檔的物件以任何方式之後這個呼叫會傳回。 如果*bTransferOwnership*為 FALSE 時，呼叫端會負責確保圖片物件的存留期內維持有效的中繼檔物件。  
  
##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString  
 擷取容器的屬性瀏覽器中顯示的字串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>參數  
 *strValue*  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)要保存的顯示字串。  
  
### <a name="return-value"></a>傳回值  
 已成功擷取的字串; 如果為非零否則為 0。  
  
##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch  
 此函式傳回的指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
### <a name="remarks"></a>備註  
 呼叫端必須呼叫`Release`在當它完成時，這個指標上。  
  
##  <a name="gettype"></a>  CPictureHolder::GetType  
 指出圖片是否為點陣圖、 中繼檔或圖示。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 值，指出類型的圖片。 可能的值和其意義如下：  
  
|值|意義|  
|-----------|-------------|  
|PICTYPE_UNINITIALIZED|`CPictureHolder` 物件被 unititialized。|  
|PICTYPE_NONE|`CPictureHolder` 物件是空的。|  
|PICTYPE_BITMAP|圖片是點陣圖。|  
|PICTYPE_METAFILE|圖片會在中繼檔。|  
|PICTYPE_ICON|圖片顯示為圖示。|  
  
##  <a name="m_ppict"></a>  CPictureHolder::m_pPict  
 指標`CPictureHolder`物件的`IPicture`介面。  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>  Cpictureholder:: Render  
 呈現的圖片中所參考的矩形*rcRender*。  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>參數  
 *pDC*  
 要轉譯圖片的顯示內容的指標。  
  
 *rcRender*  
 圖片為呈現的矩形。  
  
 *rcWBounds*  
 表示轉譯圖片物件週框矩形。 是控制項，這個矩形是*rcbounds 就*參數傳遞至的覆寫[COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw)。  
  
##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch  
 連接`CPictureHolder`物件至`IPictureDisp`介面。  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>參數  
 *pDisp*  
 新的指標`IPictureDisp`介面。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder 類別](../../mfc/reference/cfontholder-class.md)
