---
title: OMP_NESTED |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c90878ce96cf1639c983be899ba13eccf1f040e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376526"
---
# <a name="ompnested"></a>OMP_NESTED

指定是否巢狀平行處理原則已啟用，除非已啟用或停用巢狀平行處理原則`omp_set_nested`。

## <a name="syntax"></a>語法

```
set OMP_NESTED[=TRUE | =FALSE]
```

## <a name="remarks"></a>備註

`OMP_NESTED`環境變數可以覆寫[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)函式。

在 Visual c + + 實作的 OpenMP 標準預設值是`OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱 < [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

## <a name="example"></a>範例

下列命令`OMP_NESTED`環境變數設為 TRUE:

```
set OMP_NESTED=TRUE
```

下列命令會顯示目前的設定`OMP_NESTED`環境變數：

```
set OMP_NESTED
```

## <a name="see-also"></a>另請參閱

[環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)