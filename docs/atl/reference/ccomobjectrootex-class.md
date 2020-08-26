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
ms.openlocfilehash: b4dbc42cb0c6fe2c9c6692e0db37267ce3fff361
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833643"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別

這個類別提供方法來處理非匯總和匯總物件的物件參考計數管理。

## <a name="syntax"></a>語法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>參數

*ThreadModel*<br/>
類別，其方法會執行所需的執行緒模型。 您可以將 *ThreadModel* 設定為 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，以明確選擇執行緒模型。 您可以將 *ThreadModel* 設定為 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) 或 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)，以接受伺服器的預設執行緒模型。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|函式|描述|
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|
|[InternalAddRef](#internaladdref)|遞增非匯總物件的參考計數。|
|[InternalRelease](#internalrelease)|遞減非匯總物件的參考計數。|
|[鎖定](#lock)|如果執行緒模型為多執行緒，則取得重要區段物件的擁有權。|
|[解 鎖](#unlock)|如果執行緒模型為多執行緒，則釋放重要區段物件的擁有權。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法

|函式|描述|
|-|-|
|[FinalConstruct](#finalconstruct)|在您的類別中覆寫，以執行您的物件所需的任何初始化。|
|[FinalRelease](#finalrelease)|在您的類別中覆寫，以執行您的物件所需的任何清除。|
|[OuterAddRef](#outeraddref)|遞增匯總物件的參考計數。|
|[OuterQueryInterface](#outerqueryinterface)|委派至 `IUnknown` 匯總物件的外部。|
|[OuterRelease](#outerrelease)|遞減匯總物件的參考計數。|

### <a name="static-functions"></a>靜態函式

|函式|描述|
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|委派至 `IUnknown` 非匯總物件的。|
|[ObjectMain](#objectmain)|在模組初始化期間呼叫，並且在物件對應中所列的衍生類別終止時呼叫。|

### <a name="data-members"></a>資料成員

|資料成員|描述|
|-|-|
|[m_dwRef](#m_dwref)|With `m_pOuterUnknown` （union 的一部分）。 當物件未匯總以保存和的參考計數時使用 `AddRef` `Release` 。|
|[m_pOuterUnknown](#m_pouterunknown)|With `m_dwRef` （union 的一部分）。 在匯總物件以保存外部未知指標時使用。|

## <a name="remarks"></a>備註

`CComObjectRootEx` 處理非匯總和匯總物件的物件參考計數管理。 如果您的物件未進行匯總，它會保存物件參考計數，如果您的物件正在匯總，則會將指標保留為未知。 針對匯總的物件， `CComObjectRootEx` 方法可以用來處理內建物件所要建立的失敗，並在釋放內部介面或刪除內建物件時，保護外部物件的刪除。

實 COM 伺服器的類別必須繼承自 `CComObjectRootEx` 或 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果您的類別定義指定 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) 宏， `CComPolyObject<CYourClass>` 則 ATL 會在呼叫時建立的實例 `IClassFactory::CreateInstance` 。 在建立期間，會檢查外部 [未知] 的值。 如果是 Null， `IUnknown` 就會針對非匯總物件來執行。 如果外部未知不是 Null， `IUnknown` 就會針對匯總的物件執行。

如果您的類別未指定 DECLARE_POLY_AGGREGATABLE 宏，ATL 會 `CAggComObject<CYourClass>` 為非匯總物件的匯總物件或實例建立的實例 `CComObject<CYourClass>` 。

使用的優點 `CComPolyObject` 是您可以避免在 `CComAggObject` 模組中同時使用和 `CComObject` 來處理匯總和非匯總案例。 單一 `CComPolyObject` 物件會處理這兩種情況。 因此，您的模組中只會有一個 vtable 複本和一個函數複本。 如果您的 vtable 很大，這可能會大幅降低您的模組大小。 但是，如果您的 vtable 很小，使用 `CComPolyObject` 可能會產生稍微較大的模組大小，因為它並未針對匯總或非匯總的物件優化，如同 `CComAggObject` 和 `CComObject` 。

如果您的物件已匯總，則會由或實作為 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) `CComAggObject` `CComPolyObject` 。 這些類別會將、和呼叫委派給、和， `QueryInterface` `AddRef` `Release` `CComObjectRootEx` `OuterQueryInterface` `OuterAddRef` `OuterRelease` 以轉寄至外部未知。 一般而言，您會 `CComObjectRootEx::FinalConstruct` 在類別中覆寫以建立任何匯總物件，並覆寫 `CComObjectRootEx::FinalRelease` 以釋放任何匯總的物件。

如果您的物件未匯總， `IUnknown` 則會由 `CComObject` 或實作為 `CComPolyObject` 。 在此情況下， `QueryInterface` `AddRef` 會將、和的呼叫 `Release` 委派給 `CComObjectRootEx` 的、和， `InternalQueryInterface` `InternalAddRef` `InternalRelease` 以執行實際的作業。

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a> CComObjectRootEx：： CComObjectRootEx

此函數會將參考計數初始化為0。

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a> CComObjectRootEx：： FinalConstruct

您可以在衍生類別中覆寫這個方法，以執行您的物件所需的任何初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

傳回成功或其中一個標準錯誤 HRESULT 值的 S_OK。

### <a name="remarks"></a>備註

根據預設， `CComObjectRootEx::FinalConstruct` 只會傳回 S_OK。

在中執行初始化， `FinalConstruct` 而不是類別的函式，會有一些優點：

- 您無法從函式傳回狀態碼，但您可以透過的傳回值傳回 HRESULT `FinalConstruct` 。 當您使用 ATL 所提供的標準 class factory 來建立類別的物件時，此傳回值會傳播回 COM 用戶端，讓您提供詳細的錯誤資訊。

- 您無法從類別的函式使用虛擬函式機制來呼叫虛擬函式。 從類別的函式呼叫虛擬函式時，會產生靜態解析的函式呼叫，因為它是在繼承階層中的該點定義。 呼叫純虛擬函式會導致連結器錯誤。

   您的類別不是繼承階層架構中最常衍生的類別，它依賴 ATL 提供的衍生類別來提供其部分功能。 您的初始化很有可能需要使用該類別所提供的功能 (當您類別的物件需要將其他物件匯總) ，但您的類別中的函式無法存取這些功能時，這是正確的。 您類別的結構程式碼會在完全建立最衍生的類別之前執行。

   不過，在 `FinalConstruct` 完整建立衍生的類別之後，會立即呼叫，讓您能夠呼叫虛擬函式，並使用 ATL 所提供的參考計數實作為參考。

### <a name="example"></a>範例

通常會在衍生自的類別中覆寫這個方法， `CComObjectRootEx` 以建立任何匯總的物件。 例如：

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果結構失敗，您可能會傳回錯誤。 您也可以使用宏 [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) ，以防止外部物件被刪除，如果在建立期間，內部匯總物件會遞增參考計數，然後將計數遞減為0。

以下是建立匯總的一般方式：

- 將 `IUnknown` 指標加入至您的類別物件，並在函式中將它初始化為 Null。

- 覆寫 `FinalConstruct` 以建立匯總。

- 使用 `IUnknown` 您定義的指標做為 [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) 宏的參數。

- 覆寫 `FinalRelease` 以釋放 `IUnknown` 指標。

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a> CComObjectRootEx：： FinalRelease

您可以在衍生類別中覆寫這個方法，以執行您的物件所需的任何清除。

```cpp
void FinalRelease();
```

### <a name="remarks"></a>備註

預設 `CComObjectRootEx::FinalRelease` 不會執行任何動作。

`FinalRelease`若要將程式碼加入至類別的函式，最好是將程式碼加入至類別的函式，因為物件仍會在呼叫的位置進行完整的結構化 `FinalRelease` 。 這可讓您安全地存取由最衍生的類別所提供的方法。 這對於在刪除之前釋放任何匯總的物件而言特別重要。

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a> CComObjectRootEx：： InternalAddRef

將非匯總物件的參考計數遞增1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

可能適用于診斷和測試的值。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒， `InterlockedIncrement` 則用來防止一個以上的執行緒同時變更參考計數。

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a> CComObjectRootEx：： InternalQueryInterface

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
在物件的指標，該物件包含公開之介面的 COM 對應 `QueryInterface` 。

*pEntries*<br/>
在 `_ATL_INTMAP_ENTRY` 存取可用介面對應之結構的指標。

*Iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
擴展 *Iid*中指定之介面指標的指標，如果找不到介面，則為 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件已匯總，則 `InternalQueryInterface` 不會委派給外部未知。 您可以使用宏 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 或其中一個變體來輸入 COM map 資料表中的介面。

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a> CComObjectRootEx：： InternalRelease

將非匯總物件的參考計數遞減1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>傳回值

在非 debug 錯和 debug 組建中，此函式會傳回一個值，這個值可能有助於診斷或測試。 傳回的確切值取決於許多因素，例如使用的作業系統，而且不一定是參考計數。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒， `InterlockedDecrement` 則用來防止一個以上的執行緒同時變更參考計數。

## <a name="ccomobjectrootexlock"></a><a name="lock"></a> CComObjectRootEx：： Lock

如果執行緒模型為多執行緒，這個方法會呼叫 WIN32 API 函式 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，它會等到執行緒可以取得透過私用資料成員取得之重要區段物件的擁有權。

```cpp
void Lock();
```

### <a name="remarks"></a>備註

當受保護的程式碼完成執行時，執行緒必須呼叫 `Unlock` 來釋放重要區段的擁有權。

如果執行緒模型為單一執行緒，則這個方法不會執行任何動作。

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a> CComObjectRootEx：： m_dwRef

存取四個位元組記憶體的等位的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>備註

With `m_pOuterUnknown` ，union 的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果未匯總物件，則由和存取的參考計數 `AddRef` `Release` 會儲存在中 `m_dwRef` 。 如果物件已匯總，則外部未知的指標會儲存在 [m_pOuterUnknown](#m_pouterunknown)中。

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a> CComObjectRootEx：： m_pOuterUnknown

存取四個位元組記憶體的等位的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>備註

With `m_dwRef` ，union 的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果已匯總物件，則會將外部未知的指標儲存在中 `m_pOuterUnknown` 。 如果未匯總物件，則存取的參考計數 `AddRef` `Release` 會儲存在 [m_dwRef](#m_dwref)中。

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a> CComObjectRootEx：： ObjectMain

針對物件對應中列出的每個類別，此函式會在初始化模組時呼叫一次，並在終止時呼叫。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>參數

*bStarting*<br/>
擴展如果正在初始化類別，則此值為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

*BStarting*參數的值會指出模組是否正在初始化或終止。 的預設執行 `ObjectMain` 不會執行任何動作，但是您可以在類別中覆寫這個函式，以初始化或清除您想要為類別配置的資源。 請注意， `ObjectMain` 會在要求類別的任何實例之前呼叫。

`ObjectMain` 從 DLL 的進入點呼叫，因此，進入點函數可以執行的作業類型會受到限制。 如需這些限制的詳細資訊，請參閱 [dll 和 Visual C++ 執行時間程式庫行為](../../build/run-time-library-behavior.md) 和 [DllMain](/windows/win32/Dlls/dllmain)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a> CComObjectRootEx：： OuterAddRef

遞增匯總之外部未知的參考計數。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>傳回值

可能適用于診斷和測試的值。

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a> CComObjectRootEx：： OuterQueryInterface

抓取所要求介面的間接指標。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
擴展 *Iid*中指定之介面指標的指標，如果匯總不支援介面，則為 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a> CComObjectRootEx：： OuterRelease

遞減匯總之外部未知的參考計數。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>傳回值

在非 debug 組建中，一律會傳回0。 在 debug 組建中，會傳回可能有助於診斷或測試的值。

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a> CComObjectRootEx：： Unlock

如果執行緒模型為多執行緒，這個方法會呼叫 WIN32 API 函式 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，此函式會釋放透過私用資料成員取得之重要區段物件的擁有權。

```cpp
void Unlock();
```

### <a name="remarks"></a>備註

若要取得擁有權，執行緒必須呼叫 `Lock` 。 的每個呼叫都 `Lock` 需要對應的呼叫， `Unlock` 才能釋放重要區段的擁有權。

如果執行緒模型為單一執行緒，則這個方法不會執行任何動作。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
