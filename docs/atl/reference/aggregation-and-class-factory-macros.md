---
title: 聚合和類工廠宏
ms.date: 11/04/2016
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
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319329"
---
# <a name="aggregation-and-class-factory-macros"></a>聚合和類工廠宏

這些宏提供了控制聚合和聲明類工廠的方法。

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|聲明可以聚合物件(預設值)。|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|聲明類工廠為[CComClassFactory,ATL](../../atl/reference/ccomclassfactory-class.md)預設類工廠。|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|將類工廠物件聲明為類工廠。|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|聲明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)為類工廠。|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|聲明[CComClass 工廠自動線程](../../atl/reference/ccomclassfactoryautothread-class.md)為類工廠。|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|宣佈[CComClass 工廠單頓](../../atl/reference/ccomclassfactorysingleton-class.md)為類工廠。|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|聲明虛擬`GetControllingUnknown`函數。|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|聲明無法聚合物件。|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|聲明必須聚合物件。|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|檢查外部未知值,並酌情聲明物件可聚合或不可聚合。|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|在內部物件構造期間保護外部物件不刪除。|
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定容器的「檢視狀態」 標誌。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

指定可以聚合物件。

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要定義為聚合的類的名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含此宏以指定預設聚合模型。 要重寫此預設值,請在類定義中指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)宏。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

聲明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為類工廠。

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)使用此宏聲明物件的預設類工廠。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClass 工廠類別

此類實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactory`實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面,其中包含用於創建特定CLSID物件的方法,以及將類工廠鎖定在記憶體中,以便更快地創建新物件。 `IClassFactory`必須針對在系統註冊表中註冊併為其分配 CLSID 的每個類實現。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)`CComClassFactory`,它 聲明為預設類工廠。 要重寫此預設值,請在類定義中指定DECLARE_CLASSFACTORY*XXX*宏之一。 例如[,DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)宏對類工廠使用指定的類:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

上面的類定義指定`CMyClassFactory`將用作對象的預設類工廠。 `CMyClassFactory`必須指定並`CComClassFactory`覆`CreateInstance`寫 。

ATL 提供聲明類工廠的其他三個宏:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md),它控制通過許可證創建的。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md),它可在多個單元中創建物件。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用[CComClassFactory 單一項](../../atl/reference/ccomclassfactorysingleton-class.md),它建構單個[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

聲明`cf`為類工廠。

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>參數

*cf*<br/>
[在]實現類工廠物件的類的名稱。

### <a name="remarks"></a>備註

*cf*參數必須派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並`CreateInstance`重寫該方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏,`CComClassFactory`該宏 指定為預設類工廠。 但是,通過將DECLARE_CLASSFACTORY_EX宏包括在物件的類定義中,可以覆蓋此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

聲明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)為類工廠。

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>參數

*蝨子*<br/>
[在]實`VerifyLicenseKey``GetLicenseKey`作的類別`IsLicenseValid`, 與 。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏,該宏將[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定為預設類工廠。 但是,通過將DECLARE_CLASSFACTORY2宏包括在物件的類定義中,可以覆蓋此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>CComClassFactory2 類別

此類實現[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面。

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>參數

*許可證*<br/>
實作以下靜態函數的類別:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>備註

`CComClassFactory2`實現[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面,這是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的擴展。 `IClassFactory2`通過許可證控制對象創建。 在許可電腦上執行的類工廠可以提供運行時許可證密鑰。 此許可證密鑰允許應用程式在不存在完整的計算機許可證時實例化物件。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](#declare_classfactory),它聲明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為預設類工廠。 要使用`CComClassFactory2`,請在物件的類定義中指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`的`CComClassFactory2`樣本參數必須實現靜態函數`VerifyLicenseKey``GetLicenseKey``IsLicenseValid`和 。 下面是一個簡單的授權類別的範例:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`衍生與`CComClassFactory2Base`*授權*。 `CComClassFactory2Base`,反過來,派生自`IClassFactory2`和**CComObjectRootEx\< CComGlobalsThread模型>**。

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

聲明[CComClass 工廠自動線程](../../atl/reference/ccomclassfactoryautothread-class.md)為類工廠。

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏,該宏將[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定為預設類工廠。 但是,通過將DECLARE_CLASSFACTORY_AUTO_THREAD宏包括在物件的類定義中,可以覆蓋此預設值。

在多個單元(在 proc 伺服器中)創建物件時,將DECLARE_CLASSFACTORY_AUTO_THREAD添加到類中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>CComclass 工廠自動線程類別

此類實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面,並允許在多個單元中創建物件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>備註

`CComClassFactoryAutoThread`類似於[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)但允許在多個公寓中創建物件。 要利用此支援,請從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模組。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](#declare_classfactory),它聲明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為預設類工廠。 要使用`CComClassFactoryAutoThread`,請在物件的類定義中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

宣佈[CComClass 工廠單頓](../../atl/reference/ccomclassfactorysingleton-class.md)為類工廠。

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>參數

*obj*<br/>
[在]類物件的名稱。

### <a name="remarks"></a>備註

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏,該宏將[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定為預設類工廠。 但是,通過將DECLARE_CLASSFACTORY_SINGLETON宏包括在物件的類定義中,可以覆蓋此預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>CComClass 工廠單頓類別

此類派生自[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)並使用[CComObject Global](../../atl/reference/ccomobjectglobal-class.md)構造單個物件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>參數

*T*<br/>
你的班級

`CComClassFactorySingleton`派生自[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)構造單個物件。 對方法`CreateInstance`的每個調用都只是查詢此對象作為介面指標。

### <a name="remarks"></a>備註

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)`CComClassFactory`,它 聲明為預設類工廠。 要使用`CComClassFactorySingleton`,請在物件的類定義中指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

宣告虛擬函數`GetControllingUnknown`。

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>備註

如果收到未定義的編譯器錯誤消息`GetControllingUnknown`(例如,在`CComAggregateCreator`中),則此宏添加到物件。

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

指定無法聚合物件。

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要定義為不可聚合的類物件的名稱。

### <a name="remarks"></a>備註

如果嘗試`CreateInstance`聚合到物件上,DECLARE_NOT_AGGREGATABLE會導致返回錯誤(CLASS_E_NOAGGREGATION)。

默認情況下[,CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏,該宏指定可以聚合物件。 要重寫此默認行為,請在類定義中包括DECLARE_NOT_AGGREGATABLE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

指定必須聚合物件。

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要定義為僅聚合的類物件的名稱。

### <a name="remarks"></a>備註

如果嘗試將對象作為非聚合物件`CoCreate`進行 ,DECLARE_ONLY_AGGREGATABLE會導致錯誤(E_FAIL)。

默認情況下[,CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏,該宏指定可以聚合物件。 要重寫此默認行為,請在類定義中包括DECLARE_ONLY_AGGREGATABLE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

指定在建立物件時創建**CComPolyObject \< ** *x***>** 的實例。

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要定義為可聚合或不可聚合的類物件的名稱。

### <a name="remarks"></a>備註

在創建期間,將檢查外部未知值。 如果為 NULL,`IUnknown`則為非聚合物件實現。 如果外部未知值不是 NULL,`IUnknown`則為聚合對象實現。

使用DECLARE_POLY_AGGREGATABLE的優點是,您避免在模組`CComAggObject``CComObject`中同時處理聚合和非聚合情況。 單個`CComPolyObject`物件處理這兩種情況。 這意味著模組中僅存在一個 vtable 副本和一個函數副本。 如果 vtable 很大,這可大幅減小模組大小。 但是,如果 vtable 很小`CComPolyObject`,則使用可能會導致模組大小稍大一些,因為它未針對聚合或非聚合物件進行優化`CComAggObject`,`CComObject`例如和 。

如果使用 ATL 控制精靈建立完全控制項,則DECLARE_POLY_AGGREGATABLE宏將自動在物件中聲明。

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

如果(在[Final構造](ccomobjectrootex-class.md#finalconstruct)期間)內部聚合物件遞增引用計數,然後將計數縮減為 0,則保護物件不被刪除。

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

將此宏放在 ATL ActiveX 控制件的控制類中,以將「視點」標誌指定到容器。

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>參數

*statusFlags*<br/>
[在]視圖狀態標誌。 有關旗標清單,請參閱[檢視狀態](/windows/win32/api/ocidl/ne-ocidl-viewstatus)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
