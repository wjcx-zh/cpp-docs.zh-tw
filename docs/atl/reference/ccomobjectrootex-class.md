---
title: CComObjectRootEx 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417926"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別

這個類別會提供方法來處理非匯總和匯總物件的物件參考計數管理。

## <a name="syntax"></a>語法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>參數

*ThreadModel*<br/>
類別，其方法會執行所需的執行緒模型。 您可以將*ThreadModel*設定為[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，以明確選擇執行緒模型。 您可以藉由將*ThreadModel*設定為[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)，來接受伺服器的預設執行緒模型。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|
|[InternalAddRef](#internaladdref)|遞增非匯總物件的參考計數。|
|[InternalRelease](#internalrelease)|遞減非匯總物件的參考計數。|
|[狀](#lock)|如果執行緒模型為多執行緒，則會取得重要區段物件的擁有權。|
|[解除鎖定](#unlock)|如果執行緒模型為多執行緒，則釋放重要區段物件的擁有權。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法

|||
|-|-|
|[FinalConstruct](#finalconstruct)|在您的類別中覆寫，以執行物件所需的任何初始化。|
|[FinalRelease](#finalrelease)|在您的類別中覆寫，以執行物件所需的任何清除。|
|[OuterAddRef](#outeraddref)|遞增匯總物件的參考計數。|
|[OuterQueryInterface](#outerqueryinterface)|委派至匯總物件的外部 `IUnknown`。|
|[OuterRelease](#outerrelease)|遞減匯總物件的參考計數。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|委派至非匯總物件的 `IUnknown`。|
|[ObjectMain](#objectmain)|在模組初始化期間呼叫，並終止物件對應中列出的衍生類別。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_dwRef](#m_dwref)|具有 `m_pOuterUnknown`，即 union 的一部分。 當物件未匯總以保存 `AddRef` 和 `Release`的參考計數時使用。|
|[m_pOuterUnknown](#m_pouterunknown)|具有 `m_dwRef`，即 union 的一部分。 當物件匯總以保存外部未知的指標時使用。|

## <a name="remarks"></a>備註

`CComObjectRootEx` 會處理非匯總和匯總物件的物件參考計數管理。 如果您的物件未進行匯總，它會保存物件參考計數，如果您的物件正在進行匯總，則會保存外部未知的指標。 對於匯總的物件，`CComObjectRootEx` 方法可以用來處理內建物件所要建立的失敗，以及在釋放內部介面或刪除內建物件時，保護外部物件的刪除。

執行 COM 伺服器的類別必須繼承自 `CComObjectRootEx` 或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果您的類別定義指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏，則在呼叫 `IClassFactory::CreateInstance` 時，ATL 會建立 `CComPolyObject<CYourClass>` 的實例。 在建立期間，會核取 [外部未知] 的值。 如果它是 Null，則會為非匯總物件執行 `IUnknown`。 如果外部未知不是 Null，則會為匯總物件執行 `IUnknown`。

如果您的類別未指定 DECLARE_POLY_AGGREGATABLE 宏，ATL 會針對非匯總物件的匯總物件或 `CComObject<CYourClass>` 實例建立 `CAggComObject<CYourClass>` 的實例。

使用 `CComPolyObject` 的優點是，您可以避免模組中的 `CComAggObject` 和 `CComObject` 處理匯總和非匯總案例。 單一 `CComPolyObject` 物件會處理這兩種情況。 因此，只有一個 vtable 複本和一個函式複本存在於您的模組中。 如果您的 vtable 很大，這可能會大幅降低您的模組大小。 不過，如果您的 vtable 很小，使用 `CComPolyObject` 可能會產生稍微大一點的模組大小，因為它不會針對匯總或非匯總物件進行優化，如同 `CComAggObject` 和 `CComObject`。

如果您的物件已匯總，則會由 `CComAggObject` 或 `CComPolyObject`來執行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 這些類別會將 `QueryInterface`、`AddRef`和 `Release` 呼叫委派給 `CComObjectRootEx`的 `OuterQueryInterface`、`OuterAddRef`和 `OuterRelease`，以轉送到外部未知的。 一般來說，您會覆寫類別中的 `CComObjectRootEx::FinalConstruct` 來建立任何匯總物件，並覆寫 `CComObjectRootEx::FinalRelease` 以釋放任何匯總的物件。

如果您的物件未匯總，`IUnknown` 會由 `CComObject` 或 `CComPolyObject`來執行。 在此情況下，`QueryInterface`、`AddRef`和 `Release` 的呼叫會委派給 `CComObjectRootEx`的 `InternalQueryInterface`、`InternalAddRef`和 `InternalRelease`，以執行實際的作業。

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx：： CComObjectRootEx

此函式會將參考計數初始化為0。

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>CComObjectRootEx：： FinalConstruct

您可以在衍生類別中覆寫這個方法，以執行物件所需的任何初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

傳回 S_OK 成功或其中一個標準錯誤 HRESULT 值。

### <a name="remarks"></a>備註

根據預設，`CComObjectRootEx::FinalConstruct` 只會傳回 S_OK。

在 `FinalConstruct` 中執行初始化有一些優點，而不是您的類別的函式：

- 您無法從函式傳回狀態碼，但您可以透過 `FinalConstruct`的傳回值傳回 HRESULT。 當您使用 ATL 所提供的標準 Class Factory 來建立類別的物件時，此傳回值會傳播回 COM 用戶端，讓您能夠提供詳細的錯誤資訊給它們。

- 您無法從類別的函式中，透過虛擬函式機制呼叫虛擬函式。 從類別的「函式」呼叫虛擬函式，會產生以靜態方式解析的函式呼叫，因為它是在繼承階層中的該點定義。 呼叫純虛擬函式會導致連結器錯誤。

   您的類別不是繼承階層架構中最衍生的類別，而是依賴 ATL 提供的衍生類別來提供它的部分功能。 您的初始化可能需要使用該類別所提供的功能（當類別的物件需要匯總其他物件時，這當然是如此），但您的類別中的函式無法存取這些功能。 您的類別的結構化程式碼是在完全結構化最衍生的類別之前執行。

   不過，在完整結構化的衍生類別之後，會立即呼叫 `FinalConstruct`，讓您可以呼叫虛擬函式，並使用 ATL 所提供的參考計數實作為。

### <a name="example"></a>範例

通常會在衍生自 `CComObjectRootEx` 的類別中覆寫這個方法，以建立任何匯總物件。 例如，

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果結構失敗，您可以傳回錯誤。 您也可以使用宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)來保護外部物件的刪除，如果在建立期間，內部匯總物件會遞增參考計數，然後將計數遞減為0。

以下是建立匯總的一般方式：

- 將 `IUnknown` 指標新增至您的類別物件，並在此函式中將它初始化為 Null。

- 覆寫 `FinalConstruct` 以建立匯總。

- 使用您定義的 `IUnknown` 指標做為[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏的參數。

- 覆寫 `FinalRelease` 以釋放 `IUnknown` 指標。

##  <a name="finalrelease"></a>CComObjectRootEx：： FinalRelease

您可以在衍生類別中覆寫這個方法，以執行物件所需的任何清除。

```
void FinalRelease();
```

### <a name="remarks"></a>備註

根據預設，`CComObjectRootEx::FinalRelease` 不會執行任何操作。

若要在 `FinalRelease` 中執行清除，最好是將程式碼加入至類別的析構函式，因為物件仍會在呼叫 `FinalRelease` 的時間點完整地進行結構化。 這可讓您安全地存取由最衍生的類別所提供的方法。 這對於在刪除之前釋放任何匯總物件特別重要。

##  <a name="internaladdref"></a>CComObjectRootEx：： InternalAddRef

將非匯總物件的參考計數遞增1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

可能有助於診斷和測試的值。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒，`InterlockedIncrement` 會用來防止一個以上的執行緒同時變更參考計數。

##  <a name="internalqueryinterface"></a>CComObjectRootEx：： InternalQueryInterface

擷取所要求介面的指標。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*pThis*<br/>
在物件的指標，其中包含公開給 `QueryInterface`之介面的 COM 對應。

*pEntries*<br/>
在存取可用介面之對應的 `_ATL_INTMAP_ENTRY` 結構指標。

*iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
脫銷*Iid*中指定之介面指標的指標，如果找不到介面，則為 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件已匯總，`InternalQueryInterface` 不會委派至外部未知。 您可以使用宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或它的其中一個變數，在 COM 對應表中輸入介面。

##  <a name="internalrelease"></a>CComObjectRootEx：： InternalRelease

將非匯總物件的參考計數遞減1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>傳回值

在非 debug 和 debug 組建中，此函式會傳回可能有助於診斷或測試的值。 傳回的確切值取決於許多因素，例如使用的作業系統，而且可能（或可能不是參考計數）。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒，`InterlockedDecrement` 會用來防止一個以上的執行緒同時變更參考計數。

##  <a name="lock"></a>CComObjectRootEx：： Lock

如果執行緒模型為多執行緒，這個方法會呼叫 WIN32 API 函式[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，這會等到執行緒可以取得透過私用資料成員取得之重要區段物件的擁有權。

```
void Lock();
```

### <a name="remarks"></a>備註

當受保護的程式碼完成執行時，執行緒必須呼叫 `Unlock` 以釋放重要區段的擁有權。

如果執行緒模型是單一執行緒，則這個方法不會執行任何操作。

##  <a name="m_dwref"></a>CComObjectRootEx：： m_dwRef

存取四個位元組記憶體的聯集的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>備註

使用 `m_pOuterUnknown`，即 union 的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果未匯總物件，`AddRef` 和 `Release` 所存取的參考計數會儲存在 `m_dwRef`中。 如果已匯總物件，則會將外部未知的指標儲存在[m_pOuterUnknown](#m_pouterunknown)中。

##  <a name="m_pouterunknown"></a>CComObjectRootEx：： m_pOuterUnknown

存取四個位元組記憶體的聯集的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>備註

使用 `m_dwRef`，即 union 的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果已匯總物件，則會將外部未知的指標儲存在 `m_pOuterUnknown`中。 如果未匯總物件，`AddRef` 和 `Release` 所存取的參考計數會儲存在[m_dwRef](#m_dwref)中。

##  <a name="objectmain"></a>CComObjectRootEx：： ObjectMain

針對在物件對應中列出的每個類別，此函式會在初始化模組時呼叫一次，並在它終止時再次呼叫。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>參數

*bStarting*<br/>
脫銷如果正在初始化類別，則值為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

*BStarting*參數的值會指出模組是否正在初始化或終止。 `ObjectMain` 的預設執行不會執行任何工作，但是您可以在類別中覆寫這個函式，以初始化或清除您想要為類別配置的資源。 請注意，在要求類別的任何實例之前，會呼叫 `ObjectMain`。

會從 DLL 的進入點呼叫 `ObjectMain`，因此會限制進入點函式可執行檔作業類型。 如需這些限制的詳細資訊，請參閱[dll C++和 Visual 執行時間程式庫行為](../../build/run-time-library-behavior.md)和[DllMain](/windows/win32/Dlls/dllmain)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>CComObjectRootEx：： OuterAddRef

遞增匯總之外部未知的參考計數。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>傳回值

可能有助於診斷和測試的值。

##  <a name="outerqueryinterface"></a>CComObjectRootEx：： OuterQueryInterface

抓取所要求介面的間接指標。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
脫銷*Iid*中指定之介面指標的指標，如果匯總不支援介面，則為 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="outerrelease"></a>CComObjectRootEx：： OuterRelease

遞減匯總之外部未知的參考計數。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>傳回值

在非 debug 組建中，一律會傳回0。 在 [偵錯工具] 組建中，傳回可能有助於診斷或測試的值。

##  <a name="unlock"></a>CComObjectRootEx：： Unlock

如果執行緒模型為多執行緒，這個方法會呼叫 WIN32 API 函式[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，此函式會釋放透過私用資料成員取得之重要區段物件的擁有權。

```
void Unlock();
```

### <a name="remarks"></a>備註

若要取得擁有權，執行緒必須呼叫 `Lock`。 `Lock` 的每個呼叫都需要對應的 `Unlock` 呼叫，才能釋放重要區段的擁有權。

如果執行緒模型是單一執行緒，則這個方法不會執行任何操作。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
