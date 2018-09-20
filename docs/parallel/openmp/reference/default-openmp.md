---
title: 預設值 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- default
dev_langs:
- C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea32f473d96c8f48c6628d8f71212269bd6d345
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392604"
---
# <a name="default-openmp"></a>default (OpenMP)

指定在平行區域不限範圍變數的行為。

## <a name="syntax"></a>語法

```
default(shared | none)
```

## <a name="remarks"></a>備註

`shared`這實際上是如果`default`未指定子句，表示它與所指定，會視為在平行區域中的任何變數[共用](../../../parallel/openmp/reference/shared-openmp.md)子句。 `none` 表示與未設定範圍的平行區域中使用的任何變數[私人](../../../parallel/openmp/reference/private-openmp.md)，[共用](../../../parallel/openmp/reference/shared-openmp.md)，[減少](../../../parallel/openmp/reference/reduction.md)， [firstprivate](../../../parallel/openmp/reference/firstprivate.md)，或是[lastprivate](../../../parallel/openmp/reference/lastprivate.md)子句會造成編譯器錯誤。

`default` 適用於下列指示詞：

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [區段](../../../parallel/openmp/reference/sections-openmp.md)

如需詳細資訊，請參閱 < [2.7.2.5 預設](../../../parallel/openmp/2-7-2-5-default.md)。

## <a name="example"></a>範例

請參閱[私人](../../../parallel/openmp/reference/private-openmp.md)如需使用的範例`default`。

## <a name="see-also"></a>另請參閱

[子句](../../../parallel/openmp/reference/openmp-clauses.md)