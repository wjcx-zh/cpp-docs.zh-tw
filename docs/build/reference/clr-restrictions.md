---
title: /clr 限制
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 641e83cb85b6282e8c4c82dfed8c4b44fc4a7e8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223898"
---
# <a name="clr-restrictions"></a>/clr 限制

請注意下列有關 **/clr** 的使用限制：

- 在結構化例外狀況處理常式中，使用 **/clr** 進行編譯時，`_alloca` 的使用上會有些限制。 如需詳細資訊，請參閱 [_alloca](../../c-runtime-library/reference/alloca.md)。

- 執行階段錯誤檢查不能與 **/clr** 搭配使用。 如需詳細資訊，請參閱[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

- 使用 **/clr** 來編譯只使用標準 C++ 語法的程式時，應套用下列指導方針來使用內嵌組件：

  - 對於假設具有原生堆疊配置、目前函式外呼叫慣例或其他電腦相關低階資訊認知的內嵌組件程式碼，如果該認知套用到受控函式的堆疊框架，則內嵌組件程式碼可能會失敗。 包含內嵌組件程式碼的函式會產生為非受控函式，就如同將這些函式放在不是 **/clr** 編譯的個別模組中一樣。

  - 若內嵌組件程式碼位在傳遞複製建構函式參數的函式中，則不予以支援。

- 您無法從使用 **/clr** 編譯的程式中呼叫 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)。

- 在 /clr 底下，[naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) 修飾詞會遭到忽略。

- 由 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) 設定的翻譯工具函式，將只影響非受控程式碼中的攔截。 如需詳細資訊，請參閱[例外狀況處理](../../extensions/exception-handling-cpp-component-extensions.md)。

- **/clr** 底下不允許函式指標的比較。

- **/clr** 底下不允許使用原型不完整的函式。

- 下列編譯器選項不支援使用 **/clr**：

  - **/EHsc** 和 **/EHs** (**/clr** 意指 **/EHa** (請參閱 [/EH (例外狀況處理模型)](eh-exception-handling-model.md))

  - **/fp:strict** 和 **/fp:except** (請參閱 [/fp (指定浮點行為)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- 不支援 `_STATIC_CPPLIB` 前置處理器定義 (`/D_STATIC_CPPLIB`) 和 **/clr** 編譯器選項的組合。 這是因為該定義會導致您的應用程式與靜態多執行緒 C++ 標準程式庫連結，而這是不受支援的。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](md-mt-ld-use-run-time-library.md) 主題。

- 搭配使用 **/Zi**和 **/clr** 會對效能產生影響。 如需詳細資訊，請參閱 [/Zi](z7-zi-zi-debug-information-format.md)。

- 將寬字元傳遞至 .NET Framework 輸出常式，而不需要同時指定[/zc： wchar_t](zc-wchar-t-wchar-t-is-native-type.md)或不將字元轉換為， **`__wchar_t`** 會導致輸出顯示為 `unsigned short int` 。 例如：

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- 使用 **/clr** 進行編譯時，[/GS](gs-buffer-security-check.md) 會遭到忽略，除非您的函式在`#pragma` [非受控的](../../preprocessor/managed-unmanaged.md) 之下，或函式必須編譯為原生狀態，在此情況下，編譯器會產生警告 C4793 (預設為關閉)。

- 請參閱 [/ENTRY](entry-entry-point-symbol.md)，以了解受控應用程式的函式簽章需求。

- 使用 **/openmp** 和 **/clr** 編譯的應用程式只能在單一 AppDomain 程序中執行。  如需詳細資訊，請參閱 [/openmp (啟用 OpenMP 2.0 支援)](openmp-enable-openmp-2-0-support.md)。

- 若函式接受可變數目的引數 (varargs)，該函式會產生為原生函式。 變數引數位置中的任何受控資料類型都會封送處理為原生類型。 請注意，<xref:System.String?displayProperty=fullName> 類型實際上是寬字元字串，但會將其封送處理為單一位元組的字元字串。 因此，如果 printf 指定名稱為 %S (wchar_t*)，則會封送處理為 %s 字串。

- 使用 va_arg 巨集時，您可能會在使用 **/clr:pure** 進行編譯時，收到非預期的結果。 如需詳細資訊，請參閱 [va_arg、va_copy、va_end、va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。 必須是「純」或「安全」程式碼才能移植到 C#。

- 您不能從受控程式碼呼叫藉由巡歷堆疊以取得參數資訊 (函式引數) 的任何函式，P/Invoke 層會導致資訊落在堆疊的更下方。  比方說，請勿使用 **/clr** 來編譯 proxy/stub。

- 函式會盡可能編譯為受控程式碼，但並非所有 C++ 建構都可以轉譯成受控程式碼。  這會以每個函式為基礎來做出決定。 如果函式的任何部分無法轉換成受控程式碼，則整個函式將會轉換成機器碼。 下列情況會阻止編譯器產生受控程式碼。

  - 編譯器產生的 Thunk 或協助程式函式。 透過函式指標進行的任何函式呼叫 (包括虛擬函式呼叫) 都會產生原生 Thunk。

  - 呼叫 `setjmp` 或 `longjmp` 的函式。

  - 使用特定內建常式來直接操作機器資源的函式。 例如，使用 `__enable` 和 `__disable`、`_ReturnAddress` 和 `_AddressOfReturnAddress` 或多媒體內建項目，都會導致機器碼。

  - 遵循 `#pragma unmanaged` 指示詞的函式。 (請注意，反之則使用 `#pragma managed`。)

  - 包含對齊類型參考的函式，這些類型是指使用 `__declspec(align(...))` 宣告的類型。

## <a name="see-also"></a>另請參閱

- [/clr （Common Language Runtime 編譯）](clr-common-language-runtime-compilation.md)
