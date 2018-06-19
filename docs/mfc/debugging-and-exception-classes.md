---
title: 偵錯和例外狀況類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9adf6a585771336de9fb33abbebdd6bab97383ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341757"
---
# <a name="debugging-and-exception-classes"></a>偵錯和例外狀況類別
這些類別會提供偵錯動態記憶體配置的支援，以及從擲回例外狀況的函式傳遞例外狀況資訊至攔截例外狀況函式的支援。  
  
 使用類別[CDumpContext](../mfc/reference/cdumpcontext-class.md)和[CMemoryState](../mfc/reference/cmemorystate-structure.md)在開發期間協助偵錯，如中所述[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)來判斷執行階段的任何物件的類別，發行項中所述[存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)。 架構會使用 `CRuntimeClass` 動態建立特定類別的物件。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

