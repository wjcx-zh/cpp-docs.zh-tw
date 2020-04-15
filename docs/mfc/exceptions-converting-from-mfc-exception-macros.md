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
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372021"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>例外狀況：從 MFC 例外狀況巨集轉換

這是一個高級主題。

本文介紹如何轉換使用 Microsoft 基礎類巨集編寫的現有代碼 - **TRY、CATCH、THROW**等 — 使用C++異常處理關鍵**CATCH****THROW**字**嘗試**、**捕獲**和**引發**。 主題包括：

- [轉換優勢](#_core_advantages_of_converting)

- [將具有異常巨集的代碼轉換為使用C++例外](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>轉換的優點

您可能不需要轉換現有代碼,儘管您應該瞭解 MFC 版本 3.0 中的宏實現在早期版本中的實現之間的差異。 這些差異和代碼行為的後續更改在[「例外:對版本 3.0 中的異常宏的更改」中](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)進行了討論。

轉換的主要優點是:

- 使用C++異常處理關鍵字的代碼編譯為稍小一些。EXE 或 。Dll。

- C++異常處理關鍵字更通用:它們可以處理任何數據類型的異常 **(int、float、char**等),而宏**float**僅處理**char**派生`CException`自 它的類 和類的異常。

宏和關鍵字之間的主要區別是,使用宏"自動"的代碼在異常超出範圍時刪除捕獲的異常。 使用關鍵字的代碼不會,因此您必須顯式刪除捕獲的異常。 有關詳細資訊,請參閱文章[「例外:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)」。

另一個區別是語法。 宏和關鍵字的語法在三個方面有所不同:

1. 巨集參數與例外聲明:

   **CATCH**宏調用具有以下語法:

   **CATCH(exception_class,exception_object_pointer_name)** *exception_class* *exception_object_pointer_name* **)**

   請注意類名稱和物件指標名稱之間的逗號。

   **catch**關鍵字的例外宣告使用此語法:

   **漁獲***exception_type**(exception_typeexception_name)* **)**

   此異常聲明語句指示 catch 塊句柄的異常類型。

2. 漁獲物塊的劃分:

   使用宏時 **,CATCH**宏(具有其參數)開始第一個 catch 塊;使用宏宏,則使用宏宏(具有其參數)開始第一個 catch 塊。**AND_CATCH**宏開始後續 catch 塊 **,END_CATCH**宏終止 catch 塊的順序。

   使用關鍵字時 **,catch**關鍵字(其異常聲明)將啟動每個 catch 塊。 END_CATCH**宏沒有**對應點;catch 塊以其右大括弧結束。

3. 引發表示式:

   宏使用**THROW_LAST**重新引發當前異常。 **沒有參數的引發**關鍵字具有相同的效果。

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>執行轉換

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>使用巨集轉換碼以使用C++異常處理關鍵字

1. 找到 MFC**TRY**宏 TRY、CATCH、AND_CATCH、END_CATCH、THROW**END_CATCH**和**THROW** **CATCH** **AND_CATCH** **THROW_LAST**的所有匹配項。

2. 取代或移除以下巨集的配對項:

   **TRY(** 使用 **"**

   **CATCH(** 用**漁獲取代**)

   **AND_CATCH(** 用**漁獲取代**)

   **END_CATCH(** 移除 )

   **THROW(** 用**投擲**取代 )

   **THROW_LAST(** 用**投擲**取代 )

3. 修改宏參數,以便它們形成有效的異常聲明。

   例如，

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 修改 catch 塊中的代碼,以便根據需要刪除異常物件。 有關詳細資訊,請參閱文章[「例外:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)」。

下面是使用 MFC 異常宏的異常處理代碼的範例。 請注意,由於以下範例中的代碼使用巨集,因此將自動刪除`e`異常 :

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一個範例中的代碼使用C++異常關鍵字,因此必須顯式刪除異常:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

有關詳細資訊,請參閱[異常:使用 MFC 宏和C++異常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)<br/>
