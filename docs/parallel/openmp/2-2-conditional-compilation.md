---
title: 2.2 條件式編譯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440377"
---
# <a name="22-conditional-compilation"></a>2.2 條件式編譯

_**OPENMP**巨集名稱指 OpenMP 相容實作十進位常數*yyyymm*，它會是年份和月份的已核准的規格。 這個巨集不能主旨 **#define**或是 **#undef**前置處理器指示詞。

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果廠商定義與 OpenMP 的擴充功能，它們就可以指定其他預先定義的巨集。