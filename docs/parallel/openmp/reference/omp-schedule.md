---
title: OMP_SCHEDULE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 507067be30db019536ef222a62335244eabfaada
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413857"
---
# <a name="ompschedule"></a>OMP_SCHEDULE

修改的行為[排程](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。

## <a name="syntax"></a>語法

```
set OMP_SCHEDULE[=type[,size]]
```

## <a name="arguments"></a>引數

*size*<br/>
（選擇性）指定反覆項目的大小。 `size` 必須是正整數。 預設值為 1，除非`type`是靜態的。 不是有效的 when`type`是`runtime`。

*type*<br/>
排程的類型：

- `dynamic`

- `guided`

- `runtime`

- `static`

## <a name="remarks"></a>備註

在 Visual c + + 實作的 OpenMP 標準預設值是`OMP_SCHEDULE=static,0`。

如需詳細資訊，請參閱 < [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

## <a name="example"></a>範例

下列命令**OMP_SCHEDULE**環境變數：

```
set OMP_SCHEDULE="guided,2"
```

下列命令會顯示目前的設定**OMP_SCHEDULE**環境變數：

```
set OMP_SCHEDULE
```

## <a name="see-also"></a>另請參閱

[環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)