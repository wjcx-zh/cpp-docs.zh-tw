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
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373554"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 類別

提供基本機制以建立基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>參數

*基地*<br/>
基類。

## <a name="remarks"></a>備註

基類必須提供預設構造函數。

以下代碼示例演示如何與`SimpleClassFactory`[可啟動類與 FactoryEx](activatableclass-macros.md)宏一起使用。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 方法](#createinstance)|建立指定介面的實例。|

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

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>簡單類工廠::創建實例方法

建立指定介面的實例。

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>參數

*pUnkOuter*<br/>
必須是`nullptr`;否則,返回值CLASS_E_NOAGGREGATION。

簡單類工廠不支援聚合。 如果支援聚合,並且正在創建的對像是聚合的一部分,*則 pUnkOuter*將是指向`IUnknown`聚合控制 介面的指標。

*riid*<br/>
要創建的物件的介面 ID。

*ppvObject*<br/>
此操作完成後,指標指向*riid*參數指定的物件的實例。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`已定義,如果類範本參數中指定的基類不是從[運行時類](runtimeclass-class.md)派生,或者未配置 ClassicCom 或 WinRtClassicComMix[運行時類型](runtimeclasstype-enumeration.md)枚舉值,則將發出斷言錯誤。
