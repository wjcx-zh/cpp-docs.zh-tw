---
title: OMP_DYNAMIC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a2a4d660057ab83da39add7fd32bcff3e6d90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392134"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC

指定執行階段的 OpenMP 是否可調整的平行區域中的執行緒數目。

## <a name="syntax"></a>語法

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

## <a name="remarks"></a>備註

`OMP_DYNAMIC`環境變數可以覆寫[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)函式。

在 Visual c + + 實作的 OpenMP 標準預設值是`OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱 < [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

## <a name="example"></a>範例

下列命令`OMP_DYNAMIC`環境變數設為 TRUE:

```
set OMP_DYNAMIC=TRUE
```

下列命令會顯示目前的設定`OMP_DYNAMIC`環境變數：

```
set OMP_DYNAMIC
```

## <a name="see-also"></a>另請參閱

[環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)