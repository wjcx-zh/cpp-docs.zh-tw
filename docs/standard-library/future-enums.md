---
title: '&lt;future&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: a5bcebd80b296a0b8416580aa03acc59ce3750cd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865165"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 列舉

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[產品](#launch)|

## <a name="future_errc"></a>  future_errc 列舉

為 [future_error](../standard-library/future-error-class.md) 類別所回報的所有錯誤提供符號名稱。

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status"></a>  future_status 列舉

為計時的 wait 函式可傳回的原因提供符號名稱。

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch"></a>  launch 列舉

代表一種位元遮罩類型，描述範本函式 [async](../standard-library/future-functions.md#async) 可能的模式。

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>另請參閱

[\<future>](../standard-library/future.md)
