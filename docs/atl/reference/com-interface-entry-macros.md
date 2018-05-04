---
title: COM 介面進入巨集會 |Microsoft 文件
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
ms.openlocfilehash: 7c3ba41a05813c4112c1e5dd51bfe447d2c8debf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY 巨集  
 這些巨集會輸入至其 COM 對應物件的介面，以便存取它們所`QueryInterface`。 COM 對應中的項目順序是順序介面會檢查相符**IID**期間`QueryInterface`。  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY](#com_interface_entry)|輸入的 COM 介面對應的介面。|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用這個巨集，以釐清兩個繼承的分支。|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此巨集輸入到 COM 對應的介面，並指定其 IID。|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|與相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，不過您可以指定不同的 IID。|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|當介面由`iid`查詢，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，不同之處在於任何 IID 的查詢會產生轉送查詢`punk`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它會自動建立所描述的彙總`clsid`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|與相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，不同之處在於任何 IID 的查詢會產生轉送查詢`punk`，而且如果`punk`是**NULL**、 自動建立所描述的彙總`clsid`。|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|會導致您的程式來呼叫[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)時指定的介面中查詢。|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|將每個執行個體的特定介面的資料儲存。|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|會公開您 tear-off 介面。|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|處理 COM 對應的基底類別處理到達這個 COM 對應中的項目時。|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|連結至 ATL 的一般機制`QueryInterface`邏輯。|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|與相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，不同之處在於任何 IID 的查詢會導致呼叫`func`。|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|傳回**E_NOINTERFACE**並終止 COM 對應處理時，查詢指定的介面。|  

## <a name="requirements"></a>需求
**標頭：** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY
輸入的 COM 介面對應的介面。

### <a name="syntax"></a>語法

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>參數

[in] 介面的名稱 x 類別物件衍生自直接。

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
 使用這個巨集，以釐清兩個繼承的分支。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要從您的物件公開的介面名稱。  
  
 `x2`  
 [in]從中繼承分支名稱*x*公開。  
  
### <a name="remarks"></a>備註  
 例如，如果您衍生您的類別物件，這兩個雙介面，您公開`IDispatch`使用`COM_INTERFACE_ENTRY2`因為`IDispatch`可以取自之介面的其中一個。  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID  
 使用此巨集輸入到 COM 對應的介面，並指定其 IID。  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]公開介面的 GUID。  
  
 *x*  
 [in]其 vtable 即將公開為所識別的介面的類別名稱`iid`。  
  
 
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID  
 與相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，不過您可以指定不同的 IID。  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]您要指定介面的 GUID。  
  
 *x*  
 [in]類別物件直接衍生自介面的名稱。  
  
 `x2`  
 [in]第二個介面類別物件直接衍生自的名稱。  
  
##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE  
 當介面由`iid`查詢，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 `punk`參數會假設為指向內部未知的彙總或**NULL**，在此情況下會忽略此項目。 一般而言，您會**CoCreate**中的彙總`FinalConstruct`。  
  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，不同之處在於任何 IID 的查詢會產生轉送查詢`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 如果介面查詢將會失敗，會繼續處理 COM 對應。  
  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 與相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它會自動建立所描述的彙總`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。  
  
 `clsid`  
 [in]如果建立的彙總的識別碼`punk`是**NULL**。  
  
### <a name="remarks"></a>備註  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 與相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，不同之處在於任何 IID 的查詢會產生轉送查詢`punk`，而且如果`punk`是**NULL**、 自動建立所描述的彙總`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。  
  
 `clsid`  
 [in]如果建立的彙總的識別碼`punk`是**NULL**。  
  
### <a name="remarks"></a>備註  
 如果介面查詢將會失敗，會繼續處理 COM 對應。  
  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK  
 會導致您的程式來呼叫[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)時指定的介面中查詢。  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]用來建構介面識別項的文字。  
  
### <a name="remarks"></a>備註  
 藉由附加建構 IID 的介面*x*至`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 將每個執行個體的特定介面的資料儲存。  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]撕下介面的 GUID。  
  
 *x*  
 [in]實作介面的類別名稱。  
  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。 應該初始化為**NULL**類別物件的建構函式中。  
  
### <a name="remarks"></a>備註  
 如果未使用的介面，這可減少整體的執行個體大小的物件。  
  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF  
 會公開您 tear-off 介面。  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]撕下介面的 GUID。  
  
 *x*  
 [in]實作介面的類別名稱。  
  
### <a name="remarks"></a>備註  
 撕下介面的實作如下查詢每次它所代表的介面具現化的個別物件。 一般而言，您建置您的介面為撕如果很少使用的介面，因為這樣可以節省您的主要物件的每個執行個體的 vtable 指標。 分割時，會刪除其參考計數變成零時。 實作分割的類別應該衍生自`CComTearOffObjectBase`，而且有它自己的 COM 對應。  
  
  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN  
 處理 COM 對應的基底類別處理到達這個 COM 對應中的項目時。  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>參數  
 *classname*  
 [in]目前物件的基底類別。  
  
### <a name="remarks"></a>備註  
 例如，在下列程式碼：  
  
 [!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 請注意 COM 對應中的第一個項目必須包含 COM 對應的物件上的介面。 因此，您無法啟動您的 COM 對應項目與`COM_INTERFACE_ENTRY_CHAIN`，因而導致 COM 對應，不同處要搜尋的物件位置**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** 會出現在物件的 COM 對應。 如果您想要搜尋的另一個物件的 COM 對應，首先，新增介面項目**IUnknown**到 COM 對應，然後鏈結的其他物件的 COM 對應。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC  
 連結至 ATL 的一般機制`QueryInterface`邏輯。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]公開介面的 GUID。  
  
 `dw`  
 [in]為參數傳遞到`func`。  
  
 `func`  
 [in]將傳回的函式指標`iid`。  
  
### <a name="remarks"></a>備註  
 如果*iid*符合介面中查詢，則函式所指定的 IID`func`呼叫。 函式宣告應該是：  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 您的函式呼叫時，`pv`指向類別物件。 `riid`參數是指，要查詢的介面`ppv`函式應該儲存介面的指標位置的指標和`dw`是您指定的項目中的參數。 函式應該設定\*`ppv`至**NULL**並傳回**E_NOINTERFACE**或**S_FALSE**如果選擇不是要傳回的介面。 與**E_NOINTERFACE**，COM 對應處理作業會終止。 與**S_FALSE**，COM 對應處理會繼續，即使沒有介面指標傳回。 如果函式會傳回介面指標，它應該傳回`S_OK`。  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND  
 與相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，不同之處在於任何 IID 的查詢會導致呼叫`func`。  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>參數  
 `dw`  
 [in]為參數傳遞到`func`。  
  
 `func`  
 [in]取得處理 COM 對應中的此項目時呼叫的函式。  
  
### <a name="remarks"></a>備註  
 任何失敗會導致處理作業能夠繼續的 COM 對應上。 如果函式會傳回介面指標，它應該傳回`S_OK`。  
  
  
##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE  
 傳回**E_NOINTERFACE**並終止 COM 對應處理時，查詢指定的介面。  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]用來建構介面識別項的文字。  
  
### <a name="remarks"></a>備註  
 您可以使用這個巨集，以防止在特定情況下使用的介面。 例如，您可以將這個巨集，插入您的 COM 對應前`COM_INTERFACE_ENTRY_AGGREGATE_BLIND`以防止被轉送到彙總內部的未知的查詢介面。  
  
 藉由附加建構 IID 的介面*x*至`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。  
  
  