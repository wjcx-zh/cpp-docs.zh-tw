---
title: lastprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7124e51b604a55d049be13d3bbcccc4e5810ca67
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412830"
---
# <a name="lastprivate"></a>lastprivate

指定封入內容變數的版本，設定等於私用版本的任何執行緒執行的最後一個反覆項目 （for 迴圈建構） 或最後一節 （#pragma 區段）。

## <a name="syntax"></a>語法

```
lastprivate(var)
```

### <a name="parameters"></a>參數

*var*<br/>
此變數會設為等於執行緒私用版本執行的最後一個反覆項目 （for 迴圈建構） 或最後一節 （#pragma 區段）。

## <a name="remarks"></a>備註

`lastprivate` 適用於下列指示詞：

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [區段](../../../parallel/openmp/reference/sections-openmp.md)

如需詳細資訊，請參閱 < [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。

## <a name="example"></a>範例

請參閱[排程](../../../parallel/openmp/reference/schedule.md)如需使用的範例`lastprivate`子句。

## <a name="see-also"></a>另請參閱

[子句](../../../parallel/openmp/reference/openmp-clauses.md)