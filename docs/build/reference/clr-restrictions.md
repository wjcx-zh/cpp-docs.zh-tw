---
title: -clr 限制 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 697e2a50e8c63928a52bd1d960dcdefad0fe87bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="clr-restrictions"></a>/clr 限制
請注意下列限制使用 **/clr**:  
  
-   在結構化例外狀況處理常式中，有一些限制使用`_alloca`編譯時 **/clr**。 如需詳細資訊，請參閱[_alloca](../../c-runtime-library/reference/alloca.md)。  
  
-   不具有有效的執行階段錯誤檢查使用 **/clr**。 如需詳細資訊，請參閱[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。  
  
-   當 **/clr**是用來編譯只會使用標準 c + + 語法的程式，下列指導方針適用於使用內嵌組譯碼：  
  
    -   內嵌組譯碼假設您的原生堆疊配置的知識，呼叫慣例外目前的函式或其他低階電腦的相關資訊可能會失敗如果知識套用至 managed 函式之堆疊框架。 包含內嵌組譯碼的函式會產生為 unmanaged 函式，如同它們被放在個別的模組，將不會編譯 **/clr**。  
  
    -   不支援內嵌組譯程式碼將複製建構函式參數傳遞的函式中。  
  
-   [Vprintf 函式](../../c-runtime-library/vprintf-functions.md)無法從編譯的程式呼叫 **/clr**。  
  
-   [Naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md)在 /clr 下忽略修飾詞。  
  
-   翻譯工具函式來設定[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)會影響只攔截 unmanaged 程式碼中的。 請參閱[例外狀況處理](../../windows/exception-handling-cpp-component-extensions.md)如需詳細資訊。  
  
-   在不允許函式指標的比較 **/clr**。  
  
-   在不允許使用不完全原型的函式 **/clr**。  
  
-   不支援下列編譯器選項 **/clr**:  
  
    -   **/ /Ehsc**和 **/EHs** (**/clr**意味著 **/EHa** (請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md))  
  
    -   **/fp: strict**和 **/fp： 除了**(請參閱[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md))  
  
    -   [/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **/ZI**  
  
-   組合`_STATIC_CPPLIB`前置處理器定義 (`/D_STATIC_CPPLIB`) 和 **/clr**編譯器選項不支援。 這是，因為定義可能會導致您的應用程式連結到靜態多執行緒 c + + 標準程式庫，不支援。 如需詳細資訊，請參閱[/MD、 /MT、 /LD （使用執行階段程式庫）](../../build/reference/md-mt-ld-use-run-time-library.md)主題。  
  
-   當使用 **/Zi**與 **/clr**，效能的影響。 如需詳細資訊，請參閱[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
-   將寬字元傳遞至.NET Framework 未同時指定輸出常式[/zc: wchar_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)或不含轉換的字元`__wchar_t`會導致輸出會顯示為`unsigned short int`。 例如:   
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [/GS](../../build/reference/gs-buffer-security-check.md)編譯時，會忽略 **/clr**，除非您的函式是在`#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md)或者如果必須為原生編譯的函式，在此情況下，編譯器會產生警告 C4793，預設為關閉。  
  
-   請參閱[/ENTRY](../../build/reference/entry-entry-point-symbol.md)的受管理的應用程式的函式簽章需求。  
  
-   使用應用程式編譯 **/openmp**和 **/clr**只能在單一 appdomain 程序中執行。  請參閱[/openmp （啟用 OpenMP 2.0 支援）](../../build/reference/openmp-enable-openmp-2-0-support.md)如需詳細資訊。  
  
-   接受可變數目的引數 (varargs) 數的函式將會以原生函式產生。 變數引數位置中的任何 managed 的資料類型會封送處理至原生類型。 請注意，<xref:System.String?displayProperty=fullName>類型實際上的寬字元字串，但它們會封送處理至單一位元組字元字串。 因此如果 printf 規範 %S （wchar_t *），它會封送處理為 %s 字串改為。  
  
-   時使用 va_arg 巨集，您可能會收到非預期的結果以編譯時 **/clr: pure**。  如需詳細資訊，請參閱[va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。  
  
-   您不應該呼叫，從 managed 程式碼，以便取得參數資訊 （函式引數），堆疊查核行程的任何函式P/Invoke 層可讓該堆疊的深處進一步的資訊。  例如，不會編譯 proxy/stub 與 **/clr**。  
  
-   函式將會編譯為 managed 程式碼，可能的話，但並非所有的 c + + 建構可以轉譯成 managed 程式碼。  這項判斷是對函式的函式為基礎。 如果函式的任何部分無法轉換成 managed 程式碼中，整個函式將會轉換至原生程式碼。 下列情況下防止編譯器產生 managed 程式碼。  
  
    -   編譯器產生的 thunk 或 helper 函式。 所有透過函式指標，包括虛擬函式呼叫的函式呼叫會產生原生的 thunk。  
  
    -   函式呼叫`setjmp`或`longjmp`。  
  
    -   特定內建常式使用直接操作 機器資源的函式。 例如，使用`__enable`和`__disable`，`_ReturnAddress`和`_AddressOfReturnAddress`，或多媒體內建函式會在原生程式碼中的所有結果。  
  
    -   函式後面`#pragma unmanaged`指示詞。 (請注意，反向`#pragma managed`，也支援。)  
  
    -   包含參考的函式對齊類型，也就是使用宣告型別`__declspec(align(...))`。  
  
## <a name="see-also"></a>另請參閱  
 [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)