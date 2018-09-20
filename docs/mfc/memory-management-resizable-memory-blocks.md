---
title: 記憶體管理： 可調整大小的記憶體區塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92582e4255c88b9cc78368a635b27772f2e51a30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443900"
---
# <a name="memory-management-resizable-memory-blocks"></a>記憶體管理：可調整大小的記憶體區塊

**新**並**刪除**運算子，本文所述[記憶體管理： 範例](../mfc/memory-management-examples.md)，適合用於配置和解除配置的固定大小的記憶體區塊和物件。 有時候，您的應用程式可能需要可調整大小的記憶體區塊。 您必須使用標準的 C 執行階段程式庫函式[malloc](../c-runtime-library/reference/malloc.md)， [realloc](../c-runtime-library/reference/realloc.md)，並[免費](../c-runtime-library/reference/free.md)來管理堆積上的可調整的記憶體區塊。

> [!IMPORTANT]
>  混合**新**並**刪除**運算子與可調整大小的記憶體配置上的函式相同的記憶體區塊將會導致損毀的記憶體，在 MFC 的偵錯版本。 您不應該使用**realloc**上的記憶體區塊，以配置**新**。 同樣地，您不應該配置的記憶體區塊**新**運算子並將它與刪除**免費**，或使用**刪除**所配置的記憶體區塊的運算子**malloc**。

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)

