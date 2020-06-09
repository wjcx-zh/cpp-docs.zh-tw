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
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626272"
---
# <a name="memory-management-resizable-memory-blocks"></a>記憶體管理：可調整大小的記憶體區塊

「[記憶體管理：範例](memory-management-examples.md)」一文中所述的**new**和**delete**運算子，適用于配置和解除配置固定大小的記憶體區塊和物件。 有時候，您的應用程式可能需要可調整大小的記憶體區塊。 您必須使用標準 C 執行時間程式庫函數[malloc](../c-runtime-library/reference/malloc.md)、 [realloc](../c-runtime-library/reference/realloc.md)和[free](../c-runtime-library/reference/free.md)來管理堆積上的可調整大小記憶體區塊。

> [!IMPORTANT]
> 將**新**的和**delete**運算子與相同記憶體區塊上的可調整大小記憶體配置函式混合，會導致在 MFC 的 Debug 版本中出現損毀的記憶體。 您不應該在使用**new**所配置的記憶體區塊上使用**realloc** 。 同樣地，您不應該使用**new**運算子來配置記憶體區塊，並使用**free**刪除它，或在使用**malloc**配置的記憶體區塊上使用**delete**運算子。

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](memory-management-heap-allocation.md)
