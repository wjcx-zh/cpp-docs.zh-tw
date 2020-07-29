---
title: SimpleClassFactory 類別
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 66794789e51a2635fae646cca49e4fae8385dfe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211147"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 類別

提供基本機制以建立基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>參數

*群體*<br/>
基類。

## <a name="remarks"></a>備註

基類必須提供預設的函式。

下列程式碼範例示範如何搭配 `SimpleClassFactory` [ActivatableClassWithFactoryEx](activatableclass-macros.md)宏使用。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 方法](#createinstance)|建立指定之介面的實例。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory：： CreateInstance 方法

建立指定之介面的實例。

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>參數

*pUnkOuter*<br/>
必須是 **`nullptr`** ，否則傳回值會是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支援匯總。 如果支援匯總，而且所建立的物件是匯總的一部分，則*pUnkOuter*會是匯總之控制 `IUnknown` 介面的指標。

*riid*<br/>
要建立之物件的介面識別碼。

*ppvObject*<br/>
當此作業完成時，為*riid*參數所指定之物件實例的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果已 `__WRL_STRICT__` 定義，則在類別樣板參數中指定的基類不是衍生自[RuntimeClass](runtimeclass-class.md)，或未使用 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md)列舉值來設定時，就會發出 assert 錯誤。
