---
title: 例外狀況： 使用 MFC 巨集和 c + + 例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 698d8a754716f6876f9a72a0d5043807a32d2089
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932204"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>例外狀況：使用 MFC 巨集和 C++ 例外狀況
這篇文章討論撰寫使用 MFC 例外狀況處理巨集和 c + + 例外狀況處理關鍵字的程式碼的考量。  
  
 本文涵蓋下列主題：  
  
-   [混合例外狀況關鍵字和巨集](#_core_mixing_exception_keywords_and_macros)  
  
-   [Try catch 區塊內的區塊](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> 混合例外狀況關鍵字和巨集  
 您可以混合 MFC 例外狀況巨集和 c + + 例外狀況關鍵字相同程式中。 但是您不能混合 MFC 巨集與 c + + 例外狀況關鍵字在相同的區塊，因為巨集時，刪除例外狀況物件會自動在超出範圍，而不使用例外狀況處理關鍵字的程式碼。 如需詳細資訊，請參閱文章[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 巨集和關鍵字的主要差異是當超出範圍的例外狀況時，巨集 「 自動 」 刪除攔截的例外狀況。 使用關鍵字的程式碼則否。在 catch 區塊中攔截例外狀況必須明確刪除。 混合巨集和 c + + 例外狀況關鍵字可以不刪除例外狀況物件時，會導致記憶體遺漏或兩次刪除例外狀況時堆積損毀。  
  
 下列程式碼，例如，使例外狀況指標：  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 發生問題的原因`e`執行會通過 「 內部 」 之外時，會刪除**攔截**區塊。 使用**THROW_LAST**巨集，而不是**擲回**陳述式會導致 「 外部 」**攔截**區塊來接收有效的指標：  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> Try Catch 區塊內的區塊  
 您無法從重新擲回目前例外狀況**再試一次**區塊內部**攔截**區塊。 下列範例無效：  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 如需詳細資訊，請參閱[例外狀況： 檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

