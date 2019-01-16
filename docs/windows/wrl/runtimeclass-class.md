---
title: RuntimeClass 類別
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: d45fe7c6d794f216da93ffbd95dbb7058d3336f3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336052"
---
# <a name="runtimeclass-class"></a>RuntimeClass 類別

表示繼承指定的介面，並提供指定的 Windows 執行階段、 傳統 COM 和弱式參考支援 WinRT 或 COM 類別。

這個類別會提供 WinRT 及 COM 的類別，提供的實作的未定案實作`QueryInterface`， `AddRef`，`Release`等等管理模組的參考計數，並支援提供的 class factory可啟動的物件。

## <a name="syntax"></a>語法

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>參數

*classFlags*<br/>
選擇性參數。 一或多個組合[RuntimeClassType](runtimeclasstype-enumeration.md)列舉值。 `__WRL_CONFIGURATION_LEGACY__`巨集可以定義變更 classFlags 專案中的所有執行階段類別的預設值。 如果定義，RuntimeClass 執行個體是非 agile 預設。 未定義，RuntimeClass 執行個體皆為敏捷式預設。 若要避免模稜兩可一律指定`Microsoft::WRL::FtmBase`中`TInterfaces`或`RuntimeClassType::InhibitFtmBase`。 請注意，如果 InhibitFtmBase 和 FtmBase 兩者都用物件將會是敏捷式軟體開發。

*TInterfaces*<br/>
介面清單物件會實作超越`IUnknown`，`IInspectable`或其他介面受到[RuntimeClassType](runtimeclasstype-enumeration.md)。 它也可能會列出其他類別以值得注意的是衍生自`Microsoft::WRL::FtmBase`使敏捷式軟體開發的物件，並將它實作`IMarshal`。

## <a name="members"></a>成員

`RuntimeClassInitialize`<br/>
用來初始化物件，如果函式`MakeAndInitialize`樣板函式用來建構物件。 如果初始化失敗，，傳回 S_OK，如果物件已成功初始化或 COM 錯誤碼。 COM 錯誤程式碼會傳播的傳回值為`MakeAndInitialize`。 請注意，`RuntimeClassInitialize`方法不會呼叫如果`Make`樣板函式用來建構物件。

### <a name="public-constructors"></a>公用建構函式

| 名稱                                               | 描述                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | 初始化目前的執行個體`RuntimeClass`類別。   |
| [RuntimeClass::~RuntimeClass](#tilde-runtimeclass) | 取消初始化目前的執行個體`RuntimeClass`類別。 |

### <a name="public-methods"></a>公用方法

| 名稱                                                      | 描述                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | 遞增參考計數目前`RuntimeClass`物件。                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | 遞減參考計數目前`RuntimeClass`物件。                              |
| [RuntimeClass::GetIids](#getiids)                         | 取得陣列，其中可包含的介面識別碼，藉由將目前`RuntimeClass`物件。 |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | 取得目前的執行階段類別名稱`RuntimeClass`物件。                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | 取得目前的信任層級`RuntimeClass`物件。                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | 取得目前的弱式參考的物件指標`RuntimeClass`物件。                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | 目前的參考計數遞增`RuntimeClass`物件。                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | 擷取指定的介面 ID 的指標                                                 |
| [RuntimeClass::Release](#release)                         | 執行 COM 釋放作業對目前`RuntimeClass`物件。                             |

## <a name="inheritance-hierarchy"></a>繼承階層

這是實作詳細資料。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="tilde-runtimeclass"></a>RuntimeClass:: ~ RuntimeClass

取消初始化目前的執行個體`RuntimeClass`類別。

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>RuntimeClass::AddRef

遞增參考計數目前`RuntimeClass`物件。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="decrementreference"></a>RuntimeClass::DecrementReference

遞減參考計數目前`RuntimeClass`物件。

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="getiids"></a>RuntimeClass::GetIids

取得陣列，其中可包含的介面識別碼，藉由將目前`RuntimeClass`物件。

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>參數

*iidCount*<br/>
這項作業完成時，陣列中的元素總數*iid*。

*iids*<br/>
這項作業完成時，介面識別碼的陣列的指標。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_OUTOFMEMORY。

## <a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

取得目前的執行階段類別名稱`RuntimeClass`物件。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>參數

*runtimeName*<br/>
這項作業完成時，執行階段類別名稱。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果，就會發出判斷提示時發生`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`未定義。

## <a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

取得目前的信任層級`RuntimeClass`物件。

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>參數

*trustLvl*<br/>
這項作業完成時，目前的信任層級`RuntimeClass`物件。

### <a name="return-value"></a>傳回值

一律傳回 S_OK。

### <a name="remarks"></a>備註

如果，就會發出判斷提示時發生`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`未定義。

## <a name="getweakreference"></a>RuntimeClass::GetWeakReference

取得目前的弱式參考的物件指標`RuntimeClass`物件。

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>參數

*weakReference*<br/>
這項作業完成時，弱式參考物件的指標。

### <a name="return-value"></a>傳回值

一律傳回 S_OK。

## <a name="internaladdref"></a>RuntimeClass::InternalAddRef

目前的參考計數遞增`RuntimeClass`物件。

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

產生的參考計數。

## <a name="queryinterface"></a>RuntimeClass::QueryInterface

擷取指定的介面 ID 的指標

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
此 opereation 完成時，所指定之介面的指標*riid*參數。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="release"></a>RuntimeClass::Release

執行 COM 釋放作業對目前`RuntimeClass`物件。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果參考計數變成零時，`RuntimeClass`刪除物件。

## <a name="runtimeclass"></a>RuntimeClass::RuntimeClass

初始化目前的執行個體`RuntimeClass`類別。

```cpp
RuntimeClass();
```
