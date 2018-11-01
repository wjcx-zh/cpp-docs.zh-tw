---
title: 例外狀況：從 MFC 例外狀況巨集轉換
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525888"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>例外狀況：從 MFC 例外狀況巨集轉換

這是進階的主題。

這篇文章說明如何將轉換使用 Mfc 巨集撰寫的現有程式碼 —**嘗試**，**攔截**，**擲回**等等 — 若要使用 c + + 例外狀況處理關鍵字**嘗試**，**攔截**，並**擲回**。 主題包括：

- [轉換的優點](#_core_advantages_of_converting)

- [轉換程式碼以使用 c + + 例外狀況的例外狀況巨集](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> 轉換的好處

您可能不需要轉換現有的程式碼，雖然您應該注意的巨集實作 mfc 3.0 版和更早版本中的實作之間的差異。 這些差異以及後續的程式碼行為的變更會討論[例外狀況： 3.0 版例外狀況巨集變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。

將轉換的主要優點如下：

- 使用 c + + 例外狀況處理關鍵字的程式碼編譯成稍微小一點。EXE 或。DLL。

- C + + 例外狀況處理關鍵字具有更多功能： 它們能夠處理任何可複製的資料類型的例外狀況 (**int**， **float**， **char**等等)，而巨集處理的例外狀況的類別只`CException`和從它衍生的類別。

巨集和關鍵字的主要差異是當例外狀況超出範圍時使用 「 自動 」 的巨集的程式碼會刪除已攔截的例外狀況。 程式碼會使用關鍵字則否，因此您必須明確地刪除攔截的例外狀況。 如需詳細資訊，請參閱文章[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

另一個差異是語法。 巨集和關鍵字的語法不同在三個方面：

1. 巨集引數和例外狀況宣告：

   A**攔截**巨集引動過程語法如下：

   **CATCH (** *exception_class*， *exception_object_pointer_name* **)**

   請注意之間的類別名稱和物件指標名稱的逗號。

   例外狀況宣告**攔截**關鍵字會使用此語法：

   **catch (** *exception_type* *exception_name* **)**

   此例外狀況宣告陳述式表示的類型例外狀況的 catch 區塊會處理。

2. Catch 區塊的 delimitation:

   巨集，**攔截**巨集 （其引數） 開始的第一個 catch 區塊，而**AND_CATCH**巨集開始後續的 catch 區塊，而**END_CATCH**巨集結束 catch 區塊的順序。

   關鍵字，**攔截**（和其例外狀況宣告） 的關鍵字開頭的每個 catch 區塊。 沒有任何對應項目**END_CATCH**巨集; 在 catch 區塊結束其右大括號。

3. Throw 運算式：

   使用巨集**THROW_LAST**重新擲回目前例外狀況。 **擲回**關鍵字，但沒有引數，具有相同的效果。

##  <a name="_core_doing_the_conversion"></a> 執行的轉換

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>要轉換的程式碼使用 c + + 例外狀況處理關鍵字使用巨集

1. 尋找所有出現的 MFC 巨集**嘗試**，**攔截**， **AND_CATCH**， **END_CATCH**，**擲回**，並**THROW_LAST**。

2. 取代或刪除下列巨集的所有項目：

   **請嘗試**(將它取代為**試**)

   **攔截**(將它取代為**攔截**)

   **AND_CATCH** (將它取代為**攔截**)

   **END_CATCH** （刪除）

   **擲回**(將它取代為**擲回**)

   **THROW_LAST** (將它取代為**擲回**)

3. 修改巨集引數，讓它們形成有效的例外狀況宣告。

   例如，變更

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   設為

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 因此，它會刪除例外狀況物件，視需要，請修改 catch 區塊中的程式碼。 如需詳細資訊，請參閱文章[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

以下是使用 MFC 例外狀況巨集的例外狀況處理程式碼範例。 請注意，因為在下列範例中的程式碼使用巨集、 例外狀況`e`會自動刪除：

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一個範例中的程式碼使用 c + + 例外狀況關鍵字，因此必須明確刪除例外狀況：

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 使用 MFC 巨集和 c + + 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)<br/>
