---
title: MFC 中的例外狀況處理
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 7d1be30edec598135eed2a74fca87f1e5444f55d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246736"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的例外狀況處理

本文說明 MFC 中可用的例外狀況處理機制。 有兩種機制可供使用：

- C++MFC 版本3.0 和更新版本中可用的例外狀況

- Mfc 例外狀況宏（可在 MFC 版本1.0 和更新版本中取得）

如果您要使用 MFC 撰寫新的應用程式，您應該使用C++此機制。 如果您現有的應用程式已廣泛使用該機制，您可以使用以宏為基礎的機制。

您可以輕鬆地轉換現有的程式C++代碼，以使用例外狀況，而不是 MFC 例外狀況宏。 轉換程式碼和方針以進行這項作業的優點，請參閱[例外狀況：從 MFC 例外狀況宏轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)一文。

如果您已經使用 MFC 例外狀況宏開發應用程式，您可以繼續在現有的程式碼中使用這些宏，同時C++在新的程式碼中使用例外狀況。 發行[項例外狀況：版本3.0 中例外狀況宏的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)提供執行此作業的指導方針。

> [!NOTE]
>  若要C++在程式碼中啟用例外狀況處理C++ ，請在專案 [[屬性頁](../build/reference/property-pages-visual-cpp.md)] 對話方塊的C++ [C/資料夾] 中，選取 [程式碼產生] 頁面上的 [啟用例外狀況]，或使用[/ehsc](../build/reference/eh-exception-handling-model.md)編譯器選項。

本文涵蓋下列主題：

- [使用例外狀況的時機](#_core_when_to_use_exceptions)

- [MFC 例外狀況支援](#_core_mfc_exception_support)

- [進一步閱讀例外狀況](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a>使用例外狀況的時機

在程式執行期間呼叫函式時，可能會發生三種類別的結果：一般執行、錯誤執行或異常執行。 以下說明每個類別。

- 正常執行

   函式可能會正常執行並傳回。 有些函式會將結果碼傳回給呼叫端，以指出函數的結果。 函式會嚴格定義可能的結果碼，並代表函數的可能結果範圍。 結果程式碼可能表示成功或失敗，或甚至會指出在正常範圍內的特定失敗類型。 例如，檔案狀態函式可以傳回表示檔案不存在的程式碼。 請注意，「錯誤碼」一詞不會使用，因為結果程式碼代表許多預期結果的其中一個。

- 錯誤的執行

   呼叫端在將引數傳遞給函式或在不適當的內容中呼叫函數時，會犯一些錯誤。 這種情況會導致錯誤，而且應該在程式開發期間偵測到判斷提示。 （如需判斷提示的詳細資訊，請參閱[C/C++判斷](/visualstudio/debugger/c-cpp-assertions)提示）。

- 異常執行

   異常執行包含程式控制項外的條件（例如低記憶體或 i/o 錯誤）會影響函數的結果。 異常情況應該藉由攔截和擲回例外狀況來處理。

使用例外狀況特別適合用來執行異常。

##  <a name="_core_mfc_exception_support"></a>MFC 例外狀況支援

不論您是直接C++使用例外狀況，還是使用 MFC 例外狀況宏，您將會使用[CException 類別](../mfc/reference/cexception-class.md)或可能由架構或應用程式擲回的 `CException`衍生物件。

下表顯示 MFC 所提供的預先定義例外狀況。

|Exception 類別|意義|
|---------------------|-------------|
|[CMemoryException 類別](../mfc/reference/cmemoryexception-class.md)|記憶體不足|
|[CFileException 類別](../mfc/reference/cfileexception-class.md)|檔案例外狀況|
|[CArchiveException 類別](../mfc/reference/carchiveexception-class.md)|封存/序列化例外狀況|
|[CNotSupportedException 類別](../mfc/reference/cnotsupportedexception-class.md)|針對不支援之服務的要求回應|
|[CResourceException 類別](../mfc/reference/cresourceexception-class.md)|Windows 資源配置例外狀況|
|[CDaoException 類別](../mfc/reference/cdaoexception-class.md)|資料庫例外狀況（DAO 類別）|
|[CDBException 類別](../mfc/reference/cdbexception-class.md)|資料庫例外狀況（ODBC 類別）|
|[COleException 類別](../mfc/reference/coleexception-class.md)|OLE 例外狀況|
|[COleDispatchException 類別](../mfc/reference/coledispatchexception-class.md)|分派（自動化）例外狀況|
|[CUserException 類別](../mfc/reference/cuserexception-class.md)|例外狀況，會使用訊息方塊來警示使用者，然後擲回泛型[CException 類別](../mfc/reference/cexception-class.md)|

從 3.0 版開始，MFC 使用了 C++ 例外狀況，但是仍支援舊有的例外狀況處理巨集，其形式類似 C++ 例外狀況。 雖然不建議新的程式設計使用這些巨集，但是仍然支援它們以提供回溯相容性。 在已經使用巨集的程式中，您也可以使用 C++ 例外狀況而不受限制。 在前置處理期間，宏會評估為 Visual C++ C++ 2.0 版的 MSVC 執行語言所定義的例外狀況處理關鍵字。 在您開始使用 C++ 例外狀況時，可以保留現有的例外狀況巨集。 如需混合宏和C++例外狀況處理，以及轉換舊程式碼以使用新機制的詳細資訊，請參閱例外狀況[：使用C++ mfc 宏和例外](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)狀況和[例外狀況：從 MFC 例外狀況宏轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。 如果您仍然使用舊版的 MFC 例外狀況巨集，它們會判斷值為 C++ 例外狀況關鍵字。 請參閱[例外狀況：版本3.0 中例外狀況宏的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。 MFC 不直接支援 Windows NT 結構化例外狀況處理常式（SEH），如[結構化例外狀況處理](/windows/win32/debug/structured-exception-handling)中所述。

##  <a name="_core_further_reading_about_exceptions"></a>進一步閱讀例外狀況

下列文章說明如何使用 MFC 程式庫進行例外狀況處理：

- [例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [例外狀況：檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)

- [例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [例外狀況：從您自己的函式擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [例外狀況：資料庫例外狀況](../mfc/exceptions-database-exceptions.md)

- [例外狀況：OLE 例外狀況](../mfc/exceptions-ole-exceptions.md)

下列文章會比較 MFC 例外狀況宏與C++例外狀況關鍵字，並說明如何調整您的程式碼：

- [例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [例外狀況：使用 MFC 巨集和 C++ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>另請參閱

[例外C++狀況和錯誤處理的現代化最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[如何：建立自己的自訂例外狀況類別](https://go.microsoft.com/fwlink/p/?linkid=128045)
