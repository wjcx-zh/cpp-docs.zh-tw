---
title: 屏障 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c220106d62bf65505c9c5b48085a9ee3e67fe0cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415027"
---
# <a name="barrier"></a>barrier

同步處理的小組中的所有執行緒在屏障的所有執行緒都暫停，直到所有執行緒都執行的屏障為止。

## <a name="syntax"></a>語法

```
#pragma omp barrier
```

## <a name="remarks"></a>備註

`barrier`指示詞可支援無 OpenMP 子句。

如需詳細資訊，請參閱 < [2.6.3 barrier 指示詞](../../../parallel/openmp/2-6-3-barrier-directive.md)。

## <a name="example"></a>範例

如需如何使用的範例`barrier`，請參閱 <<c2> [ 主要](../../../parallel/openmp/reference/master.md)。

## <a name="see-also"></a>另請參閱

[指示詞](../../../parallel/openmp/reference/openmp-directives.md)