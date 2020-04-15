---
title: SimpleActivationFactory 類別
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370943"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 類別

提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>參數

*基地*<br/>
基類。

## <a name="remarks"></a>備註

基類必須提供預設構造函數。

以下代碼示例演示如何將簡單啟動工廠與[可啟動的類與 FactoryEx](activatableclass-macros.md)宏一起使用。

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance 方法](#activateinstance)|建立指定介面的實例。|
|[SimpleActivationFactory::GetRuntimeClassName 方法](#getruntimeclassname)|獲取*Base*類範本參數指定的類實例的運行時類名稱。|
|[SimpleActivationFactory::GetTrustLevel 方法](#gettrustlevel)|獲取*Base*類範本參數指定的類實例的信任級別。|

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

`ActivationFactory`

`SimpleActivationFactory`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>簡單啟動工廠::啟動實體方法

建立指定介面的實例。

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>參數

*ppvObject*<br/>
此操作完成後,將指標指向`Base`類範本參數指定的物件的實例。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`已定義,如果類範本參數中指定的基類不是從[RuntimeClass](runtimeclass-class.md)派生,或者未配置 WinRt 或 WinRtClassicComMix[運行時類型](runtimeclasstype-enumeration.md)枚舉值,則將發出斷言錯誤。

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>簡單啟動工廠::取得執行時類別名稱方法

獲取`Base`類範本參數指定的類實例的運行時類名稱。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>參數

*執行時名稱*<br/>
此操作完成後,運行時類名稱。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如果`__WRL_STRICT__`已定義,`Base`如果 類範本參數指定的類不是從[RuntimeClass](runtimeclass-class.md)派生,或者未配置 WinRt 或 WinRtClassicComMix[運行時類型](runtimeclasstype-enumeration.md)枚舉值,則將發出斷言錯誤。

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>簡單啟動工廠::取得信任等級方法

獲取`Base`類範本參數指定的類實例的信任級別。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>參數

*信任呂爾*<br/>
此操作完成後,當前類物件的信任級別。

### <a name="return-value"></a>傳回值

總是S_OK。
