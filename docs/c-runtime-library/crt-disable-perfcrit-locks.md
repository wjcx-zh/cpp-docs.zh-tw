---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: b6f4d8dee5577e88aa59af9bff017aab0c7eef89
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740261"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

停用 I/O 作業中的效能嚴重不足鎖定。

## <a name="syntax"></a>語法

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>備註

定義此符號可透過強制所有 I/O 作業採用單一執行緒 I/O 模型，來提升單一執行緒 I/O 繫結程式的效能。 如需詳細資訊，請參閱[多執行緒程式庫效能](../c-runtime-library/multithreaded-libraries-performance.md)。

## <a name="see-also"></a>另請參閱

[全域常數](../c-runtime-library/global-constants.md)
