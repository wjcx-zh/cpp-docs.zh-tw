---
title: "分派對應 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps. macros
- dispatch maps
- dispatch map macros
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 48e5d1fe207089733caa5ed9e8ca30c2de21f95f
ms.lasthandoff: 02/24/2017

---
# <a name="dispatch-maps"></a>分派對應
OLE Automation 提供方式呼叫方法，及跨應用程式中存取屬性。 Microsoft Foundation 類別庫發送這些要求所提供的機制是 「 分派對應 」 指定物件的函式和屬性，以及本身的屬性和函式引數的資料類型的內部和外部名稱。  
  
### <a name="dispatch-maps"></a>分派對應  
  
|||  
|-|-|  
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|宣告分派對應將用於公開類別的方法和屬性 （必須使用在類別宣告中）。|  
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|啟動分派對應的定義。|  
|[END_DISPATCH_MAP](#end_dispatch_map)|結束分派對應的定義。|  
|[DISP_FUNCTION](#disp_function)|分派對應中用來定義 OLE automation 函式。|  
|[DISP_PROPERTY](#disp_property)|定義 OLE automation 屬性。|  
|[DISP_PROPERTY_EX](#disp_property_ex)|定義 OLE automation 屬性和名稱的 Get 和 Set 函式。|  
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定義 OLE automation 屬性通知。|  
|[DISP_PROPERTY_PARAM](#disp_property_param)|定義 OLE automation 屬性的 Get 和 Set 函式採用參數和名稱。|  
|[DISP_DEFVALUE](#disp_defvalue)|將現有的屬性設為物件的預設值。|  
  
##  <a name="a-namedeclaredispatchmapa--declaredispatchmap"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP  
 如果`CCmdTarget`-衍生的類別，在程式中支援 OLE Automation，類別必須提供公開其方法和屬性的分派對應。  
  
```   
DECLARE_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>備註  
 使用`DECLARE_DISPATCH_MAP`巨集，在類別宣告的結尾。 然後，在。CPP 檔案所定義的成員函式類別，請使用`BEGIN_DISPATCH_MAP`巨集。 然後在每個類別的公開方法和屬性包含巨集項目 ( `DISP_FUNCTION`， `DISP_PROPERTY`，依此類推)。 最後，使用`END_DISPATCH_MAP`巨集。  
  
> [!NOTE]
>  如果您宣告之後的任何成員`DECLARE_DISPATCH_MAP`，您必須指定新的存取類型 (**公用**， `private`，或`protected`) 它們。  
  
 應用程式精靈和程式碼精靈會協助建立 Automation 類別和維護分派對應。 如需有關分派對應的詳細資訊，請參閱[Automation 伺服程式](../../mfc/automation-servers.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAutomation #&10;](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]  

### <a name="requirements"></a>需求  
 **標題:** afxwin.h  

##  <a name="a-namebegindispatchmapa--begindispatchmap"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP  
 宣告您的分派對應的定義。  
  
```  
BEGIN_DISPATCH_MAP(theClass, baseClass)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 指定擁有此分派對應之類別的名稱。  
  
 `baseClass`  
 指定 `theClass` 的基底類別名稱。  
  
### <a name="remarks"></a>備註  
 在為您的類別定義成員函式的實作 (.cpp) 檔案中，使用 `BEGIN_DISPATCH_MAP` 巨集啟動分派對應，為每個分派函式和屬性新增巨集項目，然後使用 `END_DISPATCH_MAP` 巨集完成分派對應。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  

##  <a name="a-nameenddispatchmapa--enddispatchmap"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP  
 結束您的分派對應的定義。  
  
```   
END_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>備註  
 必須與 `BEGIN_DISPATCH_MAP` 搭配使用。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  

##  <a name="a-namedispfunctiona--dispfunction"></a><a name="disp_function"></a>DISP_FUNCTION  
 分派對應中定義的 OLE automation 函式。  
  
```   
DISP_FUNCTION(
  theClass, 
  pszName, 
  pfnMember, 
  vtRetVal, 
  vtsParams)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 外部函式的名稱。  
  
 `pfnMember`  
 成員函式的名稱。  
  
 `vtRetVal`  
 值，指定函式的傳回型別。  
  
 `vtsParams`  
 指定函式的參數清單的一個或多個常數以空格分隔清單。  
  
### <a name="remarks"></a>備註  
 `vtRetVal`引數的型別是**VARTYPE**。 以下的可能值為這個引數取自`VARENUM`列舉型別︰  
  
|符號|傳回型別|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `vtsParams`引數是以空格分隔的清單中的值**VTS_**常數。 一或多個以空格 （不是逗號） 分隔這些值會指定函式的參數清單。 例如： 
  
 [!code-cpp[NVC_MFCAutomation #&14;](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]  
  
 指定包含短整數後面短整數指標的清單。  
  
 **VTS_**常數和其意義如下︰  
  
|符號|參數類型|  
|------------|--------------------|  
|**VTS_I2**|`Short`|  
|**VTS_I4**|`Long`|  
|**VTS_R4**|**浮點數**|  
|**VTS_R8**|`Double`|  
|**VTS_CY**|**const CY**或**CY\***|  
|**VTS_DATE**|**日期**|  
|**VTS_BSTR**|`LPCSTR`|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**const 變異\***或**VARIANT i**|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_PI2**|**簡短\***|  
|**VTS_PI4**|**長\***|  
|**VTS_PR4**|**浮點數\***|  
|**VTS_PR8**|**double\***|  
|**VTS_PCY**|**CY\***|  
|**VTS_PDATE**|**日期\***|  
|**VTS_PBSTR**|**BSTR\***|  
|**VTS_PDISPATCH**|**LPDISPATCH\***|  
|**VTS_PSCODE**|**SCODE\***|  
|**VTS_PBOOL**|**BOOL\***|  
|**VTS_PVARIANT**|**VARIANT\***|  
|**VTS_PUNKNOWN**|**LPUNKNOWN\***|  
|**VTS_NONE**|沒有參數|  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

##  <a name="a-namedisppropertya--dispproperty"></a><a name="disp_property"></a>DISP_PROPERTY  
 分派對應中定義的 OLE automation 屬性。  
  
```   
DISP_PROPERTY(
  theClass, 
  pszName, 
  memberName, 
  vtPropType)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性外部名稱。  
  
 `memberName`  
 成員變數中儲存屬性的名稱。  
  
 `vtPropType`  
 值，指定屬性的型別。  
  
### <a name="remarks"></a>備註  
 `vtPropType`引數的型別是**VARTYPE**。 可能的值，這個引數取自`VARENUM`列舉型別︰  
  
|符號|**屬性類型**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 當外部用戶端變更的屬性，指定的成員變數的值`memberName`變更; 沒有變更的通知。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

##  <a name="a-namedisppropertyexa--disppropertyex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX  
 用來取得及設定屬性的值，在分派對應的函式定義 OLE automation 屬性和名稱。  
  
```   
DISP_PROPERTY_EX(
  theClass, 
  pszName, 
  memberGet, 
  memberSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性外部名稱。  
  
 `memberGet`  
 用於取得屬性的成員函式的名稱。  
  
 `memberSet`  
 用來設定屬性的成員函式的名稱。  
  
 `vtPropType`  
 值，指定屬性的型別。  
  
### <a name="remarks"></a>備註  
 `memberGet`和`memberSet`函式具有簽章由`vtPropType`引數。 `memberGet`函式不接受引數並傳回所指定型別的值`vtPropType`。 `memberSet`函式的引數所指定型別的`vtPropType`並會傳回任何資料。  
  
 `vtPropType`引數的型別是**VARTYPE**。 可能的值，這個引數取自`VARENUM`列舉型別。 如需這些值的清單，請參閱備註`vtRetVal`中的參數[DISP_FUNCTION](#disp_function)。 請注意， `VT_EMPTY`，列在`DISP_FUNCTION`註解、 不允許做為屬性的資料類型。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

##  <a name="a-namedisppropertynotifya--disppropertynotify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY  
 定義 OLE automation 屬性與通知分派對應中。  
  
```   
DISP_PROPERTY_NOTIFY(
  theClass, 
  szExternalName, 
  memberName, 
  pfnAfterSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 `szExternalName`  
 屬性外部名稱。  
  
 `memberName`  
 成員變數中儲存屬性的名稱。  
  
 `pfnAfterSet`  
 通知函式的名稱`szExternalName`。  
  
 `vtPropType`  
 值，指定屬性的型別。  
  
### <a name="remarks"></a>備註  
 不像屬性以定義`DISP_PROPERTY`，與定義的屬性`DISP_PROPERTY_NOTIFY`會自動呼叫所指定的函數`pfnAfterSet`屬性變更時。  
  
 `vtPropType`引數的型別是**VARTYPE**。 可能的值，這個引數取自`VARENUM`列舉型別︰  
  
|符號|**屬性類型**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

##  <a name="a-namedisppropertyparama--disppropertyparam"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM  
 存取使用不同的屬性會定義**取得**和`Set`成員函式。  
  
```   
DISP_PROPERTY_PARAM(
  theClass, 
  pszExternalName, 
  pfnGet, 
  pfnSet, 
  vtPropType,
  vtsParams)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 *pszExternalName*  
 屬性外部名稱。  
  
 `pfnGet`  
 用於取得屬性的成員函式的名稱。  
  
 `pfnSet`  
 用來設定屬性的成員函式的名稱。  
  
 `vtPropType`  
 值，指定屬性的型別。  
  
 `vtsParams`  
 以空格分隔的字串**VTS_**變異參數類型，一個用於每個參數。  
  
### <a name="remarks"></a>備註  
 不同於`DISP_PROPERTY_EX`巨集，此巨集讓您指定之屬性的參數清單。 這可用於實作會編製索引或參數化屬性。  
  
### <a name="example"></a>範例  
 請考慮下列宣告的 get 和設定成員函式可讓使用者存取屬性時，要求特定資料列和資料行︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&9;](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]  
  
 這些會對應至下列`DISP_PROPERTY_PARAM`中控制項分派對應巨集︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&10;](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]  
  
 另一個範例，請考慮下列取得並設定成員函式︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&11;](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]  
  
 這些會對應至下列`DISP_PROPERTY_PARAM`中控制項分派對應巨集︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&12;](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

##  <a name="a-namedispdefvaluea--dispdefvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE  
 將現有的屬性設為物件的預設值。  
  
```   
DISP_DEFVALUE(theClass, pszName)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性外部名稱，表示物件的｢值｣。  
  
### <a name="remarks"></a>備註  
 使用預設值可以使設計 Visual Basic 應用程式的自動化物件時更為簡單。  
  
 您的物件的「預設值」就是物件的參考不指定屬性或成員函式時，所擷取或設定的屬性。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h 

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

