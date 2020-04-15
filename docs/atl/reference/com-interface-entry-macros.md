---
title: COM 介面項目巨集
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326682"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY宏

這些宏在其 COM 映射中輸入物件的介面,以便`QueryInterface`可以訪問 它們。 COM 映射中的項目順序是,將在期間`QueryInterface`檢查匹配的 IID 的順序介面。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|將介面輸入 COM 介面映射。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏可以消除繼承的兩個分支的歧義。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏將介面輸入 COM 地圖並指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|與[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同 ,但可以指定其他 IID 除外。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|查詢*iid*識別介面時`COM_INTERFACE_ENTRY_AGGREGATE`, 將`punk`轉寄到 。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同 ,只不過查詢任何 IID 會將查詢轉寄到*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同,除非*朋克*為 NULL,否則它會自動創建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|與[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同 ,只不過查詢任何 IID 會導致將查詢轉發到*punk*,如果*punk*為 NULL,則會自動創建*clsid*描述的聚合。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|當查詢指定的介面時,導致程式呼叫[DebugBreak。](/windows/win32/api/debugapi/nf-debugapi-debugbreak)|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|為每個實例保存特定於介面的數據。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公開拆解介面。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|當處理到達 COM 映射中的此條目時,處理基類的 COM 映射。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|一種連接到 ATL`QueryInterface`邏輯的一般機制。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|與[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同 ,只不過查詢任何 IID 都會導致對*func*的調用。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|E_NOINTERFACE返回並終止指定的介面時的 COM 映射處理。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

將介面輸入 COM 介面映射。

### <a name="syntax"></a>語法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]類物件直接派生的介面的名稱。

### <a name="remarks"></a>備註

通常,這是最常用的條目類型。

### <a name="example"></a>範例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

使用此宏可以消除繼承的兩個分支的歧義。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要從物件公開的介面的名稱。

*x2*<br/>
[在]從中公開*x*的繼承分支的名稱。

### <a name="remarks"></a>備註

例如,如果從兩個雙介面派生類物件,則使用COM_INTERFACE_ENTRY2公開`IDispatch`,`IDispatch`因為 可以從任一介面獲取。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

使用此宏將介面輸入 COM 地圖並指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]介面的 GUID 暴露。

*X.*<br/>
[在]其 vtable 將作為*iid*標識的介面的類的名稱。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

與[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同 ,但可以指定其他 IID 除外。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]您為介面指定的 GUID。

*X.*<br/>
[在]類物件直接派生的介面的名稱。

*x2*<br/>
[在]類物件直接派生的第二個介面的名稱。

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

當查詢*iid*識別的介面時,COM_INTERFACE_ENTRY_AGGREGATE轉發到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]查詢的介面的 GUID。

*龐克*<br/>
[在]`IUnknown`指標的名稱。

### <a name="remarks"></a>備註

假定*punk*參數指向聚合或 NULL 的內部未知值,在這種情況下,該條目將被忽略。 通常,您將`CoCreate`中的聚合在`FinalConstruct`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同 ,只不過查詢任何 IID 會將查詢轉寄到*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]`IUnknown`指標的名稱。

### <a name="remarks"></a>備註

如果介面查詢失敗,則處理 COM 映射將繼續。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同,除非*朋克*為 NULL,否則它會自動創建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]查詢的介面的 GUID。

*龐克*<br/>
[在]`IUnknown`指標的名稱。 必須是包含 COM 映射的類的成員。

*Clsid*<br/>
[在]如果*punk*為 NULL,則要建立的聚合的識別碼。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

與[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同 ,只不過查詢任何 IID 會導致將查詢轉發到*punk*,如果*punk*為 NULL,則會自動創建*clsid*描述的聚合。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]`IUnknown`指標的名稱。 必須是包含 COM 映射的類的成員。

*Clsid*<br/>
[在]如果*punk*為 NULL,則要建立的聚合的識別碼。

### <a name="remarks"></a>備註

如果介面查詢失敗,則處理 COM 映射將繼續。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

當查詢指定的介面時,導致程式呼叫[DebugBreak。](/windows/win32/api/debugapi/nf-debugapi-debugbreak)

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]用於建構介面標識碼。

### <a name="remarks"></a>備註

介面 IID 將*x*透過將`IID_`x 追加到 來建構。 例如,如果*x*`IPersistStorage`是 ,則`IID_IPersistStorage`IID 將為 。

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

為每個實例保存特定於介面的數據。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]撕裂介面的 GUID。

*X.*<br/>
[在]實現介面的類的名稱。

*龐克*<br/>
[在]`IUnknown`指標的名稱。 必須是包含 COM 映射的類的成員。 應在類物件的建構函數中初始化為 NULL。

### <a name="remarks"></a>備註

如果未使用介面,這將降低物件的總體實例大小。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

公開拆解介面。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]撕裂介面的 GUID。

*X.*<br/>
[在]實現介面的類的名稱。

### <a name="remarks"></a>備註

拆解介面作為單獨的物件實現,每次查詢它所代表的介面時都會實例化該物件。 通常,如果很少使用介面,則可以將介面構建為分機,因為這會在主物件的每個實例中保存一個 vtable 指標。 當其引用計數變為零時,將刪除拆解。 實現分淚的類應派生自`CComTearOffObjectBase`並有自己的 COM 映射。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

當處理到達 COM 映射中的此條目時,處理基類的 COM 映射。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]當前對象的基類。

### <a name="remarks"></a>備註

例如,在以下代碼中:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

請注意,COM 地圖中的第一個條目必須是包含 COM 貼圖的物件上的介面。 因此,您不能用COM_INTERFACE_ENTRY_CHAIN啟動 COM 貼圖條目,這將導致在物件 COM 地圖中出現**COM_INTERFACE_ENTRY_CHAIN()**`COtherObject`**)** 點搜索其他物件的 COM 貼圖。 如果要首先搜索另一個物件的 COM 貼圖,`IUnknown`請向 COM 貼圖添加介面項目,然後連結另一個物件的 COM 貼圖。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

一種連接到 ATL`QueryInterface`邏輯的一般機制。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]介面的 GUID 暴露。

*dw*<br/>
[在]參數傳遞給*func*。

*func*<br/>
[在]將返回*iid 的*函數指標。

### <a name="remarks"></a>備註

如果*iid*與所查詢的介面的 IID 匹配,則調用*func*指定的函數。 函數的聲明應為:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

呼叫函數時,`pv`將指向類物件。 *riid*參數是指要查詢的介面`ppv`, 是指向函數應儲存指向介面的指標的位置的指標 *,dw*是您在條目中指定的參數。 如果函數選擇不返回\*`ppv`介面,則該函數應設置為 NULL 並返回E_NOINTERFACE或S_FALSE。 使用E_NOINTERFACE,COM 映射處理將終止。 使用S_FALSE,即使未返回介面指標,COM 映射處理仍將繼續。 如果函數返回介面指標,則應返回S_OK。

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

與[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同 ,只不過查詢任何 IID 都會導致對*func*的調用。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>參數

*dw*<br/>
[在]參數傳遞給*func*。

*func*<br/>
[在]處理 COM 地圖中的此條目時調用的函數。

### <a name="remarks"></a>備註

任何故障都將導致處理在 COM 地圖上繼續。 如果函數返回介面指標,則應返回S_OK。

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

E_NOINTERFACE返回並終止指定的介面時的 COM 映射處理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]用於建構介面標識碼。

### <a name="remarks"></a>備註

可以使用此宏防止在特定情況下使用介面。 例如,可以在COM_INTERFACE_ENTRY_AGGREGATE_BLIND之前將此宏插入到 COM 地圖中,以防止將介面的查詢轉發到聚合的內部未知。

介面 IID 將*x*透過將`IID_`x 追加到 來建構。 例如,如果*x*`IPersistStorage`是 ,則`IID_IPersistStorage`IID 將為 。
