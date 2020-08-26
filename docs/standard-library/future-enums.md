---
title: '&lt;future&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 45dc3277b3f14b7f9dbb043cf9db1f1865d4e4c9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838018"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 列舉

[future_errc](#future_errc)\
[future_status](#future_status)\
[啟動](#launch)

## <a name="future_errc-enumeration"></a><a name="future_errc"></a> future_errc 列舉

為 [future_error](../standard-library/future-error-class.md) 類別所回報的所有錯誤提供符號名稱。

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a> future_status 列舉

為計時的 wait 函式可傳回的原因提供符號名稱。

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a> 啟動列舉

代表一種位元遮罩類型，描述範本函式 [async](../standard-library/future-functions.md#async) 可能的模式。

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>另請參閱

[\<future>](../standard-library/future.md)
