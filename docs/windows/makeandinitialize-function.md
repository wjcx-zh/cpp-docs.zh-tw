---
title: MakeAndInitialize 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 4dbcd208acb52522c24f1cc442e2cc1908b51502
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332279"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 函式

初始化指定的 Windows 執行階段類別。 使用此函式來具現化在相同的模組中定義的元件。

## <a name="syntax"></a>語法

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>參數

*T*<br/>
使用者指定的類別繼承自`WRL::RuntimeClass`。

*TArg1*<br/>
傳遞至指定的執行階段類別的引數 1 的型別。

*TArg2*<br/>
傳遞至指定的執行階段類別的引數 2 的型別。

*TArg3*<br/>
傳遞至指定的執行階段類別的引數 3 的型別。

*TArg4*<br/>
傳遞至指定的執行階段類別的引數 4 類型。

*TArg5*<br/>
引數 5 傳遞至指定的執行階段類別的型別。

*TArg6*<br/>
傳遞至指定的執行階段類別的引數 6 的型別。

*TArg7*<br/>
引數 7 傳遞至指定的執行階段類別的型別。

*TArg8*<br/>
引數 8 傳遞至指定的執行階段類別的型別。

*TArg9*<br/>
引數 9 的傳遞至指定的執行階段類別的型別。

*arg1*<br/>
傳遞至指定的執行階段類別的引數 1。

*Arg2*<br/>
傳遞至指定的執行階段類別的引數 2。

*arg3*<br/>
傳遞至指定的執行階段類別的引數 3。

*arg4*<br/>
傳遞至指定的執行階段類別的引數 4。

*arg5*<br/>
傳遞至指定的執行階段類別的引數 5。

*arg6*<br/>
傳遞至指定的執行階段類別的引數 6。

*arg7*<br/>
傳遞至指定的執行階段類別的引數 7。

*arg8*<br/>
傳遞至指定的執行階段類別的引數 8。

*arg9*<br/>
傳遞至指定的執行階段類別的引數 9。

## <a name="return-value"></a>傳回值

HRESULT 值。

## <a name="remarks"></a>備註

請參閱[如何： 直接具現化 WRL 元件](../windows/how-to-instantiate-wrl-components-directly.md)若要了解此函式之間的差異並[Microsoft::WRL::Make](../windows/make-function.md)，及範例。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)