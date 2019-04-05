---
title: Make 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: b45337ef773f93968570f62ab73c02d11fae88ff
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028243"
---
# <a name="make-function"></a>Make 函式

初始化指定的 Windows 執行階段類別。 使用此函式來具現化在相同的模組中定義的元件。

## <a name="syntax"></a>語法

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

*arg2*<br/>
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

A`ComPtr<T>`物件，如果成功，否則`nullptr`。

## <a name="remarks"></a>備註

請參閱[如何：直接 WRL 元件具現化](how-to-instantiate-wrl-components-directly.md)若要了解此函式之間的差異並[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)，及範例。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)