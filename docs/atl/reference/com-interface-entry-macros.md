---
title: COM 介面專案宏
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
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855662"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY 宏

這些宏會在其 COM 對應中輸入物件的介面，讓 `QueryInterface`可以存取它們。 COM 對應中的專案順序是在 `QueryInterface`期間，會檢查順序介面是否有相符的 IID。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|將介面輸入 COM 介面對應。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏來區分兩個繼承分支。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏將介面輸入 COM 對應中，並指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|與[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，不同之處在于您可以指定不同的 IID。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|當查詢*iid*所識別的介面時，`COM_INTERFACE_ENTRY_AGGREGATE` 轉送至 `punk`。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*punk*是 Null，否則會自動建立*clsid*所描述的匯總。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|與[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至*punk*，如果*punk*為 Null，則會自動建立*clsid*所描述的匯總。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|當查詢指定的介面時，讓您的程式呼叫[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|儲存每個實例的介面特定資料。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公開您的卸載介面。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|當處理常式到達 COM 對應中的這個專案時，處理基類的 COM 對應。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|連結至 ATL 的 `QueryInterface` 邏輯的一般機制。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|與[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之處在于查詢任何 IID 會導致呼叫*FUNC*。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|當查詢指定的介面時，傳回 E_NOINTERFACE 並終止 COM 對應處理。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

將介面輸入 COM 介面對應。

### <a name="syntax"></a>語法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在類別物件直接衍生自之介面的名稱。

### <a name="remarks"></a>備註

一般來說，這是您最常使用的專案類型。

### <a name="example"></a>範例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

使用此宏來區分兩個繼承分支。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>參數

*x*<br/>
在您想要從物件公開的介面名稱。

*x2*<br/>
在公開*x*的繼承分支名稱。

### <a name="remarks"></a>備註

例如，如果您從兩個雙重介面衍生類別物件，您可以使用 COM_INTERFACE_ENTRY2 公開 `IDispatch`，因為 `IDispatch` 可以從其中一個介面取得。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

使用此宏將介面輸入 COM 對應中，並指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>參數

*iid*<br/>
在公開介面的 GUID。

*x*<br/>
在類別的名稱，其 vtable 會公開為*iid*所識別的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

與[COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，不同之處在于您可以指定不同的 IID。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>參數

*iid*<br/>
在您為介面指定的 GUID。

*x*<br/>
在類別物件直接衍生自之介面的名稱。

*x2*<br/>
在類別物件直接衍生自之第二個介面的名稱。

##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

當查詢*iid*所識別的介面時，COM_INTERFACE_ENTRY_AGGREGATE 轉送至*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>參數

*iid*<br/>
在查詢之介面的 GUID。

*punk*<br/>
在`IUnknown` 指標的名稱。

### <a name="remarks"></a>備註

假設*punk*參數指向匯總的內部未知或為 Null，在此情況下會忽略專案。 一般來說，您會在 `FinalConstruct`中 `CoCreate` 匯總。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>參數

*punk*<br/>
在`IUnknown` 指標的名稱。

### <a name="remarks"></a>備註

如果介面查詢失敗，COM 對應的處理就會繼續進行。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

與[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非*punk*是 Null，否則會自動建立*clsid*所描述的匯總。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>參數

*iid*<br/>
在查詢之介面的 GUID。

*punk*<br/>
在`IUnknown` 指標的名稱。 必須是包含 COM 對應之類別的成員。

*clsid*<br/>
在如果*punk*為 Null，將會建立之匯總的識別碼。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

與[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至*punk*，如果*punk*為 Null，則會自動建立*clsid*所描述的匯總。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>參數

*punk*<br/>
在`IUnknown` 指標的名稱。 必須是包含 COM 對應之類別的成員。

*clsid*<br/>
在如果*punk*為 Null，將會建立之匯總的識別碼。

### <a name="remarks"></a>備註

如果介面查詢失敗，COM 對應的處理就會繼續進行。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

當查詢指定的介面時，讓您的程式呼叫[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在用來建立介面識別碼的文字。

### <a name="remarks"></a>備註

介面 IID 會藉由將*x*附加至 `IID_`來加以結構化。 例如，如果*x*是 `IPersistStorage`，則會 `IID_IPersistStorage`IID。

##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

儲存每個實例的介面特定資料。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>參數

*iid*<br/>
在脫離介面的 GUID。

*x*<br/>
在執行介面的類別名稱。

*punk*<br/>
在`IUnknown` 指標的名稱。 必須是包含 COM 對應之類別的成員。 應該在類別物件的函式中初始化為 Null。

### <a name="remarks"></a>備註

如果未使用介面，這會降低物件的整體實例大小。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

公開您的卸載介面。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>參數

*iid*<br/>
在脫離介面的 GUID。

*x*<br/>
在執行介面的類別名稱。

### <a name="remarks"></a>備註

卸載介面會實作為個別的物件，並在每次查詢它所代表的介面時具現化。 一般而言，如果介面很少使用，您會將介面建立為卸載，因為這會將 vtable 指標儲存在主要物件的每個實例中。 當其參考計數變成零時，會刪除卸載。 執行卸載的類別應該衍生自 `CComTearOffObjectBase`，而且有自己的 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

當處理常式到達 COM 對應中的這個專案時，處理基類的 COM 對應。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>參數

*classname*<br/>
在目前物件的基類。

### <a name="remarks"></a>備註

例如，在下列程式碼中：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

請注意，COM 對應中的第一個專案必須是包含 COM 對應之物件上的介面。 因此，您無法使用 COM_INTERFACE_ENTRY_CHAIN 來啟動您的 COM 對應專案，這會導致在物件的 COM 對應中出現**COM_INTERFACE_ENTRY_CHAIN （** `COtherObject` **）** 的位置時，搜尋不同物件的 com 對應。 如果您想要先搜尋另一個物件的 COM 對應，請將 `IUnknown` 的介面專案新增至您的 COM 對應，然後再連結另一個物件的 COM 對應。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

連結至 ATL 的 `QueryInterface` 邏輯的一般機制。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>參數

*iid*<br/>
在公開介面的 GUID。

*dw*<br/>
在傳遞至*func*的參數。

*func*<br/>
在將傳回*iid*的函式指標。

### <a name="remarks"></a>備註

如果*iid*符合所查詢之介面的 iid，則會呼叫*func*所指定的函式。 函數的宣告應該是：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

呼叫您的函式時，`pv` 會指向您的類別物件。 *Riid*參數是指要查詢的介面，`ppv` 是函式應該儲存介面指標的位置指標，而*dw*則是您在專案中指定的參數。 函數應將 \* `ppv` 設定為 Null，並在選擇不傳回介面時，傳回 E_NOINTERFACE 或 S_FALSE。 使用 E_NOINTERFACE，COM 對應處理會終止。 使用 S_FALSE，即使未傳回任何介面指標，COM 對應處理仍會繼續進行。 如果函式傳回介面指標，它應該會傳回 S_OK。

##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

與[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之處在于查詢任何 IID 會導致呼叫*FUNC*。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>參數

*dw*<br/>
在傳遞至*func*的參數。

*func*<br/>
在處理 COM 對應中的這個專案時，所呼叫的函式。

### <a name="remarks"></a>備註

任何失敗都會導致在 COM 對應上繼續處理。 如果函式傳回介面指標，它應該會傳回 S_OK。

##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

當查詢指定的介面時，傳回 E_NOINTERFACE 並終止 COM 對應處理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在用來建立介面識別碼的文字。

### <a name="remarks"></a>備註

您可以使用這個宏來避免在特定案例中使用介面。 例如，您可以在 COM_INTERFACE_ENTRY_AGGREGATE_BLIND 之前將此宏插入 COM 對應中，以防止將介面的查詢轉送至匯總的內部未知。

介面 IID 會藉由將*x*附加至 `IID_`來加以結構化。 例如，如果*x*是 `IPersistStorage`，則會 `IID_IPersistStorage`IID。
