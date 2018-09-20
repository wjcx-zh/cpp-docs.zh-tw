---
title: SimpleActivationFactory 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 111015fdd8887ae779aeb8fecc8274cfcf7c6c68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441274"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 類別

提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>參數

*基底*<br/>
基底類別。

## <a name="remarks"></a>備註

基底類別必須提供預設建構函式。

下列程式碼範例示範如何使用與 SimpleActivationFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集。

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance 方法](#activateinstance)|建立指定之介面的執行個體。|
|[SimpleActivationFactory::GetRuntimeClassName 方法](#getruntimeclassname)|取得所指定類別的執行個體的執行階段類別名稱*基底*類別範本參數。|
|[SimpleActivationFactory::GetTrustLevel 方法](#gettrustlevel)|取得所指定類別的執行個體的信任層級*基底*類別範本參數。|

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

`ActivationFactory`

`SimpleActivationFactory`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="activateinstance"></a>Simpleactivationfactory:: Activateinstance 方法

建立指定之介面的執行個體。

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>參數

*ppvObject*<br/>
這項作業完成時，所指定的物件執行個體的指標`Base`類別範本參數。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`是定義，判斷提示會發出錯誤如果類別範本參數中指定的基底類別不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或因未設定使用 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="getruntimeclassname"></a>Simpleactivationfactory:: Getruntimeclassname 方法

取得所指定類別的執行個體的執行階段類別名稱`Base`類別範本參數。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>參數

*runtimeName*<br/>
這項作業完成時，執行階段類別名稱。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`是定義，判斷提示會發出錯誤如果所指定的類別`Base`類別樣板參數不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或因未設定使用 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="gettrustlevel"></a>Simpleactivationfactory:: Gettrustlevel 方法

取得所指定類別的執行個體的信任層級`Base`類別範本參數。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>參數

*trustLvl*<br/>
這項作業完成時，目前類別物件的信任層級。

### <a name="return-value"></a>傳回值

一律傳回 S_OK。
