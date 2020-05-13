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
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365526"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的例外狀況處理

本文介紹了 MFC 中可用的異常處理機制。 有兩種機制可用:

- C++例外,在 MFC 版本 3.0 及更高版本中提供

- MFC 異常宏,在 MFC 版本 1.0 及更高版本提供

如果要使用 MFC 編寫新應用程式,則應使用C++機制。 如果現有應用程式已廣泛使用該機制,則可以使用基於宏的機制。

您可以輕鬆轉換現有代碼以使用C++異常而不是 MFC 異常宏。 在["例外:從 MFC 異常宏轉換"](../mfc/exceptions-converting-from-mfc-exception-macros.md)一文中介紹了轉換代碼和準則的優點。

如果您已經使用 MFC 異常宏開發了應用程式,則可以在現有代碼中繼續使用這些宏,同時在新代碼中使用 C++異常。 "[例外:對版本 3.0 中異常宏的更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)"提供了執行此操作的指導原則。

> [!NOTE]
> 要在代碼中啟用C++異常處理,請選擇"在專案[屬性頁](../build/reference/property-pages-visual-cpp.md)"對話框的 C/C++ 資料夾中的代碼生成頁上啟用C++異常,或使用[/EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項。

本文章涵蓋下列主題：

- [使用例外狀況的時機](#_core_when_to_use_exceptions)

- [MFC 不支援](#_core_mfc_exception_support)

- [有關異常的進一步閱讀](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>何時使用例外

在程式執行期間調用函數時,可能會出現三類結果:正常執行、錯誤執行或異常執行。 下面將介紹每個類別。

- 正常執行

   函數可以正常執行並返回。 某些函數將結果代碼返回給調用方,指示函數的結果。 對函數嚴格定義可能的結果代碼,並代表函數的可能結果範圍。 結果代碼可以指示成功或失敗,甚至可以指示在正常期望範圍內的特定類型的故障。 例如,文件狀態函數可以返回指示該檔不存在的代碼。 請注意,不使用術語「錯誤代碼」,因為結果代碼表示許多預期結果之一。

- 錯誤執行

   調用方在將參數傳遞給函數或在不適當的上下文中調用函數時犯了一些錯誤。 這種情況會導致錯誤,並且應在程式開發期間由斷言檢測到它。 (有關斷言的詳細資訊,請參閱[C/C++斷言](/visualstudio/debugger/c-cpp-assertions)。

- 例外執行

   異常執行包括程式無法控制的情況(如記憶體不足或I/O錯誤)影響函數結果的情況。 異常情況應通過捕獲和引發異常來處理。

使用異常特別適用於異常執行。

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>MFC 不支援

無論是直接使用C++異常還是使用MFC異常宏,都將使用框架或應用程式可能引發的[Cexception類](../mfc/reference/cexception-class.md)或`CException`派生物件。

下表顯示了 MFC 提供的預定義異常。

|Exception 類別|意義|
|---------------------|-------------|
|[CMemoryException 類別](../mfc/reference/cmemoryexception-class.md)|記憶體不足|
|[CFileException 類別](../mfc/reference/cfileexception-class.md)|檔案例外|
|[CArchiveException 類別](../mfc/reference/carchiveexception-class.md)|封存化異常|
|[CNotSupportedException 類別](../mfc/reference/cnotsupportedexception-class.md)|不支援的服務要求的回應|
|[CResourceException 類別](../mfc/reference/cresourceexception-class.md)|視窗資源配置例外|
|[CDaoException 類別](../mfc/reference/cdaoexception-class.md)|資料庫例外(DAO 類別)|
|[CDBException 類別](../mfc/reference/cdbexception-class.md)|資料庫例外(ODBC 類別)|
|[COleException 類別](../mfc/reference/coleexception-class.md)|OLE 例外狀況|
|[COleDispatchException 類別](../mfc/reference/coledispatchexception-class.md)|派單(自動化)異常|
|[CUserException 類別](../mfc/reference/cuserexception-class.md)|使用消息框提醒使用者,然後引發泛型[Cexception 類的異常](../mfc/reference/cexception-class.md)|

從 3.0 版開始，MFC 使用了 C++ 例外狀況，但是仍支援舊有的例外狀況處理巨集，其形式類似 C++ 例外狀況。 雖然不建議新的程式設計使用這些巨集，但是仍然支援它們以提供回溯相容性。 在已經使用巨集的程式中，您也可以使用 C++ 例外狀況而不受限制。 在預處理期間,宏將評估 Visual C++ 版本 2.0 中C++語言的 MSVC 實現中定義的異常處理關鍵字。 在您開始使用 C++ 例外狀況時，可以保留現有的例外狀況巨集。 有關混合宏和C++異常處理以及轉換舊代碼以使用新機制的資訊,請參閱文章[「例外:使用 MFC 宏C++異常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)和[異常:從 MFC 異常宏轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。 如果您仍然使用舊版的 MFC 例外狀況巨集，它們會判斷值為 C++ 例外狀況關鍵字。 請參閱[異常:對版本 3.0 中的異常巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。 MFC 不直接支援 Windows NT 結構化異常處理程式 (SEH),如[結構化異常處理](/windows/win32/debug/structured-exception-handling)中所述。

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>關於例外的進一步閱讀

以下文章解釋使用 MFC 函式庫進行例外處理:

- [例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [例外狀況：檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)

- [例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [例外狀況：從您自己的函式擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [例外狀況：資料庫例外狀況](../mfc/exceptions-database-exceptions.md)

- [例外狀況：OLE 例外狀況](../mfc/exceptions-ole-exceptions.md)

以下文章將 MFC 異常宏與C++異常關鍵字進行比較,並解釋如何調整代碼:

- [例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [例外狀況：使用 MFC 巨集和 C++ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>另請參閱

[用於例外和錯誤處理的現代C++最佳實務](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[如何操作:建立自己的自訂異常類](https://go.microsoft.com/fwlink/p/?linkid=128045)
