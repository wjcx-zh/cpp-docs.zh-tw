---
title: /clr 限制
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777814"
---
# <a name="clr-restrictions"></a>/clr 限制

請注意下列限制的用法 **/clr**:

- 在結構化例外狀況處理常式中，有使用限制`_alloca`進行編譯時 **/clr**。 如需詳細資訊，請參閱 < [_alloca](../../c-runtime-library/reference/alloca.md)。

- 使用執行階段錯誤檢查不能搭配 **/clr**。 如需詳細資訊，請參閱[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

- 當 **/clr**是用來編譯程式，只會使用標準 c + + 語法，下列指導方針適用於使用內嵌組譯碼：

  - 假設您已經在原生堆疊配置的知識的內嵌組譯碼，呼叫目前函式或其他低階電腦的相關資訊之外的慣例可能會失敗如果知識套用至 managed 函式之堆疊框架。 在如同屍體會放置在個別的模組，而不需要編譯成 unmanaged 函式，產生包含內嵌組譯碼的函式 **/clr**。

  - 不支援在複製建構函式參數傳遞的函式的內嵌組譯碼。

- [Vprintf 函式](../../c-runtime-library/vprintf-functions.md)不能從編譯的程式呼叫 **/clr**。

- [Naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md)修飾詞會忽略在 /clr 下。

- 設定轉譯器函式[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)會影響 unmanaged 程式碼中的攔截。 請參閱[例外狀況處理](../../extensions/exception-handling-cpp-component-extensions.md)如需詳細資訊。

- 下，不允許函式指標的比較 **/clr**。

- 下，不允許使用不完全原型的函式 **/clr**。

- 不支援下列編譯器選項 **/clr**:

  - **/ /Ehsc**並 **/EHs** (**/clr**意指 **/EHa** (請參閱[/EH （例外狀況處理模型）](eh-exception-handling-model.md))

  - **/fp: strict**並 **/fp： 除了**(請參閱[/fp （指定浮點行為）](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- 組合`_STATIC_CPPLIB`前置處理器定義 (`/D_STATIC_CPPLIB`) 和 **/clr**編譯器選項不支援。 這是因為定義會導致您的應用程式連結到靜態多執行緒 c + + 標準程式庫，不受支援。 如需詳細資訊，請參閱 < [/MD、 /MT、 /LD （使用執行階段程式庫）](md-mt-ld-use-run-time-library.md)主題。

- 使用時 **/Zi**具有 **/clr**，對效能的影響。 如需詳細資訊，請參閱 < [/Zi](z7-zi-zi-debug-information-format.md)。

- 將寬字元傳遞至.NET Framework 但沒有同時指定輸出常式[/zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md)或不含轉換的字元`__wchar_t`會顯示為輸出`unsigned short int`。 例如: 

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md)進行編譯時，會忽略 **/clr**，除非您的函式則位於`#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md)或必須以原生編譯函式，在此情況下，編譯器會產生警告 C4793，預設為關閉。

- 請參閱[/ENTRY](entry-entry-point-symbol.md)的受管理的應用程式的函式簽章需求。

- 應用程式編譯 **/openmp**並 **/clr**只能在單一 appdomain 程序中執行。  請參閱[/openmp （啟用 OpenMP 2.0 支援）](openmp-enable-openmp-2-0-support.md)如需詳細資訊。

- 接受可變數目的引數 (varargs) 數的函式就會產生做為原生函式。 變數引數位置中的任何 managed 的資料類型會封送處理成原生類型。 請注意，<xref:System.String?displayProperty=fullName>類型實際上的寬字元字串，但是它們會封送處理至單一位元組字元字串。 因此如果 printf 規範 %S （wchar_t *），它會封送處理為 %s 字串改為。

- 當使用 va_arg 巨集，您可能會收到非預期的結果進行編譯時 **/clr: pure**。 如需詳細資訊，請參閱 < [va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。 必須是 「 純 」 或 「 安全 」 的程式碼才能移植到C#。

- 您不應該呼叫，從 managed 程式碼，以便取得參數資訊 （函式引數），堆疊查核行程的任何函式P/Invoke 層會導致要在 stack 該資訊。  比方說，不會編譯使用的 proxy/stub **/clr**。

- 函式會編譯為 managed 程式碼，可能的話，但並非所有的 c + + 建構可以轉譯成 managed 程式碼。  做出此判斷函式的函式為基礎。 如果函式的任何部分無法轉換成 managed 程式碼中，整個函式將會轉換至原生程式碼。 下列情況下可防止編譯器產生的 managed 程式碼。

  - 編譯器產生的 thunk 或 helper 函式。 透過函式指標，包括虛擬函式呼叫的任何函式呼叫會產生原生的 thunk。

  - 函式會呼叫該`setjmp`或`longjmp`。

  - 使用特定內建常式來直接操作 機器資源的函式。 例如，使用`__enable`並`__disable`，`_ReturnAddress`和`_AddressOfReturnAddress`，或多媒體的內建函式會在原生程式碼中的所有結果。

  - 函式的`#pragma unmanaged`指示詞。 (請注意，反向， `#pragma managed`，也支援。)

  - 包含參考的函式對齊類型，也就是使用宣告型別`__declspec(align(...))`。

## <a name="see-also"></a>另請參閱

- [/clr (通用語言執行平台編譯)](clr-common-language-runtime-compilation.md)
