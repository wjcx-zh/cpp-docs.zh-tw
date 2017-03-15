---
title: "/clr 限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 限制"
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# /clr 限制
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

請注意下列使用 **\/clr** 的限制：  
  
-   在結構化例外狀況處理常式中，以 **\/clr** 編譯時，使用 `_alloca` 會有限制。  如需詳細資訊，請參閱 [\_alloca](../../c-runtime-library/reference/alloca.md)。  
  
-   使用執行階段錯誤檢查，在配合 **\/clr** 使用時無效。  如需詳細資訊，請參閱[執行階段錯誤檢查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
-   以 **\/clr** 編譯僅使用標準 C\+\+ 語法的程式時，若使用內嵌組譯碼則適用下列方針：  
  
    -   如果原生堆疊配置、目前函式以外的呼叫慣例，或其他有關電腦低階資訊這些知識是套用至 Managed 函式的堆疊框架 \(Stack Frame\)，則採用這些知識的內嵌組譯程式碼 \(Inline Assembly Code\) 將會失敗。  含有內嵌組譯程式碼的函式會以 Unmanaged 函式形式產生，就好像這些函式是放置在未使用 **\/clr** 編譯的其他模組中。  
  
    -   傳遞以複製建構之函式參數的函式中不支援內嵌組譯程式碼。  
  
-   不能從使用 **\/clr** 編譯的程式呼叫 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)。  
  
-   在 \/clr 之下，[naked](../../cpp/naked-cpp.md) [\_\_declspec](../../cpp/declspec.md) 修飾詞 \(Modifier\) 會被忽略。  
  
-   由 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md) 設定的轉譯器函式只會影響 Unmanaged 程式碼中的快取。  如需詳細資訊，請參閱[Exception Handling](../../windows/exception-handling-cpp-component-extensions.md)。  
  
-   在 **\/clr** 之下不允許函式指標的比較。  
  
-   在 **\/clr** 之下不允許使用非完整原型的函式。  
  
-   下列編譯器選項在 **\/clr** 下不支援：  
  
    -   **\/EHsc** 和 **\/EHs** \(**\/clr** 隱含 **\/EHa** \(請參閱 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)\)  
  
    -   **\/fp:strict** 和 **\/fp:except** \(請參閱 [\/fp \(指定浮點數行為\)](../../build/reference/fp-specify-floating-point-behavior.md)\)  
  
    -   [\/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [\/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [\/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **\/ZI**  
  
-   不支援 `_STATIC_CPPLIB` 前置處理器定義 \(`/D_STATIC_CPPLIB`\) 和 **\/clr** 或 **\/clr:pure** 編譯器選項的組合。  這是因為此定義可能會導致您的應用程式與靜態多執行緒 Standard C\+\+ 程式庫連結，而這是不受支援的。  如需詳細資訊，請參閱[\/MD、\/MT、\/LD \(使用執行階段程式庫\)](../../build/reference/md-mt-ld-use-run-time-library.md)主題。  
  
-   [\/J](../../build/reference/j-default-char-type-is-unsigned.md) 在 **\/clr:safe** 或 **\/clr:pure** 之下不支援。  
  
-   純模式編譯 \(**\/clr:pure**\) 不支援 ATL 和 MFC 程式庫。  如果您也使用 **\/MD** 或 **\/MDd** 進行編譯，可以使用 **\/clr:pure** 搭配 Standard C\+\+ 程式碼和 CRT。  
  
-   使用 **\/Zi** 配合 **\/clr** 時，會隱含對效能的影響。  如需詳細資訊，請參閱 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
-   傳遞萬用字元給 .NET Framework 輸出常式而未同時指定 [\/Zc:wchar\_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)，或未將該字元轉換為 `__wchar_t`，將會造成輸出顯示為 `unsigned short int`。  例如：  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   使用 **\/clr** 編譯時，會忽略 [\/GS](../../build/reference/gs-buffer-security-check.md)，除非函式是在 `#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md) 之下，或者函式必須編譯成原生 \(Native\) \(這項作業預設為關閉\)，在這種情況下，編譯器將會產生警告 C4793。  
  
-   如需 Managed 應用程式的函式簽章需求，請參閱 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md)。  
  
-   使用 **\/openmp** 和 **\/clr** 編譯的應用程式僅能在單一 appdomain 處理中執行。如需詳細資訊，請參閱[\/openmp \(啟用 OpenMP 2.0 支援\)](../../build/reference/openmp-enable-openmp-2-0-support.md)。  
  
-   採用引數的變數數字 \(varargs\) 之函式，將產生成原生函式。  變數引數位置內的任何 Managed 資料型別將封送至原生型別。  請注意，<xref:System.String?displayProperty=fullName> 型別實際上為寬字元字串，不過它們會封送至單位元組字元字串。  因此若 printf 規範為 %S \(wchar\_t\*\)，它就會改封送至 %s 字串。  
  
-   使用 va\_arg macro 時，如果以 **\/clr:pure** 編譯，您可能會得到意外的結果。如需詳細資訊，請參閱[va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。  
  
-   如果您的應用程式將型別 [va\_list](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 的引數傳遞至宣告採用 [引數變數數目](../../misc/variable-argument-lists.md)的函式，且您的應用程式是以 **\/clr:pure** 編譯的，CLR 會擲回<xref:System.NotSupportedException>。  如果改用 **\/clr** ，會將受影響的函式編譯為機器碼並正確執行。  如果使用**\/clr:safe**，會發出錯誤診斷。  
  
-   您不可以從 Managed 程式碼呼叫任何進行堆疊查核行程以取得參數資訊 \(函式引數\) 的函式；P\/Invoke 層會導致該項資訊進一步向下堆疊。例如，不要使用 **\/clr** 編譯 proxy\/stub。  
  
-   函式將盡可能地編譯成 Managed 程式碼，但並不是所有 C\+\+ 建構都可以轉譯成 Managed 程式碼。這是逐一根據各個函式加以判定。  如果函式有任何部分無法轉換成 Managed 程式碼，則整個函式都會改為轉換成機器碼。  下列各種情形都會阻止編譯器產生 Managed 程式碼。  
  
    -   編譯器產生的 Thunk 或 helper 函式。  原生 Thunk 是為任何透過函式指標呼叫之函式而產生的，包括虛擬函式呼叫在內。  
  
    -   呼叫 `setjmp` 或 `longjmp` 的函式。  
  
    -   使用特定內建常式，以直接管理電腦資源的函式。  例如，使用 `__enable` 和 `__disable`、`_ReturnAddress` 和 `_AddressOfReturnAddress`，或者多個內建全部都會產生機器碼。  
  
    -   跟隨在 `#pragma unmanaged` 指示詞之後的函式 \(請注意，也支援相反的情況，`#pragma managed`\)。  
  
    -   包含對齊型別參考的函式，也就是，使用 `__declspec(align(...))` 加以宣告的型別。  
  
-   您不能使用 [編譯器 COM 支援](../../cpp/compiler-com-support.md) 類別配合 **\/clr:pure** 或 **\/clr:safe**。  
  
## 請參閱  
 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)