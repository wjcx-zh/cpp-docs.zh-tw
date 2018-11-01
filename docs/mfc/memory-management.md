---
title: 記憶體管理
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: b5b91245d08c6c4a17c9ba96a0ca4dcf19932d9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461378"
---
# <a name="memory-management"></a>記憶體管理

本文件群說明如何使用 MFC 程式庫中與記憶體管理相關的通用服務。 記憶體配置可以分成兩個主要類型：框架配置和堆積配置。

兩個配置技術之間的主要差異是框架配置通常搭配實際的記憶體區塊，而使用時堆積配置則一定會給您指向記憶體區塊的指標。 兩種配置之間的另一個主要差異是框架物件會自動刪除，而堆積物件則必須由程式設計人員明確刪除。

如需 Windows 程式中記憶體管理的非 MFC 資訊，請參閱[記憶體管理](https://msdn.microsoft.com/library/windows/desktop/aa366779)Windows SDK 中。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [框架配置](../mfc/memory-management-frame-allocation.md)

- [堆積配置](../mfc/memory-management-heap-allocation.md)

- [陣列配置記憶體](../mfc/memory-management-examples.md)

- [從堆積解除配置陣列的記憶體](../mfc/memory-management-examples.md)

- [資料結構配置記憶體](../mfc/memory-management-examples.md)

- [物件配置記憶體](../mfc/memory-management-examples.md)

- [可調整大小的記憶體區塊](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)

