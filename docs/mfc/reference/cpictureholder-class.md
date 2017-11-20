---
title: "CPictureHolder 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 779ecfc7bd546e2acbd013be9cbb229df2c5e62d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cpictureholder-class"></a>CPictureHolder 類別
實作圖片屬性，這可讓使用者在控制項中顯示的圖片。  
  
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
|[CPictureHolder::GetType](#gettype)|指示是否`CPictureHolder`物件是點陣圖，中繼檔或圖示。|  
|[Cpictureholder:: Render](#render)|呈現圖片。|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|設定`CPictureHolder`物件的`IDispatch`介面。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|以圖片物件指標。|  
  
## <a name="remarks"></a>備註  
 `CPictureHolder`沒有基底類別。  
  
 使用內建圖片屬性中，開發人員可以指定點陣圖、 圖示或顯示中繼檔。  
  
 如需建立自訂圖片屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項： 在 ActiveX 控制項中使用的圖片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPictureHolder`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxctl.h  
  
##  <a name="cpictureholder"></a>CPictureHolder::CPictureHolder  
 建構 `CPictureHolder` 物件。  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>CPictureHolder::CreateEmpty  
 建立空`CPictureHolder`物件，並連接到其`IPicture`介面。  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功建立物件。否則便是 0。  
  
##  <a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap  
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
 為非零，如果已成功建立物件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**、 呼叫端不應該使用點陣圖或以任何方式在這個呼叫之後的調色盤物件傳回。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保圖片物件的存留期間點陣圖和調色盤物件維持有效。  
  
##  <a name="createfromicon"></a>CPictureHolder::CreateFromIcon  
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
 為非零，如果已成功建立物件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**，呼叫端不應該使用 icon 物件以任何方式之後，這個呼叫會傳回。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保圖示物件圖片物件的存留期間就持續有效。  
  
##  <a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile  
 使用中繼檔初始化中的圖片物件`CPictureHolder`。  
  
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
 為非零，如果已成功建立物件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果`bTransferOwnership`是**TRUE**，呼叫端不應該使用中繼檔物件以任何方式之後，這個呼叫會傳回。 如果`bTransferOwnership`是**FALSE**，呼叫端會負責確保中繼檔物件的存留期圖片物件就持續有效。  
  
##  <a name="getdisplaystring"></a>CPictureHolder::GetDisplayString  
 擷取容器的屬性瀏覽器中顯示的字串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>參數  
 `strValue`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)要保存的顯示字串。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果成功擷取字串。否則便是 0。  
  
##  <a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch  
 此函式傳回的指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CPictureHolder`物件的`IPictureDisp`介面。  
  
### <a name="remarks"></a>備註  
 呼叫端必須呼叫**發行**當它完成時，此指標上。  
  
##  <a name="gettype"></a>CPictureHolder::GetType  
 指出圖片是點陣圖，中繼檔或圖示。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 值，指出類型的圖片。 可能的值和其意義如下：  
  
|值|意義|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder`物件被 unititialized。|  
|**PICTYPE_NONE**|`CPictureHolder`物件是空的。|  
|**PICTYPE_BITMAP**|圖片是點陣圖。|  
|**PICTYPE_METAFILE**|圖片會在中繼檔。|  
|**PICTYPE_ICON**|圖片顯示為圖示。|  
  
##  <a name="m_ppict"></a>CPictureHolder::m_pPict  
 指標`CPictureHolder`物件的`IPicture`介面。  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>Cpictureholder:: Render  
 呈現所參考的矩形中的圖片`rcRender`。  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 圖片為轉譯的顯示內容的指標。  
  
 `rcRender`  
 圖片為呈現的矩形。  
  
 *rcWBounds*  
 表示轉譯圖片物件的週框的矩形。 控制項，這個矩形是`rcBounds`參數傳遞給的覆寫[COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw)。  
  
##  <a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch  
 連接`CPictureHolder`物件`IPictureDisp`介面。  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 新的指標`IPictureDisp`介面。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder 類別](../../mfc/reference/cfontholder-class.md)
