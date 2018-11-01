---
title: A.2 指定條件式編譯
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491217"
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