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
ms.openlocfilehash: 1358a51f6bcb65f9c54c2006a6a467cf96593b5f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834696"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY 宏

這些宏會在其 COM 對應中輸入物件的介面，以供存取 `QueryInterface` 。 COM 對應中的專案順序是在期間，會檢查是否有相符 IID 的順序介面 `QueryInterface` 。

|巨集|描述|
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|將介面輸入至 COM 介面對應。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用這個宏來區分繼承的兩個分支。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏將介面輸入至 COM 對應，並指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|與 [COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，不同之處在于您可以指定不同的 IID。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|當查詢由 *iid* 識別的介面時，會 `COM_INTERFACE_ENTRY_AGGREGATE` 轉送至 `punk` 。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|與 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至 *punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|與 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非 *punk* 為 Null，否則它會自動建立 *clsid*所描述的匯總。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|與 [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至 *punk*，如果 *punk* 為 Null，則會自動建立 *clsid*所描述的匯總。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|當查詢指定的介面時，讓您的程式呼叫 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|儲存每個實例的介面特定資料。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公開您的卸載介面。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|當處理到達 COM 對應中的這個專案時，處理基類的 COM 對應。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|連結至 ATL 邏輯的一般機制 `QueryInterface` 。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|與 [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之處在于查詢任何 IID 都會導致對 *FUNC*的呼叫。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|當查詢指定的介面時，會傳回 E_NOINTERFACE 並終止 COM 對應處理。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

將介面輸入至 COM 介面對應。

### <a name="syntax"></a>語法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在類別物件直接衍生自的介面名稱。

### <a name="remarks"></a>備註

通常，這是您最常使用的專案類型。

### <a name="example"></a>範例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a> COM_INTERFACE_ENTRY2

使用這個宏來區分繼承的兩個分支。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>參數

*x*<br/>
在您要從物件公開的介面名稱。

*x2*<br/>
在從中公開 *x* 的繼承分支名稱。

### <a name="remarks"></a>備註

例如，如果您從兩個雙重介面衍生類別物件，則會 `IDispatch` 使用 COM_INTERFACE_ENTRY2 公開，因為 `IDispatch` 可以從其中一個介面取得。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a> COM_INTERFACE_ENTRY_IID

使用此宏將介面輸入至 COM 對應，並指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在公開之介面的 GUID。

*x*<br/>
在類別的名稱，其 vtable 將公開為由 *iid*識別的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a> COM_INTERFACE_ENTRY2_IID

與 [COM_INTERFACE_ENTRY2](#com_interface_entry2)相同，不同之處在于您可以指定不同的 IID。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在您為介面指定的 GUID。

*x*<br/>
在類別物件直接衍生自的介面名稱。

*x2*<br/>
在類別物件直接衍生自第二個介面的名稱。

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a> COM_INTERFACE_ENTRY_AGGREGATE

當查詢由 *iid* 識別的介面時，COM_INTERFACE_ENTRY_AGGREGATE 轉送至 *punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在所查詢之介面的 GUID。

*朋 克*<br/>
在指標的名稱 `IUnknown` 。

### <a name="remarks"></a>備註

假設 *punk* 參數指向匯總的內部未知或 Null，在此情況下會忽略該專案。 一般而言，您會 `CoCreate` 在中匯總 `FinalConstruct` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a> COM_INTERFACE_ENTRY_AGGREGATE_BLIND

與 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至 *punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>參數

*朋 克*<br/>
在指標的名稱 `IUnknown` 。

### <a name="remarks"></a>備註

如果介面查詢失敗，則會繼續處理 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a> COM_INTERFACE_ENTRY_AUTOAGGREGATE

與 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)相同，除非 *punk* 為 Null，否則它會自動建立 *clsid*所描述的匯總。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在所查詢之介面的 GUID。

*朋 克*<br/>
在指標的名稱 `IUnknown` 。 必須是包含 COM 對應之類別的成員。

*Clsid*<br/>
在如果 *punk* 為 Null 時，將會建立之匯總的識別碼。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a> COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

與 [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)相同，不同之處在于查詢任何 IID 會導致將查詢轉送至 *punk*，如果 *punk* 為 Null，則會自動建立 *clsid*所描述的匯總。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>參數

*朋 克*<br/>
在指標的名稱 `IUnknown` 。 必須是包含 COM 對應之類別的成員。

*Clsid*<br/>
在如果 *punk* 為 Null 時，將會建立之匯總的識別碼。

### <a name="remarks"></a>備註

如果介面查詢失敗，則會繼續處理 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a> COM_INTERFACE_ENTRY_BREAK

當查詢指定的介面時，讓您的程式呼叫 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 。

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在用來建立介面識別碼的文字。

### <a name="remarks"></a>備註

介面 IID 將會藉由將 *x* 附加至來構成 `IID_` 。 例如，如果 *x* 是 `IPersistStorage` ，則 IID 會是 `IID_IPersistStorage` 。

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a> COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

儲存每個實例的介面特定資料。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在卸載介面的 GUID。

*x*<br/>
在執行介面之類別的名稱。

*朋 克*<br/>
在指標的名稱 `IUnknown` 。 必須是包含 COM 對應之類別的成員。 在類別物件的函式中，應該初始化為 Null。

### <a name="remarks"></a>備註

如果未使用介面，這會減少物件的整體實例大小。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a> COM_INTERFACE_ENTRY_TEAR_OFF

公開您的卸載介面。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在卸載介面的 GUID。

*x*<br/>
在執行介面之類別的名稱。

### <a name="remarks"></a>備註

卸載介面會實作為個別的物件，此物件會在每次查詢其代表的介面時具現化。 一般來說，如果介面很少使用，您會將介面建立成卸載，因為這樣會將 vtable 指標儲存在主要物件的每個實例中。 當其參考計數變成零時，會刪除卸載。 實作為卸載的類別應該衍生自 `CComTearOffObjectBase` ，而且有自己的 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a> COM_INTERFACE_ENTRY_CHAIN

當處理到達 COM 對應中的這個專案時，處理基類的 COM 對應。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>參數

*classname*<br/>
在目前物件的基類。

### <a name="remarks"></a>備註

例如，在下列程式碼中：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

請注意，COM 對應中的第一個專案必須是包含 COM 對應之物件上的介面。 因此，您無法使用 COM_INTERFACE_ENTRY_CHAIN 啟動 com 對應專案，這會導致在**COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` 物件的 com 對應中出現 COM_INTERFACE_ENTRY_CHAIN (**) **的點搜尋不同物件的 com 對應。 如果您想要先搜尋另一個物件的 COM 對應，請將介面專案加入 `IUnknown` 至您的 com 對應，然後再鏈另一個物件的 com 對應。 例如：

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a> COM_INTERFACE_ENTRY_FUNC

連結至 ATL 邏輯的一般機制 `QueryInterface` 。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>參數

*Iid*<br/>
在公開之介面的 GUID。

*dw*<br/>
在傳遞至 *func*的參數。

*func*<br/>
在將傳回 *iid*的函式指標。

### <a name="remarks"></a>備註

如果 *iid* 符合所查詢之介面的 iid，則會呼叫 *func* 所指定的函式。 函數的宣告應該是：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

呼叫您的函式時，會 `pv` 指向您的類別物件。 *Riid*參數指的是要查詢的介面， `ppv` 它是函式應將指標儲存至介面之位置的指標，而*dw*則是您在專案中指定的參數。 函式應該設定 \* `ppv` 為 Null，並傳回 E_NOINTERFACE 或 S_FALSE 如果選擇不傳回介面。 使用 E_NOINTERFACE，COM 對應處理會終止。 使用 S_FALSE 時，COM 對應處理會繼續進行，即使沒有傳回任何介面指標也一樣。 如果函式傳回介面指標，則應該傳回 S_OK。

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a> COM_INTERFACE_ENTRY_FUNC_BLIND

與 [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)相同，不同之處在于查詢任何 IID 都會導致對 *FUNC*的呼叫。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>參數

*dw*<br/>
在傳遞至 *func*的參數。

*func*<br/>
在處理 COM 對應中的這個專案時，所呼叫的函式。

### <a name="remarks"></a>備註

任何失敗都會導致在 COM 對應上繼續處理。 如果函式傳回介面指標，則應該傳回 S_OK。

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a> COM_INTERFACE_ENTRY_NOINTERFACE

當查詢指定的介面時，會傳回 E_NOINTERFACE 並終止 COM 對應處理。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在用來建立介面識別碼的文字。

### <a name="remarks"></a>備註

您可以使用這個宏來防止介面用於特定案例中。 例如，您可以在 COM_INTERFACE_ENTRY_AGGREGATE_BLIND 之前將這個宏插入 COM 對應中，以防止將介面的查詢轉送至匯總的內部未知。

介面 IID 將會藉由將 *x* 附加至來構成 `IID_` 。 例如，如果 *x* 是 `IPersistStorage` ，則 IID 會是 `IID_IPersistStorage` 。
