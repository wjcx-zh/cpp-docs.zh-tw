---
title: 匯總和類別 Factory 宏
ms.date: 08/12/2020
f1_keywords:
- ATLCOM/ATL::DECLARE_AGGREGATABLE
- ATLCOM/ATL::DECLARE_CLASSFACTORY
- ATLCOM/ATL::DECLARE_CLASSFACTORY_EX
- ATLCOM/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/ATL::DECLARE_NOT_AGGREGATABLE
- ATLCOM/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_POLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/ATL::DECLARE_VIEW_STATUS
- ATLDEF/ATL::DECLARE_AGGREGATABLE
- ATLDEF/ATL::DECLARE_CLASSFACTORY
- ATLDEF/ATL::DECLARE_CLASSFACTORY_EX
- ATLDEF/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLDEF/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLDEF/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLDEF/ATL::DECLARE_NOT_AGGREGATABLE
- ATLDEF/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_POLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLDEF/ATL::DECLARE_VIEW_STATUS
- ATLCOM/DECLARE_AGGREGATABLE
- ATLCOM/DECLARE_CLASSFACTORY
- ATLCOM/DECLARE_CLASSFACTORY_EX
- ATLCOM/DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/DECLARE_NOT_AGGREGATABLE
- ATLCOM/DECLARE_ONLY_AGGREGATABLE
- ATLCOM/DECLARE_POLY_AGGREGATABLE
- ATLCOM/DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/DECLARE_VIEW_STATUS
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
- DECLARE_AGGREGATABLE
- DECLARE_CLASSFACTORY
- DECLARE_CLASSFACTORY_EX
- DECLARE_CLASSFACTORY_AUTO_THREAD
- DECLARE_CLASSFACTORY_SINGLETON
- DECLARE_GET_CONTROLLING_UNKNOWN
- DECLARE_NOT_AGGREGATABLE
- DECLARE_ONLY_AGGREGATABLE
- DECLARE_POLY_AGGREGATABLE
- DECLARE_PROTECT_FINAL_CONSTRUCT
- DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 5fdf330cfc69ea68720666eae5952be356cad314
ms.sourcegitcommit: 50db6d0a0d640155c9347c1914bc8859efaadd90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88197342"
---
# <a name="aggregation-and-class-factory-macros"></a>匯總和類別 Factory 宏

這些宏提供控制匯總和宣告類別 factory 的方式。

| 巨集 | Description |
|--|--|
| [DECLARE_AGGREGATABLE](#declare_aggregatable) | 宣告您的物件可以 (預設) 匯總。 |
| [DECLARE_CLASSFACTORY](#declare_classfactory) | 宣告要 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)的 Class Factory，即 ATL 預設 Class Factory。 |
| [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) | 將您的 Class Factory 物件宣告為 Class Factory。 |
| [DECLARE_CLASSFACTORY2](#declare_classfactory2) | 將 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 宣告為 Class Factory。 |
| [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) | 將 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 宣告為 Class Factory。 |
| [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) | 將 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 宣告為 Class Factory。 |
| [DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown) | 宣告虛擬 `GetControllingUnknown` 函數。 |
| [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) | 宣告您的物件無法匯總。 |
| [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) | 宣告您的物件必須加以匯總。 |
| [DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable) | 檢查 [外部未知] 的值，並視需要宣告您的物件可匯總或非匯總。 |
| [DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct) | 保護外部物件不會在內建物件的結構中刪除。 |
| [DECLARE_VIEW_STATUS](#declare_view_status) | 指定容器的 VIEWSTATUS 旗標。 |

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a> DECLARE_AGGREGATABLE

指定可以匯總您的物件。

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在您要定義為匯總之類別的名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 包含這個宏來指定預設匯總模型。 若要覆寫此預設值，請在您的類別定義中指定 [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) 或 [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) 宏。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a> DECLARE_CLASSFACTORY

將 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 宣告為 Class Factory。

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 會使用這個宏來宣告物件的預設 Class Factory。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a> CComClassFactory 類別

這個類別會實 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 介面。

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactory` 會執行 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 介面，其中包含用來建立特定 CLSID 物件的方法，以及鎖定記憶體中的 Class Factory，讓新物件可以更快速地建立。 `IClassFactory` 必須針對您在系統登錄中註冊的每個類別，以及您要指派 CLSID 的來執行。

ATL 物件通常會藉由衍生自 [CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏 [DECLARE_CLASSFACTORY](#declare_classfactory)，它會宣告 `CComClassFactory` 為預設 Class Factory。 若要覆寫此預設值，請在您的類別定義中指定其中一個 DECLARE_CLASSFACTORY*XXX* 宏。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) 宏會針對 Class Factory 使用指定的類別：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

上述類別定義 `CMyClassFactory` 會指定將用來做為物件的預設 Class Factory。 `CMyClassFactory` 必須衍生自 `CComClassFactory` ，而且會覆寫 `CreateInstance` 。

ATL 提供其他三個宣告 Class Factory 的宏：

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) 會使用 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，透過授權來控制建立。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) 會使用 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，以在多個單元中建立物件。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) 會使用 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，它會構造單一 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 物件。

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a> DECLARE_CLASSFACTORY_EX

宣告 `cf` 為 Class Factory。

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>參數

*cf*<br/>
在實作為 Class Factory 物件的類別名稱。

### <a name="remarks"></a>備註

*Cf*參數必須衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並覆寫 `CreateInstance` 方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 包含 [DECLARE_CLASSFACTORY](#declare_classfactory) 宏，它會指定 `CComClassFactory` 做為預設 Class Factory。 不過，藉由在物件的類別定義中包含 DECLARE_CLASSFACTORY_EX 宏，就會覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a> DECLARE_CLASSFACTORY2

將 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 宣告為 Class Factory。

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>參數

*.lic*<br/>
在執行 `VerifyLicenseKey` 、和的類別 `GetLicenseKey` `IsLicenseValid` 。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 包含 [DECLARE_CLASSFACTORY](#declare_classfactory) 宏，它會指定 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 做為預設 Class Factory。 不過，藉由在物件的類別定義中包含 DECLARE_CLASSFACTORY2 宏，就會覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a> CComClassFactory2 類別

這個類別會實 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 介面。

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>參數

*執照*<br/>
實作用下列靜態函式的類別：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>備註

`CComClassFactory2` 會執行 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 介面，這是 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的延伸模組。 `IClassFactory2` 透過授權控制物件的建立。 在授權的電腦上執行的 Class Factory 可以提供執行時間授權金鑰。 當完整的電腦授權不存在時，此授權金鑰可讓應用程式具現化物件。

ATL 物件通常會藉由衍生自 [CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏 [DECLARE_CLASSFACTORY](#declare_classfactory)，其會將 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 宣告為預設 Class Factory。 若要使用 `CComClassFactory2` ，請在物件的類別定義中指定 [DECLARE_CLASSFACTORY2](#declare_classfactory2) 宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`，的樣板參數 `CComClassFactory2` 必須實作用、和的靜態函式 `VerifyLicenseKey` `GetLicenseKey` `IsLicenseValid` 。 以下是簡單授權類別的範例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` 衍生自 `CComClassFactory2Base` 和 *授權*。 `CComClassFactory2Base`接著，衍生自 `IClassFactory2` 並** \< CComGlobalsThreadModel > CComObjectRootEx**。

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a> DECLARE_CLASSFACTORY_AUTO_THREAD

將 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 宣告為 Class Factory。

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 包含 [DECLARE_CLASSFACTORY](#declare_classfactory) 宏，它會指定 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 做為預設 Class Factory。 不過，藉由在物件的類別定義中包含 DECLARE_CLASSFACTORY_AUTO_THREAD 宏，就會覆寫此預設值。

當您在跨進程伺服器) 中建立多個單元 (中的物件時，請將 DECLARE_CLASSFACTORY_AUTO_THREAD 新增至您的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a> CComClassFactoryAutoThread 類別

這個類別會實 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 介面，並允許在多個單元中建立物件。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactoryAutoThread` 類似于 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許在多個單元中建立物件。 若要利用這項支援，請從 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)衍生您的 EXE 模組。

ATL 物件通常會藉由衍生自 [CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏 [DECLARE_CLASSFACTORY](#declare_classfactory)，其會將 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 宣告為預設 Class Factory。 若要使用 `CComClassFactoryAutoThread` ，請在物件的類別定義中指定 [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) 宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a> DECLARE_CLASSFACTORY_SINGLETON

將 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 宣告為 Class Factory。

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>參數

*obj*<br/>
在類別物件的名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 包含 [DECLARE_CLASSFACTORY](#declare_classfactory) 宏，它會指定 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 做為預設 Class Factory。 不過，藉由在物件的類別定義中包含 DECLARE_CLASSFACTORY_SINGLETON 宏，就會覆寫此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a> CComClassFactorySingleton 類別

這個類別衍生自 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 來建立單一物件。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別。

`CComClassFactorySingleton` 衍生自 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 來建立單一物件。 每次呼叫 `CreateInstance` 方法時，只會查詢此物件的介面指標。

### <a name="remarks"></a>備註

ATL 物件通常會藉由衍生自 [CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏 [DECLARE_CLASSFACTORY](#declare_classfactory)，它會宣告 `CComClassFactory` 為預設 Class Factory。 若要使用 `CComClassFactorySingleton` ，請在物件的類別定義中指定 [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) 宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a> DECLARE_GET_CONTROLLING_UNKNOWN

宣告虛擬函數 `GetControllingUnknown` 。

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>備註

如果您收到未定義 (的編譯器錯誤訊息 `GetControllingUnknown` （例如) ），請將此宏新增至您的物件 `CComAggregateCreator` 。

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a> DECLARE_NOT_AGGREGATABLE

指定無法匯總您的物件。

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在您要定義為不可匯總之類別物件的名稱。

### <a name="remarks"></a>備註

`CreateInstance`如果嘗試在您的物件上進行匯總，DECLARE_NOT_AGGREGATABLE 會導致 (CLASS_E_NOAGGREGATION) 傳回錯誤。

根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md) 會包含 [DECLARE_AGGREGATABLE](#declare_aggregatable) 宏，這會指定您的物件可以匯總。 若要覆寫此預設行為，請在您的類別定義中包含 DECLARE_NOT_AGGREGATABLE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a> DECLARE_ONLY_AGGREGATABLE

指定您的物件必須加以匯總。

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在您要定義為僅匯總之類別物件的名稱。

### <a name="remarks"></a>備註

如果您的物件是非匯總物件的嘗試，DECLARE_ONLY_AGGREGATABLE 會導致 (E_FAIL) 錯誤 `CoCreate` 。

根據預設， [CComCoClass](../../atl/reference/ccomcoclass-class.md) 會包含 [DECLARE_AGGREGATABLE](#declare_aggregatable) 宏，這會指定您的物件可以匯總。 若要覆寫此預設行為，請在您的類別定義中包含 DECLARE_ONLY_AGGREGATABLE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a> DECLARE_POLY_AGGREGATABLE

指定在建立物件時，建立**CComPolyObject \<** *x* **> **的實例。

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在您要定義為匯總或不可匯總之類別物件的名稱。

### <a name="remarks"></a>備註

在建立期間，會核取 [外部未知] 的值。 如果是 Null， `IUnknown` 則會針對非匯總物件執行。 如果外部未知不是 Null， `IUnknown` 則會針對匯總物件來執行。

使用 DECLARE_POLY_AGGREGATABLE 的優點是，您可以避免在 `CComAggObject` 模組中同時擁有和 `CComObject` 來處理匯總和非匯總案例。 單一 `CComPolyObject` 物件可處理這兩種情況。 這表示只會有一個 vtable 複本，而您的模組中會有一份函數複本。 如果您的 vtable 很大，這可能會大幅降低您的模組大小。 不過，如果您的 vtable 很小，使用 `CComPolyObject` 可能會產生稍微大一點的模組大小，因為它不會針對匯總或非匯總物件進行優化，如同 `CComAggObject` 和 `CComObject` 。

如果您使用 ATL Control Wizard 來建立完全控制，則會在您的物件中自動宣告 DECLARE_POLY_AGGREGATABLE 宏。

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a> DECLARE_PROTECT_FINAL_CONSTRUCT

保護您的物件，以便在 [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) 期間 (時，) 內部匯總物件遞增參考計數，然後將計數遞減為0。

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a> DECLARE_VIEW_STATUS

將此宏放在 ATL ActiveX 控制項的控制項類別中，以指定容器的 VIEWSTATUS 旗標。

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>參數

*statusFlags*<br/>
在VIEWSTATUS 旗標。 如需旗標的清單，請參閱 [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
