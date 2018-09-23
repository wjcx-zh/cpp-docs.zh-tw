---
title: _WAIT_CHILD、_WAIT_GRANDCHILD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dd7b3fab51c382413c507831572afedd824c3f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018336"
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