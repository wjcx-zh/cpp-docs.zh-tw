---
title: A.2 指定條件式編譯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d8b0f3df67313dbf03d40077a551fe64930199d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393694"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2 指定條件式編譯

下列範例說明使用使用 OpenMP 巨集的條件式編譯`_OPENMP`([2.2 節](../../parallel/openmp/2-2-conditional-compilation.md)上第 8 頁)。 使用 /openmp 編譯`_OPENMP`會變成已定義巨集。

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

已定義的前置處理器運算子可讓測試在單一的指示詞中的多個巨集。

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```