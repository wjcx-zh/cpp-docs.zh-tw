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
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364780"
---
# <a name="memory-management-resizable-memory-blocks"></a>記憶體管理：可調整大小的記憶體區塊

新的**new****和刪除**運算符,在文章[記憶體管理:示例](../mfc/memory-management-examples.md)中介紹,非常適合分配和釋放固定大小的記憶體塊和物件。 有時,應用程式可能需要可調整大小的記憶體區塊。 您必須使用標準的 C 執行時庫函數[malloc、realloc](../c-runtime-library/reference/malloc.md)和[免費](../c-runtime-library/reference/free.md)來管理堆上可調整[realloc](../c-runtime-library/reference/realloc.md)大小的記憶體區塊。

> [!IMPORTANT]
> 將**新的**運算子和**刪除**運算元與同一記憶體區塊上的可調整大小的記憶體分配函數混合將導致 MFC 的調試版本中的記憶體損壞。 不應在使用**new**分配的記憶體區塊上使用**realloc。** 同樣,您不應使用**新**運算符分配記憶體區塊,並使用**空閒**的刪除記憶體區塊,或使用使用**malloc**分配的記憶體區塊上的**刪除**運算符號。

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)
