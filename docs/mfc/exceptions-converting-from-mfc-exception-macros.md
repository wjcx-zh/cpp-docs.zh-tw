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
ms.openlocfilehash: 8a936a0af9927aa0dc453a93c98676a77f4ad6dc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621757"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>例外狀況：從 MFC 例外狀況巨集轉換

這是一個先進的主題。

本文說明如何轉換以 Microsoft Foundation Class 宏（ **try**、 **catch**、 **THROW**等等）撰寫的現有程式碼，以使用 c + + 例外狀況處理關鍵字**try**、 **catch**和**THROW**。 主題包括：

- [轉換優點](#_core_advantages_of_converting)

- [將具有例外狀況宏的程式碼轉換成使用 c + + 例外狀況](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>轉換的優點

您可能不需要轉換現有的程式碼，不過您應該知道 MFC 版本3.0 中的宏執行與舊版中的版本之間的差異。 這些差異和程式程式碼為的後續變更會在例外狀況中討論[：版本3.0 中例外狀況宏的變更](exceptions-changes-to-exception-macros-in-version-3-0.md)。

轉換的主要優點如下：

- 使用 c + + 例外狀況處理關鍵字的程式碼會編譯成稍微小一點。EXE 或。URLMON.DLL.

- C + + 例外狀況處理關鍵字更具彈性：它們可以處理任何可以複製之資料類型的例外狀況（**int**、 **float**、 **char**等等），而宏只會處理 `CException` 衍生自它的類別和類別的例外狀況。

宏與關鍵字的主要差異在於，使用宏「自動」的程式碼會在例外狀況超出範圍時，刪除攔截到的例外狀況。 使用關鍵字的程式碼不是，因此您必須明確地刪除攔截到的例外狀況。 如需詳細資訊，請參閱[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

另一個差異是語法。 宏和關鍵字的語法在三方面不同：

1. 宏引數和例外狀況宣告：

   **CATCH**宏調用具有下列語法：

   **CATCH （** *exception_class*， *exception_object_pointer_name* **）**

   請注意類別名稱和物件指標名稱之間的逗號。

   **Catch**關鍵字的例外狀況宣告會使用下列語法：

   **catch （** *exception_type* *exception_name* **）**

   這個例外狀況宣告語句會指出 catch 區塊所處理的例外狀況類型。

2. Catch 區塊的 Delimitation：

   使用宏時， **catch**宏（具有其引數）會開始第一個 catch 區塊;**AND_CATCH**宏會開始後續的 catch 區塊，而**END_CATCH**宏則會終止 catch 區塊的順序。

   使用關鍵字時， **catch**關鍵字（包含其例外狀況宣告）會開始每個 catch 區塊。 **END_CATCH**宏沒有對應的。catch 區塊的結尾會加上右大括弧。

3. Throw 運算式：

   宏會使用**THROW_LAST**來重新擲回目前的例外狀況。 不含引數的**throw**關鍵字具有相同的效果。

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>執行轉換

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>使用宏轉換程式碼以使用 c + + 例外狀況處理關鍵字

1. 找出所有出現的 MFC 宏**TRY**、 **CATCH**、 **AND_CATCH**、 **END_CATCH**、 **THROW**和**THROW_LAST**。

2. 取代或刪除所有出現的下列宏：

   **嘗試**（以**try**取代它）

   **Catch** （以**catch**取代）

   **AND_CATCH** （以**CATCH**取代）

   **END_CATCH** （刪除）

   **Throw** （以**throw**取代它）

   **THROW_LAST** （以**THROW**取代）

3. 修改宏引數，使其形成有效的例外狀況宣告。

   例如，

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 修改 catch 區塊中的程式碼，讓它在必要時刪除例外狀況物件。 如需詳細資訊，請參閱[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

以下是使用 MFC 例外狀況宏的例外狀況處理常式代碼範例。 請注意，因為下列範例中的程式碼使用宏，所以 `e` 會自動刪除例外狀況：

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一個範例中的程式碼使用 c + + 例外狀況關鍵字，因此必須明確地刪除例外狀況：

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

如需詳細資訊，請參閱[例外狀況：使用 MFC 宏和 c + + 例外](exceptions-using-mfc-macros-and-cpp-exceptions.md)狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)<br/>
