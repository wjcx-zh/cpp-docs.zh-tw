---
title: COM 介面項目巨集 |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16aa17ef58e8e4a7f0b8970cb229b6c914f291fe
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080113"
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY 巨集

這些巨集會輸入到其 COM 對應物件的介面，讓他們可以存取`QueryInterface`。 COM 對應中的項目順序是訂單介面將會檢查比對期間 iid `QueryInterface`。

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|輸入 COM 介面對應的介面。|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用這個巨集，以釐清繼承的兩個分支。|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|您可以使用這個巨集來輸入到 COM 對應的介面，並指定其 IID。|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|與相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|當介面會由*iid*查詢，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，差異在於查詢任何 IID 導致轉送查詢*punk*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非*punk*是 NULL，它會自動建立所描述的彙總*clsid*。|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|與相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，差異在於查詢任何 IID 導致轉送查詢*punk*，而如果*punk*為 NULL，就會自動建立所描述的彙總*clsid*。|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|會導致您的程式來呼叫[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297)時便會查詢指定的介面。|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|儲存每個執行個體的指定介面的資料。|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|會公開您 tear-off 介面。|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|處理到達這個 COM 對應中的項目時，請處理 COM 對應的基底類別。|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|連結到 ATL 的一般機制`QueryInterface`邏輯。|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|與相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，差異在於查詢任何 IID 的呼叫會導致*func*。|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|會傳回 E_NOINTERFACE 並結束 COM 對應會處理查詢指定的介面時。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

輸入 COM 介面對應的介面。

### <a name="syntax"></a>語法

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您類別的物件直接衍生自介面的名稱。

### <a name="remarks"></a>備註

一般而言，這是您最常使用的項目類型。

### <a name="example"></a>範例

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2

使用這個巨集，以釐清繼承的兩個分支。

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您要從您的物件公開的介面名稱。

*x2*<br/>
[in]要從中繼承分支名稱*x*公開。

### <a name="remarks"></a>備註

比方說，如果您衍生您的類別物件，這兩個雙重介面，公開`IDispatch`使用自 COM_INTERFACE_ENTRY2`IDispatch`可以取自其中之一的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID

您可以使用這個巨集來輸入到 COM 對應的介面，並指定其 IID。

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]公開介面的 GUID。

*x*<br/>
[in]其 vtable 即將公開為所識別的介面的類別名稱*iid*。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID

與相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]您指定介面的 GUID。

*x*<br/>
[in]您類別的物件直接衍生自介面的名稱。

*x2*<br/>
[in]您類別的物件直接衍生自第二個介面的名稱。

##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE

當介面會由*iid*查詢的 COM_INTERFACE_ENTRY_AGGREGATE 轉送給*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]查詢介面的 GUID。

*punk*<br/>
[in]名稱`IUnknown`指標。

### <a name="remarks"></a>備註

*Punk*參數會假設以指向內部彙總的未知或 NULL，在此情況下的項目會被忽略。 一般而言，您就`CoCreate`中的彙總`FinalConstruct`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND

與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，差異在於查詢任何 IID 導致轉送查詢*punk*。

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>參數

*punk*<br/>
[in]名稱`IUnknown`指標。

### <a name="remarks"></a>備註

如果介面查詢將會失敗，會繼續處理 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE

與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非*punk*是 NULL，它會自動建立所描述的彙總*clsid*。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]查詢介面的 GUID。

*punk*<br/>
[in]名稱`IUnknown`指標。 必須是包含 COM 對應之類別的成員。

*clsid*<br/>
[in]如果會建立彙總的識別碼*punk*是 NULL。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

與相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，差異在於查詢任何 IID 導致轉送查詢*punk*，而如果*punk*為 NULL，就會自動建立所描述的彙總*clsid*。

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>參數

*punk*<br/>
[in]名稱`IUnknown`指標。 必須是包含 COM 對應之類別的成員。

*clsid*<br/>
[in]如果會建立彙總的識別碼*punk*是 NULL。

### <a name="remarks"></a>備註

如果介面查詢將會失敗，會繼續處理 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK

會導致您的程式來呼叫[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297)時便會查詢指定的介面。

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>參數

*x*<br/>
[in]文字用來建構的介面識別項。

### <a name="remarks"></a>備註

介面的 IID 將建構附加*x*至`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。

##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

儲存每個執行個體的指定介面的資料。

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]分割介面的 GUID。

*x*<br/>
[in]實作介面的類別名稱。

*punk*<br/>
[in]名稱`IUnknown`指標。 必須是包含 COM 對應之類別的成員。 應該初始化為 NULL 類別物件的建構函式中。

### <a name="remarks"></a>備註

如果未使用的介面，這會降低整體的執行個體大小的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF

會公開您 tear-off 介面。

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]分割介面的 GUID。

*x*<br/>
[in]實作介面的類別名稱。

### <a name="remarks"></a>備註

分割介面被實作查詢具現化每次它所代表之介面的個別物件。 通常，您會建置您的介面分割為如果很少使用的介面，因為這會將 vtable 指標儲存在您的主要物件的每個執行個體。 分割會刪除其參考計數變成零。 實作分割的類別應該衍生自`CComTearOffObjectBase`，而且有它自己的 COM 對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN

處理到達這個 COM 對應中的項目時，請處理 COM 對應的基底類別。

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>參數

*classname*<br/>
[in]目前物件的基底類別。

### <a name="remarks"></a>備註

例如，在下列程式碼：

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

請注意，在 COM 對應中的第一個項目必須是包含 COM 對應的物件上的介面。 因此，您無法讓您的 COM 對應項目開始 COM_INTERFACE_ENTRY_CHAIN，這會導致不同的物件，要搜尋之處的 COM 對應所在**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** 物件的 COM 對應中會出現。 如果您想要先搜尋另一個物件的 COM 對應中，新增介面項目`IUnknown`到 COM 對應，然後鏈結的其他物件的 COM 對應。 例如: 

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC

連結到 ATL 的一般機制`QueryInterface`邏輯。

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]公開介面的 GUID。

*dw*<br/>
[in]為參數傳遞給*func*。

*func*<br/>
[in]將傳回的函式指標*iid*。

### <a name="remarks"></a>備註

如果*iid*比對，查詢的介面，然後藉由指定的函式的 IID *func*呼叫。 函式宣告應該是：

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

您的函式呼叫時，`pv`指向您類別的物件。 *Riid*參數是指，查詢的介面`ppv`函式應在其中儲存介面指標的位置的指標和*dw*參數您指定的項目中。 函式應該設定\* `ppv` NULL，並傳回 E_NOINTERFACE 或 S_FALSE 如果選擇不傳回的介面。 具有 E_NOINTERFACE，COM 對應處理作業會終止。 S_FALSE，與 COM 對應處理會繼續，即使沒有介面指標傳回。 如果函數傳回的介面指標，它應該會傳回 S_OK。

##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND

與相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，差異在於查詢任何 IID 的呼叫會導致*func*。

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>參數

*dw*<br/>
[in]為參數傳遞給*func*。

*func*<br/>
[in]取得在處理 COM 對應中的此項目時所呼叫的函式。

### <a name="remarks"></a>備註

任何失敗會導致處理作業能夠繼續在 COM 對應上。 如果函數傳回的介面指標，它應該會傳回 S_OK。

##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE

會傳回 E_NOINTERFACE 並結束 COM 對應會處理查詢指定的介面時。

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>參數

*x*<br/>
[in]文字用來建構的介面識別項。

### <a name="remarks"></a>備註

您可以使用這個巨集，以防止在特定情況下使用的介面。 例如，您可以將這個巨集插入之前防止介面的查詢轉送到彙總的內部未知 COM_INTERFACE_ENTRY_AGGREGATE_BLIND COM 對應。

介面的 IID 將建構附加*x*至`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。

