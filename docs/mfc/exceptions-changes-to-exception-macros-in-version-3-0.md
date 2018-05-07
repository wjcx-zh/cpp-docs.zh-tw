---
title: 例外狀況： 3.0 版例外狀況巨集變更 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92d1691f9a61a11dc4d9dfe7e869ccb7899746bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>例外狀況：3.0 版例外狀況巨集的變更
這是進階的主題。  
  
 在 MFC 3.0 版和更新版本中，已變更的例外狀況處理巨集使用 c + + 例外狀況。 這篇文章會告訴您這些變更如何影響使用巨集的現有程式碼的行為。  
  
 本文涵蓋下列主題：  
  
-   [例外狀況類型和 CATCH 巨集](#_core_exception_types_and_the_catch_macro)  
  
-   [重新擲回例外狀況](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> 例外狀況類型和 CATCH 巨集  
 在舊版的 MFC，**攔截**巨集使用 MFC 的執行階段類型資訊來判斷例外狀況的類型，例外狀況的類型決定，也就是說，在 catch 站台。 與 c + + 例外狀況，不過，例外狀況的類型是一律決定在擲回站台就會擲回的例外狀況物件類型。 這會導致不相容的少數情況下，不同於擲回之物件的型別擲回的物件指標的類型。  
  
 下列範例將說明這 MFC 3.0 版和舊版之間的差異的結果：  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 此程式碼的行為不同 3.0 版因為控制項永遠都會將傳遞至第一個**攔截**相符的例外狀況宣告具有區塊。 Throw 運算式的結果  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 被擲回做**CException\***，即使它建構為**CCustomException**。 **攔截**MFC 版本 2.5 和較早的使用中的巨集`CObject::IsKindOf`測試在執行階段類型。 因為運算式  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 為 true，第一個 catch 區塊攔截例外狀況。 3.0 版，實作許多例外狀況處理巨集使用 c + + 例外狀況，可擲回的第二個 catch 區塊符合`CException`。  
  
 這很類似的程式碼。 它通常會顯示當例外狀況物件傳遞至另一個函式可接受泛型**CException\*** 執行 「 預先擲回 「 處理中，且最後會擲回例外狀況。  
  
 若要解決這個問題，將擲回運算式從函式呼叫的程式碼，編譯器會產生例外狀況時的已知型別的實際發生例外狀況。  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> 重新擲回例外狀況  
 Catch 區塊不會擲回相同它攔截的例外狀況指標。  
  
 比方說，這段程式碼在較舊的版本中有效，但會有非預期的結果 3.0 版：  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 使用**擲回**中捕捉區塊會導致指標`e`遭到刪除，以便在外部 catch 站台將會收到無效的指標。 使用`THROW_LAST`重新擲回`e`。  
  
 如需詳細資訊，請參閱[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

