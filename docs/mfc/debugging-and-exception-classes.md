---
title: "偵錯和例外狀況類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.debug
dev_langs: C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 622e6d04a567668ebfd2c737c5cdde1c2ea09b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-exception-classes"></a>偵錯和例外狀況類別
這些類別會提供偵錯動態記憶體配置的支援，以及從擲回例外狀況的函式傳遞例外狀況資訊至攔截例外狀況函式的支援。  
  
 使用類別[CDumpContext](../mfc/reference/cdumpcontext-class.md)和[CMemoryState](../mfc/reference/cmemorystate-structure.md)在開發期間協助偵錯，如中所述[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)來判斷執行階段的任何物件的類別，發行項中所述[存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)。 架構會使用 `CRuntimeClass` 動態建立特定類別的物件。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

