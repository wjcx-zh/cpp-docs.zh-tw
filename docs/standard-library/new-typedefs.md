---
title: '&lt;new&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549114"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedef

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

此類型會指向適合用來作為新處理常式的函式。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>備註

當 **operatornew** 或 `operator new[]` 無法滿足提供額外儲存體的要求時，便會呼叫此類型的處理常式函式。

### <a name="example"></a>範例

如需使用 `new_handler` 作為傳回值的範例，請參閱 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。

## <a name="see-also"></a>另請參閱

[\<new>](../standard-library/new.md)<br/>
