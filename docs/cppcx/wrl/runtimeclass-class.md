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
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376227"
---
# <a name="runtimeclass-class"></a>RuntimeClass 類別

表示繼承指定介面並提供指定的 Windows 執行時、經典 COM 和弱引用支援的 WinRT 或 COM 類。

此類提供 WinRT 和 COM 類的樣`QueryInterface`板`AddRef`實現`Release`,提供的實現, 等,管理模組的引用計數,並支援為可啟動物件提供類工廠。

## <a name="syntax"></a>語法

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>參數

*類別標誌*<br/>
選擇性參數。 一個或多個[運行時類類型](runtimeclasstype-enumeration.md)枚舉值的組合。 可以`__WRL_CONFIGURATION_LEGACY__`定義宏來更改專案中所有運行時類的 classFlags 的預設值。 如果定義,運行時類實例默認情況下是非敏捷的。 如果未定義運行時類實例,默認情況下是敏捷的。 為了避免歧義,`Microsoft::WRL::FtmBase`請永遠`TInterfaces``RuntimeClassType::InhibitFtmBase`指定的或 。 請注意,如果使用 InhibitFtmBase 和 FtmBase,則物件將是敏捷的。

*T 介面*<br/>
物件實現超出`IUnknown`的介面清單,`IInspectable`或[由執行時ClassType](runtimeclasstype-enumeration.md)控制的其他介面。 它還可能列出要派生的其他類,特別是`Microsoft::WRL::FtmBase`使物件變得敏捷,並使其`IMarshal`實現 。

## <a name="members"></a>成員

`RuntimeClassInitialize`<br/>
一個函數,用於構造物件時`MakeAndInitialize`初始化物件的函數。 如果物件成功初始化,它將返回S_OK;如果初始化失敗,則返回 COM 錯誤代碼。 COM 錯誤代碼作為的傳回`MakeAndInitialize`值傳播 。 請注意,如果使用`RuntimeClassInitialize`範本函數建構物件`Make`, 則不調用 該方法。

### <a name="public-constructors"></a>公用建構函式

| 名稱                                               | 描述                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [執行時類:執行時類](#runtimeclass)        | 初始化類的`RuntimeClass`當前實例。   |
| [執行時類::=運行時類](#tilde-runtimeclass) | 取消初始化類的`RuntimeClass`當前實例。 |

### <a name="public-methods"></a>公用方法

| 名稱                                                      | 描述                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [執行時類::添加參考](#addref)                           | 增加當前`RuntimeClass`物件的引用計數。                              |
| [執行時類::Decrement 參考](#decrementreference)   | 取消當前`RuntimeClass`物件的引用計數。                              |
| [執行時類::取得 Iid](#getiids)                         | 獲取一個陣列,該陣列可以包含當前`RuntimeClass`物件實現的介面指示。 |
| [執行時類::取得執行時類名稱](#getruntimeclassname) | 獲取當前`RuntimeClass`物件的運行時類名稱。                                  |
| [執行時類::取得信任等級](#gettrustlevel)             | 獲取當前`RuntimeClass`物件的信任級別。                                         |
| [執行時類::取得 Weak 引用](#getweakreference)       | 獲取指向當前`RuntimeClass`物件的弱引用對象的指標。                 |
| [執行時類::內部AddRef](#internaladdref)           | 將引用計數遞增到當前`RuntimeClass`物件。                               |
| [執行時類::查詢介面](#queryinterface)           | 檢索指向指定介面 ID 的指標。                                                 |
| [運行時類::發佈](#release)                         | 對當前`RuntimeClass`物件執行 COM 釋放操作。                             |

## <a name="inheritance-hierarchy"></a>繼承階層架構

這是實作的詳細資料。

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間：** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>執行時類::=運行時類

取消初始化類的`RuntimeClass`當前實例。

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>執行時類::添加參考

增加當前`RuntimeClass`物件的引用計數。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>執行時類::Decrement 參考

取消當前`RuntimeClass`物件的引用計數。

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>執行時類::取得 Iid

獲取一個陣列,該陣列可以包含當前`RuntimeClass`物件實現的介面指示。

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>參數

*iid( Iid) Count*<br/>
此操作完成後,陣列*iid*中的元素總數。

*伊德*<br/>
此操作完成後,指向介面指示陣列的指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_OUTOFMEMORY。

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>執行時類::取得執行時類名稱

獲取當前`RuntimeClass`物件的運行時類名稱。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>參數

*執行時名稱*<br/>
此操作完成後,運行時類名稱。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__``__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`或 未定義,將發出斷言錯誤。

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>執行時類::取得信任等級

獲取當前`RuntimeClass`物件的信任級別。

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>參數

*信任呂爾*<br/>
此操作完成後,當前`RuntimeClass`物件的信任級別。

### <a name="return-value"></a>傳回值

總是S_OK。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__``__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`或 未定義,將發出斷言錯誤。

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>執行時類::取得 Weak 引用

獲取指向當前`RuntimeClass`物件的弱引用對象的指標。

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>參數

*弱參考*<br/>
此操作完成後,指向弱引用物件的指標。

### <a name="return-value"></a>傳回值

總是S_OK。

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>執行時類::內部AddRef

將引用計數遞增到當前`RuntimeClass`物件。

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

生成的引用計數。

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>執行時類::查詢介面

檢索指向指定介面 ID 的指標。

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
完成此操作後,指向*riid*參數指定的介面的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="runtimeclassrelease"></a><a name="release"></a>運行時類::發佈

對當前`RuntimeClass`物件執行 COM 釋放操作。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果引用計數變為零,則`RuntimeClass`刪除該物件。

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>執行時類:執行時類

初始化類的`RuntimeClass`當前實例。

```cpp
RuntimeClass();
```
