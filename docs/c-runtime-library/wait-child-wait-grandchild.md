---
title: _WAIT_CHILD、_WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: 714b4e79f1c229817a12908aad0d726f74023036
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524387"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD、_WAIT_GRANDCHILD

## <a name="syntax"></a>語法

```

#include <process.h>
```

## <a name="remarks"></a>備註

`_cwait` 函式可以由任何處理序用來等候任何其他處理序 (若處理序識別碼為已知)。 動作引數可以是下列其中一個值：

|常數|意義|
|--------------|-------------|
|`_WAIT_CHILD`|發出呼叫的處理序將等候指定的新處理序終止。|
|`_WAIT_GRANDCHILD`|發出呼叫的處理序將等候指定的新處理序以及由該新處理序建立的所有處理序終止。|

## <a name="see-also"></a>請參閱

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)