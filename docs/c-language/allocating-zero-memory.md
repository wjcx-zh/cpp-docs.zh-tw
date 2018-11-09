---
title: 配置零記憶體
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: c7d5f307a38fff938c94cf2e1660cec99262a10a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447303"
---
# <a name="allocating-zero-memory"></a>配置零記憶體

**ANSI 4.10.3** `calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為

`calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)