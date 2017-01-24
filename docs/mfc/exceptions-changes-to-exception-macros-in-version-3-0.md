---
title: "例外狀況：3.0 版例外狀況巨集的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, 升級考量"
  - "CATCH 巨集"
  - "例外狀況, 已變更的內容"
  - "THROW_LAST 巨集"
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況：3.0 版例外狀況巨集的變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這是進階主題。  
  
 在 MFC 3.0 版和更新版本中，例外處理巨集已改變為使用 C\+\+ 例外狀況。  本文說明這些變更如何影響使用巨集現有程式碼的行為。  
  
 本章節涵蓋下列主題：  
  
-   [例外狀況型別和 Catch 巨集](#_core_exception_types_and_the_catch_macro)  
  
-   [重新擲回例外狀況](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> 例外狀況型別和 Catch 巨集  
 在 MFC 舊版，**CATCH** 巨集使用 MFC 的執行階段型別資訊判斷例外狀況型別；也就是說，例外狀況型別是在 catch 網站決定的。  然而，有了 C\+\+ 例外狀況，例外狀況型別永遠是在擲回網站判斷，並且是根據所擲回的例外狀況物件的型別。  這在一些罕見情況會造成不相容，像是指標對被擲回物件的型別與被擲回物件的型別不同。  
  
 下列範例說明在 MFC 3.0 版和舊版之間，這個差異的後果：  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 這段程式碼的行為和在版本 3.0 中不同，因為控制項會傳遞具有相符例外狀況宣告的 **catch** 區塊。  擲回運算式的結果。  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 被擲回做為 **CException\***，即使它是建構為 **CCustomException**。  在 MFC 2.5 版和更早的版本中，**CATCH** 巨集使用 `CObject::IsKindOf` 在執行階段測試型別。  因為運算式  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 為 true 時，第一個 catch 區塊攔截例外狀況。  3.0 版使用 C\+\+ 例外狀況實作許多例外狀況處理巨集，第二個 catch 區塊符合擲回的 `CException`。  
  
 像這樣的程式碼並不常見。  這通常會發生在例外狀況物件傳遞給接受泛型 **CException\*** 的另一個函式，執行「處理之前擲回」，並最後擲回給例外狀況。  
  
 若要解決此問題，請將擲回運算式從函式移動至呼叫程式碼，並在產生例外狀況時擲回這個編譯器知道的實際型別的例外狀況。  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> 重新擲回例外狀況  
 Catch 區塊不能擲回與它攔截的相同的例外狀況指標。  
  
 例如，這個程式碼在舊版本有效，但是在版本 3.0 會有非預期的結果：  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 在 catch 區塊使用 **THROW** 蕙造成指標 `e` 被刪除，因此外部 catch 網站會收到無效的指標。  使用 `THROW_LAST` 重新擲回 `e`。  
  
 如需詳細資訊，請參閱 [例外狀況：攔截和刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)