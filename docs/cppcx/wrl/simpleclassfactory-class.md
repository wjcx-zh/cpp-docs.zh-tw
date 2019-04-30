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
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403074"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 類別

提供基本機制以建立基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>參數

*基底*<br/>
基底類別。

## <a name="remarks"></a>備註

基底類別必須提供預設建構函式。

下列程式碼範例示範如何使用`SimpleClassFactory`具有[ActivatableClassWithFactoryEx](activatableclass-macros.md)巨集。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 方法](#createinstance)|建立指定之介面的執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

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

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="createinstance"></a>Simpleclassfactory:: Createinstance 方法

建立指定之介面的執行個體。

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>參數

*pUnkOuter*<br/>
必須是`nullptr`; 否則傳回的值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支援彙總。 如果已支援彙總，但所建立的物件已是在彙總的一部分*pUnkOuter*會是指標，以控制`IUnknown`彙總的介面。

*riid*<br/>
介面若要建立之物件的識別碼。

*ppvObject*<br/>
這項作業完成時，所指定的物件執行個體的指標*riid*參數。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`是定義，判斷提示會發出錯誤如果類別範本參數中指定的基底類別不衍生自[RuntimeClass](runtimeclass-class.md)，或因未設定 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md)列舉值。
