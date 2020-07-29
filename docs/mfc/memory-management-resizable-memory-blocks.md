---
title: 記憶體管理：可調整大小的記憶體區塊
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 308b5aa00aeb1f0e7887ad90bad79a28b361d7c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217918"
---
# <a name="memory-management-resizable-memory-blocks"></a>記憶體管理：可調整大小的記憶體區塊

「 **`new`** **`delete`** [記憶體管理：範例](memory-management-examples.md)」一文中所述的和運算子，適用于配置和解除配置固定大小的記憶體區塊和物件。 有時候，您的應用程式可能需要可調整大小的記憶體區塊。 您必須使用標準 C 執行時間程式庫函數[malloc](../c-runtime-library/reference/malloc.md)、 [realloc](../c-runtime-library/reference/realloc.md)和[free](../c-runtime-library/reference/free.md)來管理堆積上的可調整大小記憶體區塊。

> [!IMPORTANT]
> **`new`** **`delete`** 將和運算子與相同記憶體區塊上的可調整大小記憶體配置函式混用，會導致在 MFC 的 Debug 版本中有損毀的記憶體。 您不應該在使用配置的記憶體區塊上使用**realloc** **`new`** 。 同樣地，您不應該使用運算子來配置記憶體區塊， **`new`** 並使用「**免費**」加以刪除，或在使用 malloc 配置的 **`delete`** 記憶體區塊**malloc**上使用運算子。

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](memory-management-heap-allocation.md)
