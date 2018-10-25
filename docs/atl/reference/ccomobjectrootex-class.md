---
title: CComObjectRootEx 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 413485bc7675fbc68f2c224ceefdd0f552538eb9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076980"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別

這個類別提供方法來處理非彙總與彙總物件的物件參考計數管理。

## <a name="syntax"></a>語法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>參數

*ThreadModel*<br/>
類別，其方法實作所需的執行緒模型。 您可以設定，以明確選擇的執行緒模型*ThreadModel*要[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 您可以藉由設定接受伺服器的預設執行緒模型*ThreadModel*要[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或是[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|
|[InternalAddRef](#internaladdref)|非彙總物件的參考計數會遞增。|
|[InternalRelease](#internalrelease)|遞減參考計數為非彙總的物件。|
|[鎖定](#lock)|如果多執行緒的執行緒模型，取得重要區段物件的擁有權。|
|[解除鎖定](#unlock)|如果執行緒模型為多執行緒，釋放重要區段物件的擁有權。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法

|||
|-|-|
|[跖](#finalconstruct)|若要執行您的物件所需的任何初始化類別中覆寫。|
|[FinalRelease](#finalrelease)|在您執行您的物件所需的任何清除作業的類別中覆寫。|
|[OuterAddRef](#outeraddref)|遞增參考計數的彙總的物件。|
|[OuterQueryInterface](#outerqueryinterface)|會委派到外部`IUnknown`的彙總的物件。|
|[OuterRelease](#outerrelease)|遞減參考計數的彙總的物件。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|委派給`IUnknown`的非彙總的物件。|
|[ObjectMain](#objectmain)|在模組初始化和終止的物件對應中所列的衍生類別呼叫。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_dwRef](#m_dwref)|使用`m_pOuterUnknown`聯集的一部分。 未保留參考計數的彙總物件時，使用`AddRef`和`Release`。|
|[m_pOuterUnknown](#m_pouterunknown)|使用`m_dwRef`聯集的一部分。 以指標可要抓緊頭的外部未知彙總物件時使用。|

## <a name="remarks"></a>備註

`CComObjectRootEx` 處理非彙總與彙總物件的物件參考計數管理。 如果您的物件不正在彙總，而且存放的外部未知的指標，如果您的物件正在彙總，它就會保留物件參考計數。 對於彙總的物件，`CComObjectRootEx`方法可以用來處理失敗，內部物件的建構，並刪除保護以防止刪除內部介面發行時則外部物件或內部的物件。

實作的 COM 伺服器的類別必須繼承自`CComObjectRootEx`或是[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果您的類別定義會指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)巨集，ATL 建立的執行個體`CComPolyObject<CYourClass>`當`IClassFactory::CreateInstance`呼叫。 在建立期間，會檢查的外部未知的值。 如果它是 NULL，`IUnknown`實作非彙總的物件。 如果不是 NULL，外部未知`IUnknown`會彙總物件的實作。

如果您的類別未指定 DECLARE_POLY_AGGREGATABLE 巨集，ATL 建立的執行個體`CAggComObject<CYourClass>`彙總的物件或執行個體的`CComObject<CYourClass>`非彙總的物件。

使用的優點`CComPolyObject`避免擁有`CComAggObject`和`CComObject`處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 因此，只有一個複本的 vtable 和一份函式存在於您的模組。 如果您的 vtable 很大，這可以大幅降低您的模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`可能會導致稍微大一點的模組大小因為它不會最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。

如果您的物件已彙總， [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)藉由`CComAggObject`或`CComPolyObject`。 這些類別委派`QueryInterface`， `AddRef`，並`Release`呼叫`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`轉寄至的外部未知。 通常，您會覆寫`CComObjectRootEx::FinalConstruct`在您的類別，建立任何彙總的物件，並覆寫`CComObjectRootEx::FinalRelease`來釋放任何彙總物件。

如果您的物件不會彙總，`IUnknown`藉由`CComObject`或`CComPolyObject`。 在此情況下，呼叫`QueryInterface`， `AddRef`，並`Release`委派給`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`執行實際的作業。

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

建構函式會初始化為 0 的參考計數。

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

您可以執行您的物件所需的任何初始化衍生類別中覆寫這個方法。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

在成功或其中一個標準錯誤的 HRESULT 值傳回 S_OK。

### <a name="remarks"></a>備註

根據預設，`CComObjectRootEx::FinalConstruct`只會傳回 S_OK。

有執行中的初始設定的優點`FinalConstruct`而不是您的類別的建構函式：

- 您無法從建構函式，傳回狀態碼，但您可以傳回 HRESULT，藉由`FinalConstruct`的傳回值。 當正在使用 ATL 所提供的標準 class factory 來建立您的類別物件時，此傳回值會傳播回 COM 用戶端可讓您提供詳細的錯誤資訊。

- 您無法透過虛擬函式機制，從類別的建構函式呼叫虛擬函式。 從類別建構函式呼叫虛擬函式導致以統計方式解析呼叫函式，因為它在該點定義繼承階層架構中。 呼叫純虛擬函式會導致連結器錯誤。

   您的類別不是繼承階層架構中最具衍生性的類別，它依賴衍生類別提供的 ATL 提供其中一些功能。 很可能您的初始化需要使用該類別中 （特別是您類別的物件必須彙總的其他物件時），所提供的功能，但在您的類別建構函式具有無法存取這些功能。 您類別的建構程式碼執行之前的最具衍生性的類別就會完整建構。

   不過，`FinalConstruct`稱為立即之後最多衍生類別就會完整建構可讓您呼叫虛擬函式，並使用參考計數所提供的實作 ATL

### <a name="example"></a>範例

一般而言，覆寫這個方法在類別中衍生自`CComObjectRootEx`建立任何彙總物件。 例如: 

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果建構失敗，您可以傳回錯誤。 您也可以使用巨集[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)來保護您的外部物件無法刪除，如果在建立期間，內部彙總的物件遞增參考計數則遞減為 0。

以下是建立彙總的典型方式：

- 新增`IUnknown`指向您的類別物件，並將它初始化為 NULL 的建構函式。

- 覆寫`FinalConstruct`來建立彙總。

- 使用`IUnknown`您定義做為參數的指標[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)巨集。

- 覆寫`FinalRelease`釋放`IUnknown`指標。

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

您可以在您執行您的物件所需的任何清除作業的衍生類別中覆寫這個方法。

```
void FinalRelease();
```

### <a name="remarks"></a>備註

根據預設，`CComObjectRootEx::FinalRelease`不執行任何動作。

執行中的清理`FinalRelease`偏好將程式碼加入您的類別的解構函式，因為物件仍可獲得完整建構之起點在`FinalRelease`呼叫。 這可讓您安全地存取最具衍生性的類別所提供的方法。 這是特別重要，釋放任何彙總的物件，再刪除。

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

非彙總物件的參考計數遞增 1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷和測試。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒、`InterlockedIncrement`用來防止多個執行緒同時變更的參考計數。

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

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
[in]包含的介面公開至 COM 對應物件的指標`QueryInterface`。

*pEntries*<br/>
[in]指標`_ATL_INTMAP_ENTRY`存取的可用的介面對應的結構。

*iid*<br/>
[in]所要求介面的 GUID。

*ppvObject*<br/>
[out]在指定的介面指標的指標*iid*，或如果找不到介面則為 NULL。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

`InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件已彙總，`InternalQueryInterface`不會不會委派給外部未知。 您可以將介面輸入到 COM 對應表格巨集[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其中一個變數。

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

遞減參考計數的非彙總的物件加 1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>傳回值

在同時非偵錯及偵錯組建，此函數會傳回值可能是適用於診斷或測試。 確切的值取決於許多因素，例如作業系統使用，並可能，也可能不時，傳回做為參考計數。

### <a name="remarks"></a>備註

如果執行緒模型為多執行緒、`InterlockedDecrement`用來防止多個執行緒同時變更的參考計數。

##  <a name="lock"></a>  CComObjectRootEx::Lock

如果多執行緒的執行緒模型，這個方法會呼叫 Win32 API 函式[EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection)，哪一個等候，直到執行緒可以取得重要區段物件的擁有權取得透過私用資料成員。

```
void Lock();
```

### <a name="remarks"></a>備註

當受保護的程式碼完成執行後時，必須呼叫執行緒`Unlock`釋放重要區段的擁有權。

如果執行緒模型為單一執行緒，這個方法沒有任何作用。

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

存取記憶體的四個位元組的聯集的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>備註

使用`m_pOuterUnknown`聯集的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果物件不會彙總，來存取的參考計數`AddRef`並`Release`會儲存在`m_dwRef`。 如果彙總物件的外部未知的指標會儲存在[m_pOuterUnknown](#m_pouterunknown)。

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

存取記憶體的四個位元組的聯集的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>備註

使用`m_dwRef`聯集的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果彙總物件的外部未知的指標會儲存在`m_pOuterUnknown`。 如果物件不會彙總，來存取的參考計數`AddRef`並`Release`會儲存在[m_dwRef](#m_dwref)。

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

物件對應中所列每個類別，一旦初始化模組時，會呼叫此函數並再次時它就會終止。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>參數

*bStarting*<br/>
[out]值為 TRUE，如果正在初始化類別;否則為 FALSE。

### <a name="remarks"></a>備註

值*bStarting*參數會指出是否將模組正在初始化或終止。 預設實作`ObjectMain`不執行任何動作，但您可以在初始化或清除您想要的類別配置的資源類別中覆寫這個函式。 請注意，`ObjectMain`類別的任何執行個體要求之前呼叫。

`ObjectMain` 被呼叫從 DLL 的進入點，所以的進入點函式可以執行的作業類型會限制。 如需有關這些限制的詳細資訊，請參閱 < [Dll 和 Visual c + + 執行階段程式庫行為](../../build/run-time-library-behavior.md)並[DllMain](/windows/desktop/Dlls/dllmain)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

遞增參考計數的彙總的外部未知。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷和測試。

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

擷取要求之介面的間接指標。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]所要求介面的 GUID。

*ppvObject*<br/>
[out]在指定的介面指標的指標*iid*，或如果彙總不支援的介面，則為 NULL。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

遞減參考計數的彙總的外部未知。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>傳回值

在非偵錯組建中，一律會傳回 0。 在偵錯組建中，傳回值，可能有助於診斷或測試。

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

如果多執行緒的執行緒模型，這個方法會呼叫 Win32 API 函式[LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection)，透過私用資料成員取得的哪些版本的擁有權的重要區段物件。

```
void Unlock();
```

### <a name="remarks"></a>備註

若要取得擁有權，必須呼叫執行緒`Lock`。 每次呼叫`Lock`需要對應呼叫`Unlock`釋放重要區段的擁有權。

如果執行緒模型為單一執行緒，這個方法沒有任何作用。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
