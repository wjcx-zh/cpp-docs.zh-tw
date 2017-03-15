---
title: "CPictureHolder 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Picture
- CPictureHolder
dev_langs:
- C++
helpviewer_keywords:
- Picture property
- controls [MFC], OLE
- OLE controls, image
- CPictureHolder class
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 20
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 14a774e3edc8b5e160b287612d3709c3424503be
ms.lasthandoff: 02/24/2017

---
# <a name="cpictureholder-class"></a>CPictureHolder 類別
實作 [圖片] 屬性，可讓使用者在控制項中顯示圖片。  
  
## <a name="syntax"></a>語法  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|建構 `CPictureHolder` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|建立空的 `CPictureHolder` 物件。|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|建立`CPictureHolder`點陣圖中的物件。|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|建立`CPictureHolder`從圖示的物件。|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|建立`CPictureHolder`中繼檔中的物件。|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|擷取控制項容器的屬性瀏覽器中顯示的字串。|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|傳回`CPictureHolder`物件的`IDispatch`介面。|  
|[CPictureHolder::GetType](#gettype)|指示是否`CPictureHolder`物件是點陣圖、 中繼檔或圖示。|  
|[CPictureHolder::Render](#render)|呈現圖片。|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|設定`CPictureHolder`物件的`IDispatch`介面。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|圖片物件指標。|  
  
## <a name="remarks"></a>備註  
 `CPictureHolder`沒有基底類別。  
  
 使用內建的 [圖片] 屬性中，開發人員可以指定點陣圖、 圖示或顯示中繼檔。  
  
 如需建立自訂圖片屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項︰ 使用 ActiveX 控制項中的圖片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPictureHolder`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-namecpictureholdera--cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder  
 建構 `CPictureHolder` 物件。  
  
```  
CPictureHolder();
```  
  
##  <a name="a-namecreateemptya--cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty  
 建立空`CPictureHolder`物件，並連接至其`IPicture`介面。  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立物件。否則為 0。  
  
##  <a name="a-namecreatefrombitmapa--cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap  
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
 `idResource`  
 點陣圖資源的資源識別碼。  
  
 `pBitmap`  
 指標[CBitmap](../../mfc/reference/cbitmap-class.md)物件。  
  
 *pPal*  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件。  
  
 `bTransferOwnership`  
 表示圖片物件是否將點陣圖和調色盤物件的擁有權。  
  
 `hbm`  
 點陣圖的控制代碼`CPictureHolder`建立物件。  
  
 `hpal`  
 用來呈現點陣圖的調色盤的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立物件。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**、 呼叫端不應該使用點陣圖或以任何方式在這個呼叫之後調色盤物件傳回。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保圖片物件的存留期間點陣圖和調色盤物件保持有效。  
  
##  <a name="a-namecreatefromicona--cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateFromIcon  
 使用圖示來初始化中的圖片物件`CPictureHolder`。  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `idResource`  
 點陣圖資源的資源識別碼。  
  
 `hIcon`  
 圖示的控制代碼`CPictureHolder`建立物件。  
  
 `bTransferOwnership`  
 表示圖片物件是否將圖示物件的擁有權。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立物件。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**，呼叫端應該不圖示物件以任何方式使用這個呼叫傳回之後也一樣。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保圖示物件圖片物件的存留期就持續有效。  
  
##  <a name="a-namecreatefrommetafilea--cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile  
 使用中繼檔中的將圖片物件初始化`CPictureHolder`。  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `hmf`  
 用來建立中繼檔的控制代碼`CPictureHolder`物件。  
  
 *xExt*  
 X 圖片的範圍。  
  
 *yExt*  
 圖片的 Y 範圍。  
  
 `bTransferOwnership`  
 表示圖片物件是否將中繼檔物件的擁有權。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立物件。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**，呼叫端不應該使用中繼檔的物件以任何方式這個呼叫傳回之後也一樣。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保中繼檔物件的圖片物件存留期就持續有效。  
  
##  <a name="a-namegetdisplaystringa--cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString  
 擷取容器的屬性瀏覽器中顯示的字串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>參數  
 `strValue`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)要保存的顯示字串。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功擷取的字串。否則為 0。  
  
##  <a name="a-namegetpicturedispatcha--cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch  
 此函式傳回的指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
### <a name="remarks"></a>備註  
 呼叫端必須呼叫**版本**當它完成時，此指標上。  
  
##  <a name="a-namegettypea--cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType  
 表示圖片的點陣圖，中繼檔或圖示。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 值，指出類型的圖片。 可能的值和其意義如下︰  
  
|值|意義|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder`物件被 unititialized。|  
|**PICTYPE_NONE**|`CPictureHolder`物件是空的。|  
|**PICTYPE_BITMAP**|圖片是點陣圖。|  
|**PICTYPE_METAFILE**|圖片是中繼檔。|  
|**PICTYPE_ICON**|圖片都會有一個圖示。|  
  
##  <a name="a-namemppicta--cpictureholdermppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict  
 指標`CPictureHolder`物件的`IPicture`介面。  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="a-namerendera--cpictureholderrender"></a><a name="render"></a>CPictureHolder::Render  
 呈現所參考的矩形中的圖片`rcRender`。  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 要呈現圖片顯示內容的指標。  
  
 `rcRender`  
 圖片為呈現的矩形。  
  
 *rcWBounds*  
 表示轉譯圖片的物件，這個周框矩形。 對控制項中，這個矩形是`rcBounds`參數傳遞的覆寫至[COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw)。  
  
##  <a name="a-namesetpicturedispatcha--cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch  
 連接`CPictureHolder`物件傳遞給`IPictureDisp`介面。  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 新指標`IPictureDisp`介面。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder 類別](../../mfc/reference/cfontholder-class.md)

