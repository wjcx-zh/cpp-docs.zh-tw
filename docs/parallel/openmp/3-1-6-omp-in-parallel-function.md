---
title: 3.1.6 omp_in_parallel 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404614"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函式

**Omp_in_parallel**函式會傳回非零值，如果它動態程度以平行方式執行的平行區域內呼叫; 否則它會傳回 0。 格式如下：

```
#include <omp.h>
int omp_in_parallel(void);
```

此函數會傳回非零值，以平行方式，包括序列化的巢狀的區域執行的區域中呼叫時。