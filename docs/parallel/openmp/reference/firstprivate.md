---
title: firstprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d070b8de3cf0382447c3b8e756140892dcd85edc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387116"
---
# <a name="firstprivate"></a>firstprivate

指定每個執行緒都應該有自己的執行個體的變數，並以變數的值，應該先初始化變數，因為它存在於之前平行建構。

## <a name="syntax"></a>語法

```
firstprivate(var)
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`var`|個執行個體中每個執行緒，變數會初始化變數的值，因為它存在於之前平行建構。 如果指定多個變數，請以逗號分隔變數名稱。|

## <a name="remarks"></a>備註

## <a name="remarks"></a>備註

`firstprivate` 適用於下列指示詞：

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [區段](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

如需詳細資訊，請參閱 < [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。

## <a name="example"></a>範例

如需使用的範例`firstprivate`，請參閱中的範例[私人](../../../parallel/openmp/reference/private-openmp.md)。

## <a name="see-also"></a>另請參閱

[子句](../../../parallel/openmp/reference/openmp-clauses.md)