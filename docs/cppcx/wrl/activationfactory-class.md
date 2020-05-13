---
title: ActivationFactory 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368698"
---
# <a name="activationfactory-class"></a>ActivationFactory 類別

讓 Windows 執行階段啟動一或多個類別。

## <a name="syntax"></a>語法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>參數

*I0*<br/>
第零個介面。

*I1*<br/>
第一個介面。

*I2*<br/>
第二個介面。

## <a name="remarks"></a>備註

`ActivationFactory`提供了介面的`IActivationFactory`註冊方法和基本功能。 `ActivationFactory`還使您能夠提供自定義工廠實現。

以下代碼片段象徵性地說明了如何使用激活工廠。

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

以下片段示範如何使用[實現](implements-structure.md)結構指定三個以上介面 ID。

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                       | 描述
---------------------------------------------------------- | ------------------------------------------
[啟動工廠::啟動工廠](#activationfactory) | 初始化 `ActivationFactory` 類別。

### <a name="public-methods"></a>公用方法

名稱                                                           | 描述
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[啟動工廠::新增參考](#addref)                           | 增加當前`ActivationFactory`物件的引用計數。
[啟動工廠::取得 Iid](#getiids)                         | 檢索實現的介面指示的陣組。
[啟動工廠::取得執行時類別名稱](#getruntimeclassname) | 獲取當前`ActivationFactory`實例化物件的運行時類名稱。
[啟用工廠:取得信任等級](#gettrustlevel)             | 獲取當前`ActivationFactory`實例化的物件的信任級別。
[啟動工廠::查詢介面](#queryinterface)           | 檢索指向指定介面的指標。
[啟動工廠::發佈](#release)                         | 取消當前`ActivationFactory`物件的引用計數。

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

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>啟動工廠::啟動工廠

初始化 `ActivationFactory` 類別。

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>啟動工廠::新增參考

增加當前`ActivationFactory`物件的引用計數。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="activationfactorygetiids"></a><a name="getiids"></a>啟動工廠::取得 Iid

檢索實現的介面指示的陣組。

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>參數

*iid( Iid) Count*<br/>
此操作完成後 *,iids*陣列中的 Interace ID 數。

*伊德*<br/>
此操作完成後,將包含一系列已實現的介面指示。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 E_OUTOFMEMORY可能是故障 HRESULT。

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>啟動工廠::取得執行時類別名稱

獲取當前`ActivationFactory`實例化物件的運行時類名稱。

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>參數

*執行時名稱*<br/>
此操作完成後,包含當前`ActivationFactory`實例化物件的運行時類名稱的字串的句柄。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>啟用工廠:取得信任等級

獲取當前`ActivationFactory`實例化的物件的信任級別。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>參數

*信任呂爾*<br/>
此操作完成後,`ActivationFactory`實體化執行時類別的信任等級。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,將發出斷言錯誤,並將*信任 Lvl*`FullTrust`設定為 。

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>啟動工廠::查詢介面

檢索指向指定介面的指標。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
此操作完成後,指向參數*riid*指定的介面的指標。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="activationfactoryrelease"></a><a name="release"></a>啟動工廠::發佈

取消當前`ActivationFactory`物件的引用計數。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。
