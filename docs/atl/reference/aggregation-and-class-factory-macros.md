---
title: 彙總與 Class Factory 巨集 |Microsoft Docs
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
ms.openlocfilehash: 7115d73319dc7b76386367fb93329906cd72a027
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073405"
---
# <a name="aggregation-and-class-factory-macros"></a>彙總與 Class Factory 巨集

這些巨集提供的方式控制彙總，並宣告 class factory。

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|宣告您的物件可以是彙總 （預設值）。|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|宣告為的 class factory [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，ATL 預設 class factory。|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|宣告您類別處理站物件的 class factory。|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|宣告[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)是 class factory。|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|宣告[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)是 class factory。|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|宣告[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)是 class factory。|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|宣告虛擬`GetControllingUnknown`函式。|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|宣告您的物件不能彙總。|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|宣告您的物件必須加以彙總。|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|檢查外部未知的值，並彙總或不可彙總則，視需要宣告您的物件。|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|內部物件的建構期間刪除可防止外部物件。|
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定容器的 forced VIEWSTATUS 旗標。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE

指定可以彙總您的物件。

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您會定義為彙總的類別名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含此巨集來指定預設彙總模型。 若要覆寫此預設值，指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或是[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)類別定義中的巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY

宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)是 class factory。

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)來宣告物件的預設 class factory 會使用這個巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>  CComClassFactory 類別

這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactory` 會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，其中包含用於建立特定的 CLSID 的物件，以及鎖定的 class factory，以允許更快速地建立新物件的記憶體中的方法。 `IClassFactory` 必須針對您要註冊在系統登錄，並將您指派為 CLSID 的每個類別實作。

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要覆寫此預設值，請指定其中一個 DECLARE_CLASSFACTORY*XXX*類別定義中的巨集。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)巨集的 class factory 會使用指定的類別：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

上述的類別定義指定`CMyClassFactory`將用於做為物件的預設 class factory。 `CMyClassFactory` 必須衍生自`CComClassFactory`，並覆寫`CreateInstance`。

ATL 提供三個其他宣告 class factory 的巨集：

- [DECLARE_CLASSFACTORY2](#declare_classfactory2)會使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，這會控制透過授權的建立。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)會使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，這會建立在多個 apartment 中的物件。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)會使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，這會建構單一[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX

宣告`cf`是 class factory。

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>參數

*cf*<br/>
[in]實作您類別的 factory 物件的類別名稱。

### <a name="remarks"></a>備註

*Cf*參數必須衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並覆寫`CreateInstance`方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，其指定`CComClassFactory`做為預設 class factory。 不過，藉由在您的物件類別定義中包含 DECLARE_CLASSFACTORY_EX 巨集，您覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2

宣告[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)是 class factory。

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>參數

*授權*<br/>
[in]類別若實作`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，其指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，藉由在您的物件類別定義中包含 DECLARE_CLASSFACTORY2 巨集，您覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>  CComClassFactory2 類別

這個類別會實作[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)介面。

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>參數

*授權*<br/>
類別若實作下列靜態函式：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>備註

`CComClassFactory2` 會實作[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)介面，這是延伸模組的[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)。 `IClassFactory2` 透過授權的控制項物件建立。 類別處理站執行已授權的電腦上，可以提供執行階段授權金鑰。 這種授權金鑰可讓應用程式的完整機器授權不存在時，具現化物件。

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)物件的類別定義中的巨集。 例如: 

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`要與範本參數`CComClassFactory2`，必須實作的靜態函式`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 以下是簡單的授權類別的範例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` 衍生自兩者`CComClassFactory2Base`並*授權*。 `CComClassFactory2Base`反而是衍生自`IClassFactory2`並**CComObjectRootEx\< CComGlobalsThreadModel >**。

##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD

宣告[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)是 class factory。

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，其指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，藉由在您的物件類別定義中包含 DECLARE_CLASSFACTORY_AUTO_THREAD 巨集，您覆寫此預設值。

當您在多個 （跨處理序伺服器） 中的 apartment 中建立物件時，將 DECLARE_CLASSFACTORY_AUTO_THREAD 新增至您的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>  CComClassFactoryAutoThread 類別

這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，並允許在多個 apartment 中建立的物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactoryAutoThread` 類似於[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許在多個 apartment 中建立的物件。 若要利用這項支援，衍生您的 EXE 模組，從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)物件的類別定義中的巨集。 例如: 

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON

宣告[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)是 class factory。

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>參數

*obj*<br/>
[in]您的類別物件的名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)巨集，其指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 不過，藉由在您的物件類別定義中包含 DECLARE_CLASSFACTORY_SINGLETON 巨集，您覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>  CComClassFactorySingleton 類別

這個類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別。

`CComClassFactorySingleton` 衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。 每次呼叫`CreateInstance`方法只會查詢此物件的介面指標。

### <a name="remarks"></a>備註

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)物件的類別定義中的巨集。 例如: 

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN

虛擬函式宣告`GetControllingUnknown`。

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>備註

將這個巨集新增至您的物件，如果您收到編譯器錯誤訊息，指出`GetControllingUnknown`未定義 (例如，在`CComAggregateCreator`)。

##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE

指定您的物件不能彙總。

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您會定義為不可彙總則類別物件的名稱。

### <a name="remarks"></a>備註

DECLARE_NOT_AGGREGATABLE 導致`CreateInstance`傳回錯誤 (CLASS_E_NOAGGREGATION)，如果嘗試要到您的物件上的彙總。

根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)巨集，指定可以彙總您的物件。 若要覆寫此預設行為，請包含 DECLARE_NOT_AGGREGATABLE 類別定義中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE

指定您的物件必須加以彙總。

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您會定義為只可彙總的類別物件的名稱。

### <a name="remarks"></a>備註

如果嘗試對 DECLARE_ONLY_AGGREGATABLE 會造成錯誤 (E_FAIL)`CoCreate`您物件做為非彙總的物件。

根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)巨集，指定可以彙總您的物件。 若要覆寫此預設行為，請包含 DECLARE_ONLY_AGGREGATABLE 類別定義中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE

指定的執行個體**CComPolyObject \<**  *x* **>** 在建立物件時所建立。

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您會定義為彙總或不可彙總則類別物件的名稱。

### <a name="remarks"></a>備註

在建立期間，會檢查的外部未知的值。 如果它是 NULL，`IUnknown`實作非彙總的物件。 如果不是 NULL，外部未知`IUnknown`會彙總物件的實作。

使用 DECLARE_POLY_AGGREGATABLE 的優點是，您不需要同時`CComAggObject`和`CComObject`處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 這表示只有一個複本的 vtable 和一份函式存在於您的模組。 如果您的 vtable 很大，這可以大幅降低您的模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`可能會導致稍微大一點的模組大小因為它不會最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。

如果您使用 [ATL 控制項精靈] 來建立完整的控制權，就會自動 DECLARE_POLY_AGGREGATABLE 巨集宣告在您的物件。

##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT

保護您的物件遭到刪除 (期間[跖](ccomobjectrootex-class.md#finalconstruct)) 內部彙總的物件遞增參考計數則遞減為 0。

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS

將這個巨集放在 ATL ActiveX 控制項的控制項類別，以指定容器的 forced VIEWSTATUS 旗標。

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>參數

*statusFlags*<br/>
[in]Forced VIEWSTATUS 旗標。 請參閱[forced VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus)旗標的清單。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
