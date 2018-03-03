---
title: "例外狀況： 建構函式中例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc17821e2dd358a4b8f596492fa46c2b7412feed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-exceptions-in-constructors"></a>例外狀況：建構函式中的例外狀況
當擲回例外狀況的建構函式中，清除任何物件，而且記憶體配置您所做之前擲回例外狀況，如所述[例外狀況： 從您的函式擲回的例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。  
  
 如果建構函式擲回例外狀況，表示呼叫建構函式時已經配置物件本身的記憶體。 因此，在擲回例外狀況之後，編譯器將會自動解除配置物件所佔用的記憶體。  
  
 如需詳細資訊，請參閱[例外狀況： 例外狀況時釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md)。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

