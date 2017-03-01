---
title: "CPropExchange 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPropExchange
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange class
- OLE controls, persistence
- controls [MFC], OLE
ms.assetid: ed872180-e770-4942-892a-92139d501fab
caps.latest.revision: 22
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
ms.openlocfilehash: 655d8e2f074c3bd12b1b52ece74efb844c7a9904
ms.lasthandoff: 02/24/2017

---
# <a name="cpropexchange-class"></a>CPropExchange 類別
支援 OLE 控制項的永續性實作。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|交換二進位大型物件 (BLOB) 屬性。|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|交換的字型屬性。|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|交換控制項和檔案之間的屬性。|  
|[CPropExchange::ExchangeProp](#exchangeprop)|交換的任何內建類型的屬性。|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|交換 OLE 控制項的版本號碼。|  
|[CPropExchange::GetVersion](#getversion)|擷取 OLE 控制項的版本號碼。|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|決定屬性交換會以非同步方式進行。|  
|[CPropExchange::IsLoading](#isloading)|指出屬性是否被載入控制項或儲存它。|  
  
## <a name="remarks"></a>備註  
 `CPropExchange`沒有基底類別。  
  
 建立內容和屬性交換的方向。  
  
 持續性是控制項的狀態資訊時，通常由其屬性，控制項本身和媒體之間的交換。  
  
 架構會建構物件衍生自`CPropExchange`時它會通知 OLE 控制項的屬性是從載入或儲存至持續性儲存體。  
  
 架構會將指標傳遞至這個`CPropExchange`物件至控制項的`DoPropExchange`函式。 如果您使用精靈來建立控制項，控制項的起始檔案`DoPropExchange`函式呼叫`COleControl::DoPropExchange`。 基底類別版本交換控制項的內建屬性。您修改您已加入至您的控制項來交換內容的衍生的類別版本。  
  
 `CPropExchange`可用來序列化控制項的屬性，或在初始化時載入或建立控制項的控制項的屬性。 `ExchangeProp`和`ExchangeFontProp`的成員函式`CPropExchange`能夠儲存至屬性，以及從不同的媒體載入它們。  
  
 如需有關使用`CPropExchange`，請參閱文章[MFC ActiveX 控制項︰ 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPropExchange`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-nameexchangeblobpropa--cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp  
 將序列化儲存二進位大型物件 (BLOB) 資料的屬性。  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pszPropName`  
 交換屬性的名稱。  
  
 `phBlob`  
 指標指向變數，來儲存屬性 （變數通常是您的類別的成員）。  
  
 `hBlobDefault`  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 Exchange 已成功; 如果為非零0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值從位址讀取或寫入，，因為已適當情況下，所參考的變數`phBlob`。 如果`hBlobDefault`指定，它將用於做為屬性的預設值。 如果因為任何原因而控制項的序列化失敗，則會使用此值。  
  
 函式**CArchivePropExchange::ExchangeBlobProp**， **CResetPropExchange::ExchangeBlobProp**，和**CPropsetPropExchange::ExchangeBlobProp**覆寫此純虛擬函式。  
  
##  <a name="a-nameexchangefontpropa--cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp  
 交換儲存媒體和控制項之間的字型屬性。  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pszPropName`  
 交換屬性的名稱。  
  
 `font`  
 參考[CFontHolder](../../mfc/reference/cfontholder-class.md)物件，其中包含的字型屬性。  
  
 `pFontDesc`  
 指標[FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)結構，其中包含值初始化的字型屬性的預設狀態時`pFontDispAmbient`是**NULL**。  
  
 `pFontDispAmbient`  
 指標**IFontDisp**介面要用來初始化的字型屬性的預設狀態的字型。  
  
### <a name="return-value"></a>傳回值  
 Exchange 已成功; 如果為非零0，如果不成功。  
  
### <a name="remarks"></a>備註  
 如果正在從媒體載入至控制項的字型屬性，從媒體擷取字型的特性和`CFontHolder`所參考物件`font`會使用它們來初始化。 如果要儲存的字型屬性，會寫入媒體字型物件中的特性。  
  
 函式**CArchivePropExchange::ExchangeFontProp**， **CResetPropExchange::ExchangeFontProp**，和**CPropsetPropExchange::ExchangeFontProp**覆寫此純虛擬函式。  
  
##  <a name="a-nameexchangepersistentpropa--cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp  
 交換控制項和檔案之間的屬性。  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pszPropName`  
 交換屬性的名稱。  
  
 `ppUnk`  
 包含屬性的指標變數的指標**IUnknown** （這個變數通常是您的類別的成員） 的介面。  
  
 `iid`  
 介面上的控制項將會使用屬性的介面 ID。  
  
 `pUnkDefault`  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 Exchange 已成功; 如果為非零0，如果不成功。  
  
### <a name="remarks"></a>備註  
 如果屬性從檔案載入至控制項，此屬性是建立並從檔案初始化。 如果儲存屬性時，其值會寫入至檔案。  
  
 函式**CArchivePropExchange::ExchangePersistentProp**， **CResetPropExchange::ExchangePersistentProp**，和**CPropsetPropExchange::ExchangePersistentProp**覆寫此純虛擬函式。  
  
##  <a name="a-nameexchangepropa--cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp  
 交換儲存媒體和控制項之間的屬性。  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>參數  
 `pszPropName`  
 交換屬性的名稱。  
  
 `vtProp`  
 符號，指定要交換之屬性的型別。 可能的值為：  
  
|符號|屬性類型|  
|------------|-------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_BOOL`|**BOOL**|  
|`VT_BSTR`|`CString`|  
|`VT_CY`|**CY**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
  
 `pvProp`  
 屬性的值的指標。  
  
 *pvDefault*  
 屬性的預設值的指標。  
  
### <a name="return-value"></a>傳回值  
 Exchange 已成功; 如果為非零0，如果不成功。  
  
### <a name="remarks"></a>備註  
 如果正在從媒體載入至控制項的屬性，屬性的值會從媒體擷取，並儲存在所指向的物件`pvProp`。 如果屬性儲存為 「 中 」，將物件的值所指`pvProp`寫入至媒體。  
  
 函式**CArchivePropExchange::ExchangeProp**， **CResetPropExchange::ExchangeProp**，和**CPropsetPropExchange::ExchangeProp**覆寫此純虛擬函式。  
  
##  <a name="a-nameexchangeversiona--cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion  
 若要處理的版本號碼的持續性架構呼叫。  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>參數  
 *dwVersionLoaded*  
 參考變數，將儲存所載入的永續性資料的版本號碼。  
  
 `dwVersionDefault`  
 控制項的目前版本號碼。  
  
 `bConvert`  
 指出是否要永續性資料轉換成目前的版本，或將它放在已載入的版本相同。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
##  <a name="a-namegetversiona--cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion  
 呼叫此函式可擷取控制項的版本號碼。  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>傳回值  
 控制版本號碼。  
  
##  <a name="a-nameisasynchronousa--cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange::IsAsynchronous  
 決定屬性交換會以非同步方式進行。  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 TRUE，如果屬性被交換以非同步的方式，否則為 FALSE。  
  
##  <a name="a-nameisloadinga--cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange::IsLoading  
 呼叫此函式來判斷屬性是否在控制項載入或儲存它。  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>傳回值  
 正在載入內容; 如果為非零否則為 0。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)




