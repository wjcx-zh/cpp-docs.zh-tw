---
title: "CFontHolder 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFontHolder
dev_langs:
- C++
helpviewer_keywords:
- custom fonts
- CFontHolder class
- fonts, ActiveX controls
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
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
ms.openlocfilehash: fdfa16756ff218159087969f2a4967ed5e76a445
ms.lasthandoff: 02/24/2017

---
# <a name="cfontholder-class"></a>CFontHolder 類別
實作內建字型屬性，並封裝 Windows 字型物件和 `IFont` 介面的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|建構 `CFontHolder` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|擷取容器的屬性瀏覽器中顯示的字串。|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|傳回字型的`IDispatch`介面。|  
|[CFontHolder::GetFontHandle](#getfonthandle)|傳回 Windows 字型的控制代碼。|  
|[CFontHolder::InitializeFont](#initializefont)|初始化`CFontHolder`物件。|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|擷取資訊相關的字型。|  
|[CFontHolder::ReleaseFont](#releasefont)|中斷連接`CFontHolder`物件從`IFont`和`IFontNotification`介面。|  
|[CFontHolder::Select](#select)|選取字型資源放入裝置內容。|  
|[CFontHolder::SetFont](#setfont)|連接`CFontHolder`物件傳遞給`IFont`介面。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|指標`CFontHolder`物件的`IFont`介面。|  
  
## <a name="remarks"></a>備註  
 `CFontHolder`沒有基底類別。  
  
 使用此類別來實作自訂的字型屬性，為您的控制項。 如需建立這類屬性的資訊，請參閱文章[ActiveX 控制項︰ 使用字型](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CFontHolder`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-namecfontholdera--cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder  
 建構 `CFontHolder` 物件。  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>參數  
 *pNotify*  
 字型的指標`IPropertyNotifySink`介面。  
  
### <a name="remarks"></a>備註  
 您必須呼叫`InitializeFont`使用之前，先初始化產生的物件。  
  
##  <a name="a-namegetdisplaystringa--cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 擷取容器的屬性瀏覽器中可能顯示的字串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>參數  
 `strValue`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)要保存的顯示字串。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功擷取的字串。否則為 0。  
  
##  <a name="a-namegetfontdispatcha--cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 呼叫此函式可擷取的字型分派介面的指標。  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CFontHolder`物件的**IFontDisp**介面。 請注意，呼叫此函式`GetFontDispatch`必須呼叫`IUnknown::Release`當它完成後，此介面指標上。  
  
### <a name="remarks"></a>備註  
 呼叫`InitializeFont`之前，先呼叫`GetFontDispatch`。  
  
##  <a name="a-namegetfonthandlea--cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 呼叫此函式可取得 Windows 字型的控制代碼。  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>參數  
 `cyLogical`  
 以邏輯單位，繪製控制項的矩形的高度。  
  
 `cyHimetric`  
 高度，請在`MM_HIMETRIC`個控制項。  
  
### <a name="return-value"></a>傳回值  
 物件控制代碼的字型。否則**NULL**。  
  
### <a name="remarks"></a>備註  
 比率`cyLogical`和`cyHimetric`用來計算適當的顯示大小，以邏輯單位，以表示字型的點數大小的`MM_HIMETRIC`單位︰  
  
 顯示大小 = ( `cyLogical`  /  `cyHimetric`) X 字型大小  
  
 不含任何參數的版本控制代碼傳回到螢幕正確調整大小的字型。  
  
##  <a name="a-nameinitializefonta--cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::InitializeFont  
 初始化`CFontHolder`物件。  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pFontDesc`  
 字型描述結構的指標 ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782))，指定字型的特性。  
  
 `pFontDispAmbient`  
 容器的環境字型屬性的指標。  
  
### <a name="remarks"></a>備註  
 如果`pFontDispAmbient`不**NULL**、`CFontHolder`物件所連接的複製品`IFont`容器的環境字型屬性所使用的介面。  
  
 如果`pFontDispAmbient`是**NULL**，會建立新的字型物件可能是來自所指的字型描述`pFontDesc`或者，如果`pFontDesc`是**NULL**，從預設描述。  
  
 呼叫此函式之後建構`CFontHolder`物件。  
  
##  <a name="a-namempfonta--cfontholdermpfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont  
 指標`CFontHolder`物件的`IFont`介面。  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="a-namequerytextmetricsa--cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 擷取有關所代表的實體字型`CFontHolder`物件。  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>參數  
 `lptm`  
 指標[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)來接收資訊的結構。  
  
##  <a name="a-namereleasefonta--cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont  
 此函式中斷`CFontHolder`物件從其`IFont`介面。  
  
```  
void ReleaseFont();
```  
  
##  <a name="a-nameselecta--cfontholderselect"></a><a name="select"></a>CFontHolder::Select  
 呼叫此函式可放入指定的裝置內容中選取控制項的字型。  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 在其中選取字型的裝置內容。  
  
 `cyLogical`  
 以邏輯單位，繪製控制項的矩形的高度。  
  
 `cyHimetric`  
 高度，請在`MM_HIMETRIC`個控制項。  
  
### <a name="return-value"></a>傳回值  
 要被取代的字型指標。  
  
### <a name="remarks"></a>備註  
 請參閱[GetFontHandle](#getfonthandle)的討論`cyLogical`和`cyHimetric`參數。  
  
##  <a name="a-namesetfonta--cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont  
 釋放任何現有的字型，並連接`CFontHolder`物件傳遞給`IFont`介面。  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>參數  
 *pNewFont*  
 新指標`IFont`介面。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPropExchange 類別](../../mfc/reference/cpropexchange-class.md)

