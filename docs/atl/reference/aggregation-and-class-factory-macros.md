---
title: 彙總與類別的 Factory 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
dev_langs:
- C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8569d4ecbbd74a6d2d37701a4ec22e56cbe9f100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366415"
---
# <a name="aggregation-and-class-factory-macros"></a>彙總與類別的 Factory 巨集
這些巨集提供方式控制彙總並宣告 class factory。  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|宣告可以是您的物件 （預設值） 的彙總資料。|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|宣告為的 class factory [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，ATL 預設 class factory。|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|宣告您要的 class factory 的類別處理站物件。|  
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|宣告[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)為 class factory。|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|宣告[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)為 class factory。|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|宣告[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)為 class factory。|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|宣告虛擬`GetControllingUnknown`函式。|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|宣告您的物件不能彙總。|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|宣告必須彙總物件。|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|檢查外部未知的值，並彙總或不可彙總則，視需要宣告您的物件。|  
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|內部物件的建構期間刪除可防止在外部物件。|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定**forced VIEWSTATUS**旗標的容器。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
   
##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE  
 指定可以彙總物件。  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您會定義為彙總的類別名稱。  
  
### <a name="remarks"></a>備註  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含這個巨集來指定預設彙總模型。 若要覆寫此預設值，指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)類別定義中的巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY  
 宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為 class factory。  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>備註  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)宣告物件的預設 class factory 會使用這個巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>  CComClassFactory 類別  
 這個類別會實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面。  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>備註  
 `CComClassFactory` 實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面，其中包含用於建立特定的 CLSID 的物件，以及鎖定以允許更快速地建立新物件的記憶體中的 class factory 方法。 **IClassFactory**必須針對您在系統登錄中，並為您指派為 CLSID 註冊每個類別中實作。  
  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要覆寫此預設值，指定的其中一個`DECLARE_CLASSFACTORY` *XXX*類別定義中的巨集。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)巨集的 class factory 中用於指定的類別：  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 上述類別定義指定**CMyClassFactory**將使用做為物件的預設 class factory。 **CMyClassFactory**必須衍生自`CComClassFactory`並覆寫`CreateInstance`。  
  
 ATL 提供三個其他宣告 class factory 的巨集：  
  
- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，這會控制透過授權建立。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，這會在多個 apartment 中建立物件。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，這會建構一個[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。  
  
##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX  
 宣告`cf`為 class factory。  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 [in]實作您類別的 factory 物件的類別名稱。  
  
### <a name="remarks"></a>備註  
 `cf`參數必須衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並覆寫`CreateInstance`方法。  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，指定`CComClassFactory`做為預設 class factory。 不過，透過包括`DECLARE_CLASSFACTORY_EX`巨集物件的類別定義，在您覆寫此預設值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2  
 宣告[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)為 class factory。  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>參數  
 *授權*  
 [in]類別可實作`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。  
  
### <a name="remarks"></a>備註  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，透過包括`DECLARE_CLASSFACTORY2`巨集物件的類別定義，在您覆寫此預設值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>  CComClassFactory2 類別  
 這個類別會實作[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)介面。  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>參數  
 *授權*  
 實作下列靜態函式的類別：  
  
- **靜態 BOOL VerifyLicenseKey (BSTR** `bstr` **);**  
  
- **靜態 BOOL GetLicenseKey (DWORD** `dwReserved` **，BSTR\***  `pBstr` **);**  
  
- **靜態 BOOL IsLicenseValid （);**  
  
### <a name="remarks"></a>備註  
 `CComClassFactory2` 實作[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)介面的擴充功能的[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)。 **IClassFactory2**控制項物件透過授權建立。 類別處理站執行授權的電腦上，可以提供執行階段授權金鑰。 這個授權金鑰可讓應用程式的完整電腦授權不存在時，將物件具現化。  
  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**，在樣板參數`CComClassFactory2`，必須實作的靜態函式`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 以下是簡單的授權類別的範例：  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2` 衍生自兩者**CComClassFactory2Base**和*授權*。 **CComClassFactory2Base**，又，衍生自**IClassFactory2**和**CComObjectRootEx\< CComGlobalsThreadModel >**。  
  
##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD  
 宣告[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)為 class factory。  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>備註  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，透過包括`DECLARE_CLASSFACTORY_AUTO_THREAD`巨集物件的類別定義，在您覆寫此預設值。  
  
 當您建立的物件 （在跨處理序伺服器） 中的多個 apartment 中時，新增`DECLARE_CLASSFACTORY_AUTO_THREAD`到您的類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>  CComClassFactoryAutoThread 類別  
 這個類別會實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面，並允許在多個 apartment 中建立的物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>備註  
 `CComClassFactoryAutoThread` 類似於[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許在多個 apartment 中建立的物件。 若要利用這項支援，衍生您的 EXE 模組從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON  
 宣告[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)為 class factory。  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>參數  
 `obj`  
 [in]類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，透過包括`DECLARE_CLASSFACTORY_SINGLETON`巨集物件的類別定義，在您覆寫此預設值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>  CComClassFactorySingleton 類別  
 此類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>參數  
 `T`  
 您的類別。  
  
 `CComClassFactorySingleton` 衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。 每次呼叫`CreateInstance`方法只會查詢此物件的介面指標。  
  
### <a name="remarks"></a>備註  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN  
 虛擬函式宣告為`GetControllingUnknown`。  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>備註  
 這個巨集新增至您的物件，您會得到編譯器錯誤訊息，如果`GetControllingUnknown`是未定義 (例如，在**CComAggregateCreator**)。  
  
##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE  
 指定您的物件不能彙總。  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要定義為 not aggregatable 類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 `DECLARE_NOT_AGGREGATABLE` 會導致`CreateInstance`傳回錯誤 ( **CLASS_E_NOAGGREGATION**) 如果您嘗試要彙總到您的物件。  
  
 根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)巨集，指定可以彙總物件。 若要覆寫此預設行為，包括`DECLARE_NOT_AGGREGATABLE`類別定義中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE  
 指定您的物件必須彙總。  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您定義成只可彙總的類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 `DECLARE_ONLY_AGGREGATABLE` 會導致錯誤 ( **E_FAIL**) 如果嘗試對**CoCreate**您為非彙總物件的物件。  
  
 根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)巨集，指定可以彙總物件。 若要覆寫此預設行為，包括`DECLARE_ONLY_AGGREGATABLE`類別定義中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE  
 指定的執行個體**CComPolyObject \<**  *x* **>** 建立您的物件時所建立。  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要定義為彙總或不可彙總則類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 在建立期間，會檢查的外部未知的值。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部未知**NULL**， **IUnknown**彙總物件，則實作。  
  
 使用的優點`DECLARE_POLY_AGGREGATABLE`是，您可以避免必須同時`CComAggObject`和`CComObject`處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 這表示您可以在模組中存在 vtable 只能有一個複本和一份函式。 如果您的 vtable 很大，這可以大幅降低模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`會造成較大的模組大小因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
 `DECLARE_POLY_AGGREGATABLE`巨集就會自動宣告物件中如果您使用 ATL 控制項精靈建立的完整控制權。  
  
##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT  

 保護您的物件遭到刪除 (期間[跖](ccomobjectrootex-class.md#finalconstruct)) 內部彙總的物件會遞增參考計數則遞減的計數為 0。  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS  
 將這個巨集放在 ATL ActiveX 控制項的控制項類別，以指定**forced VIEWSTATUS**旗標的容器。  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>參數  
 `statusFlags`  
 [in]**Forced VIEWSTATUS**旗標。 請參閱[forced VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)旗標的清單。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)
