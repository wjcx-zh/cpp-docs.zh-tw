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
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745060"
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

## <a name="see-also"></a>另請參閱

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
