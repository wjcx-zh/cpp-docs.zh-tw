---
title: 預先定義巨集 |Microsoft Docs
ms.custom: update_every_version
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
dev_langs:
- C++
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a95141aa97d7272970adaaa69f3f63de2a622780
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235642"
---
# <a name="predefined-macros"></a>預先定義的巨集

Visual c + + 編譯器會預先定義特定的前置處理器巨集，視語言 （C 或 c + +）、 編譯目標和所選擇的編譯器選項而定。

Visual c + + 支援需要預先定義前置處理器巨集的 ANSI/ISO C99 標準和 ISO C + + 14 標準所指定。 實作也支援數個多個 Microsoft 專有前置處理器巨集。 僅適用於特定的建置環境或編譯器選項定義一些巨集。 若為已指定為除非另有說明，巨集會定義整個轉譯單位 **/D**編譯器選項引數。 定義時，巨集是由前置處理器在編譯之前展開指定的值。 預先定義的巨集不接受引數，並不能重新定義。

## <a name="standard-predefined-identifier"></a>標準預先定義的識別項

編譯器支援 ISO C99 和 ISO c++11 標準所指定此預先定義的識別碼。

- **&#95;&#95;func&#95; &#95;** 函式本機封入函式不合格及未修飾名稱**靜態 const**陣列**char**。

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>標準的預先定義巨集

編譯器支援下列 ISO C99 和 ISO C + + 17 標準所指定的預先定義巨集。

- **&#95;&#95;cplusplus**時轉譯單位會編譯為 c + + 定義為整數常值。 否則，未定義。

- **&#95;&#95;日期&#95;&#95;** 目前的原始程式檔的編譯日期。 日期是固定長度字串常值形式*Mmm dd yyyy*。 月份*Mmm*等同於中的縮寫的月份名稱的 C 執行階段程式庫所產生的日期[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式。 日期的第一個字元*dd*是空格，此值是否小於 10。 一律定義此巨集。

- **&#95;&#95;檔案&#95;&#95;** 目前的原始程式檔的名稱。 **&#95;&#95;檔案&#95;&#95;** 展開字元字串常值。 若要確保顯示檔案的完整路徑，使用[/FC （完整路徑的來源診斷中原始程式碼檔）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 一律定義此巨集。

- **&#95;&#95;行&#95;&#95;** 定義為整數的行號，在目前的原始程式檔中。 值 **&#95;&#95;行&#95;&#95;** 巨集可以變更利用`#line`指示詞。 一律定義此巨集。

- **&#95;&#95;STDC&#95; &#95;** 定義為 1，只有在編譯為 C 時，如果[/Za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項指定。 否則，未定義。

- **&#95;&#95;STDC&#95;HOSTED&#95; &#95;** 定義為 1，如果實作是*裝載實作*，支援整個必要的標準程式庫。 否則，定義為 0。

- **&#95;&#95;STDCPP&#95;執行緒&#95;&#95;** 定義為 1，如果且只有一個程式可以擁有多個執行的執行緒，且編譯為 c + +。 否則，未定義。

- **&#95;&#95;時間&#95;&#95;** 翻譯的前置處理過的轉譯單位的時間。 時間是字元字串常值形式*hh: mm:*，C 執行階段程式庫所傳回的時間與相同[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式。 一律定義此巨集。

## <a name="microsoft-specific-predefined-macros"></a>Microsoft 專有的預先定義巨集

Microsoft Visual c + + 支援這些額外的預先定義巨集。

- **&#95;&#95;ATOM&#95; &#95;** 定義為 1 時[/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md)編譯器選項設定，且編譯器目標是 x86 或 x64。 否則，未定義。

- **&#95;&#95;AVX&#95; &#95;** 定義為 1 時[/arch: avx](../build/reference/arch-x86.md)或是[/arch:avx2](../build/reference/arch-x86.md)設定編譯器選項，編譯器目標是 x86 或 x64。 否則，未定義。

- **&#95;&#95;AVX2&#95; &#95;** 定義為 1 時[/arch:avx2](../build/reference/arch-x86.md)編譯器選項設定，且編譯器目標是 x86 或 x64。 否則，未定義。

- **&#95;CHAR&#95;不帶正負號**定義為 1，否則預設值**char**型別是不帶正負號。 這會設定何時[/J (預設 char 類型為 unsigned)](../build/reference/j-default-char-type-is-unsigned.md)設定編譯器選項。 否則，未定義。

- **&#95;&#95;CLR&#95;VER**定義為整數常值，表示已編譯應用程式時所使用的 common language runtime 版本。 值以表單編碼`Mmmbbbbb`，其中`M`是執行階段的主要版本`mm`是執行階段的次要版本和`bbbbb`是組建編號。 **&#95;&#95;CLR&#95;VER**如果定義[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則，未定義。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;控制&#95;資料流程&#95;防護**定義為 1 時[/guard: cf （啟用控制流程防護）](../build/reference/guard-enable-control-flow-guard.md)編譯器選項設定。 否則，未定義。

- **&#95;&#95;計數器&#95;&#95;** 展開為整數常值從 0 開始並每次原始程式檔中使用時，會加 1，或包含的原始程式檔的標頭。 **&#95;&#95;計數器&#95;&#95;** 當您使用先行編譯標頭時，會記住其狀態。 一律定義此巨集。

  這個範例會使用`__COUNTER__`將唯一識別碼指派給相同類型的三個不同的物件。 `exampleClass`建構函式會接受整數作為參數。 在  `main`，應用程式會宣告三個物件的型別`exampleClass`，並使用`__COUNTER__`做為唯一識別項參數：

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- **&#95;&#95;cplusplus&#95;cli**定義為整數常值 200406 編譯為 c + + 時， [/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則，未定義。 定義時，  **&#95; &#95;cplusplus&#95;cli**適用於整個轉譯單位。

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95;&#95;cplusplus&#95;winrt**定義為整數常值 201009 編譯為 c + + 時， [/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)編譯器選項設定。 否則，未定義。

- **&#95;CPPRTTI**定義為 1，否則[/GR （啟用執行階段類型資訊）](../build/reference/gr-enable-run-time-type-information.md)設定編譯器選項。 否則，未定義。

- **&#95;CPPUNWIND**定義為 1，如果一或多個[/GX （啟用例外狀況處理）](../build/reference/gx-enable-exception-handling.md)， [/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)，或[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項設定。 否則，未定義。

- **&#95;偵錯**定義為 1 時， [/LDd](../build/reference/md-mt-ld-use-run-time-library.md)， [/MDd](../build/reference/md-mt-ld-use-run-time-library.md)，或[/MTd](../build/reference/md-mt-ld-use-run-time-library.md)設定編譯器選項。 否則，未定義。

- **&#95;DLL**定義為 1 時， [/MD](../build/reference/md-mt-ld-use-run-time-library.md)或是[/MDd](../build/reference/md-mt-ld-use-run-time-library.md)設定 (Multithreaded DLL) 編譯器選項。 否則，未定義。

- **&#95;&#95;FUNCDNAME&#95; &#95;** 定義為字串常值，其中包含[裝飾名稱](../build/reference/decorated-names.md)封入函式。 只能在函式內定義的巨集。 **&#95; &#95;FUNCDNAME&#95; &#95;** 如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或是[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。

   這個範例會使用`__FUNCDNAME__`， `__FUNCSIG__`，和`__FUNCTION__`巨集來顯示函式的資訊。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;** 定義為字串常值，其中包含封入函式的簽章。 只能在函式內定義的巨集。 **&#95; &#95;FUNCSIG&#95; &#95;** 如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或是[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。 當針對 64 位元目標編譯時，呼叫慣例是`__cdecl`預設。 如需使用方式的範例，請參閱`__FUNCDNAME__`巨集。

- **&#95;&#95;函式&#95;&#95;** 定義為字串常值，其中包含封入函式的未裝飾的名稱。 只能在函式內定義的巨集。 **&#95;&#95;函式&#95;&#95;** 如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或是[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。 如需使用方式的範例，請參閱`__FUNCDNAME__`巨集。

- **&#95;整數&#95;MAX&#95;位元**為 64 的整數常值的定義、 非向量的整數類資料類型的大小上限 （以位元為單位）。 一律定義此巨集。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;** 定義為 1 時的 IntelliSense 編譯器傳遞 Visual Studio IDE 中。 否則，未定義。 您可以使用這個巨集來保護程式碼 IntelliSense 編譯器不會了解，或使用它來組建和 IntelliSense 編譯器之間切換。 如需詳細資訊，請參閱 < [IntelliSense 速度很慢的疑難排解秘訣](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/)。

- **&#95;ISO&#95;VOLATILE**定義為 1，否則[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項設定。 否則，未定義。

- **&#95;核心&#95;模式**定義為 1，否則[/kernel （建立核心模式二進位檔）](../build/reference/kernel-create-kernel-mode-binary.md)編譯器選項設定。 否則，未定義。

- **&#95;M&#95;AMD64**定義為常值的整數值的 100 編譯該目標 x64 處理器。 否則，未定義。

- **&#95;M&#95;ARM**定義為 ARM 處理器為目標的編譯次數的整數常值 7。 否則，未定義。

- **&#95;M&#95;ARM&#95;ARMV7VE**定義為 1 時[/arch:armv7ve](../build/reference/arch-arm.md)編譯器選項設定為 ARM 處理器為目標的編譯。 否則，未定義。

- **&#95;M&#95;ARM&#95;FP**定義為整數常值，指示何種[/arch](../build/reference/arch-arm.md)編譯器選項已設定，如果編譯目標為 ARM 處理器。 否則，未定義。

  - 在範圍內 30-39，如果沒有`/arch`ARM 選項已指定，表示 ARM 的預設架構已設定 (`VFPv3`)。

  - 在範圍 40-49 如果`/arch:VFPv4`設定。

  - 請參閱[/arch (ARM)](../build/reference/arch-arm.md)如需詳細資訊。

- **&#95;M&#95;ARM64**定義為 1 以 64 位元 ARM 處理器為目標的編譯。 否則，未定義。

- **&#95;M&#95;CEE**定義為 001 如果任何[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則，未定義。

- **&#95;M&#95;CEE&#95;PURE**開始，Visual Studio 2015 中的已被取代。 定義為 001 if [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)設定編譯器選項。 否則，未定義。

- **&#95;M&#95;CEE&#95;安全**開始，Visual Studio 2015 中的已被取代。 定義為 001 if [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md)設定編譯器選項。 否則，未定義。

- **&#95;M&#95;FP&#95;EXCEPT**定義為 1，否則[/fp： 除了](../build/reference/fp-specify-floating-point-behavior.md)或是[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)設定編譯器選項。 否則，未定義。

- **&#95;M&#95;FP&#95;快速**定義為 1，否則[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則，未定義。

- **&#95;M&#95;FP&#95;PRECISE**定義為 1，否則[/fp： 精確](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則，未定義。

- **&#95;M&#95;FP&#95;STRICT**定義為 1，否則[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則，未定義。

- **&#95;M&#95;IX86**定義為整數常值的值 600 編譯該目標 x86 處理器。 X64 或 ARM 編譯目標未定義此巨集。

- **&#95;M&#95;IX86&#95;FP**定義為整數常值，指出[/arch](../build/reference/arch-arm.md)編譯器選項集，或預設值。 這個巨集一律已定義時的編譯目標為 x86 處理器。 否則，未定義。 定義時，這個值會是：

  - 0`/arch:IA32`編譯器選項已設定。

  - 1，否則`/arch:SSE`編譯器選項已設定。

  - 2 if `/arch:SSE2`，`/arch:AVX`或`/arch:AVX2`編譯器選項已設定。 這個值是預設值，如果`/arch`未指定編譯器選項。 當`/arch:AVX`未指定，巨集會 **&#95; &#95;AVX&#95; &#95;** 也會定義。 當`/arch:AVX2`指定，則兩者 **&#95; &#95;AVX&#95; &#95;** 並 **&#95; &#95;AVX2&#95; &#95;** 也會定義。

  - 請參閱[/(x86)](../build/reference/arch-x86.md)如需詳細資訊。

- **&#95;M&#95;X64**定義為常值的整數值的 100 編譯該目標 x64 處理器。 否則，未定義。

- **&#95;受控**定義為 1 時， [/clr](../build/reference/clr-common-language-runtime-compilation.md)設定編譯器選項。 否則，未定義。

- **&#95;MSC&#95;建置**定義為整數常值，其中包含編譯器的版本號碼的修訂編號項目。 修訂編號是句號分隔版本號碼的第四個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01，  **&#95;MSC&#95;建置**巨集判斷值為 1。 一律定義此巨集。

- **&#95;MSC&#95;延伸模組**定義為 1，否則[/Ze （啟用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md)編譯器選項會設定，這是預設值。 否則，未定義。

- **&#95;MSC&#95;完整&#95;VER**定義為整數常值，可以編碼主要，次要和組建的編譯器版本號碼的數字項目。 主要號碼是句號分隔版本號碼的第一個元素、 次要版本號碼是第二個項目，和組建編號是第三個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01，  **&#95;MSC&#95;FULL&#95;VER**巨集判斷值為 150020706。 輸入`cl /?`在命令列，以檢視編譯器的版本號碼。 一律定義此巨集。

- **&#95;MSC&#95;VER**定義為編譯器版本號碼的主要和次要編號項目會將編碼的整數常值。 主要號碼是句號分隔版本號碼的第一個項目和次要版本號碼是第二個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 17.00.51106.1，  **&#95;MSC&#95;VER**巨集判斷值為 1700年。 輸入`cl /?`在命令列，以檢視編譯器的版本號碼。 一律定義此巨集。

   |Visual Studio 版本|&AMP;#95;MSC&AMP;#95;V|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio.NET 2002 (7.0)|1300|
   |Visual Studio.NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|為 1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 15.3 版|為 1911，|
   |Visual Studio 2017 15.5 版|1912|
   |Visual Studio 2017 15.6 版|1913|
   |Visual Studio 2017 15.7 版|1914|

   若要測試為編譯器版本或更新指定版本的 Visual Studio 或之後，使用**>=** （大於或等於） 運算子來比較 **&#95;MSC&#95;VER**針對已知版本。 如果您有數個版本中是互斥的方式比較時，我們建議您訂購的版本號碼的遞減順序比較。 比方說，這段程式碼會檢查發行 Visual Studio 2015 和更新版本的編譯器中，或在 Visual Studio 2013 之後, 發行的編譯器，則會採用所有編譯器發行 Visual Studio 2013 之前的動作，然後：

   ```cpp
   #if _MSC_VER >= 1900
   // . . .
   #elif _MSC_VER >= 1800
   // . . .
   #else
   // . . .
   #endif
   ```

   如需詳細資訊，請參閱 < [Visual c + + 編譯器版本](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/)Visual c + + Team 部落格中。

- **&#95;MSVC&#95;LANG**定義為整數常值，指定編譯器為目標的 c + + 語言標準。 當編譯為 c + +，巨集如果是整數常值 201402 L [/std: c + + 14](../build/reference/std-specify-language-standard-version.md)編譯器選項設定，或根據預設值; 它設定為 201703 L 如果[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)編譯器選項已設定，並設定為更高版本，未指定值的時機[/std: c + + 最新](../build/reference/std-specify-language-standard-version.md)。 否則，巨集未定義。 **&#95;MSVC&#95;LANG**巨集並[/std （指定語言標準版本）](../build/reference/std-specify-language-standard-version.md)編譯器選項會在 Visual Studio 2015 Update 3 開始提供。

- **&#95;&#95;MSVC&#95;執行階段&#95;會檢查**定義為 1 時的[/RTC](../build/reference/rtc-run-time-error-checks.md)編譯器選項設定。 否則，未定義。

- **&#95;MT**定義為 1 時， [/MD 或 /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded DLL) 或[/MT 或 /MTd](../build/reference/md-mt-ld-use-run-time-library.md)指定 （多執行緒）。 否則，未定義。

- **&#95;原生&#95;WCHAR&#95;T&#95;定義**定義為 1 時[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項設定。 否則，未定義。

- **&#95;OPENMP**定義為代表 Visual c + + 所實作的 OpenMP 規格的日期，如果整數常值的 200203 [/openmp （啟用 OpenMP 2.0 支援）](../build/reference/openmp-enable-openmp-2-0-support.md)設定編譯器選項。 否則，未定義。

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;** 定義為 1 時， [/analyze](../build/reference/analyze-code-analysis.md)編譯器選項設定。 否則，未定義。

- **&#95;&#95;時間戳記&#95;&#95;** 定義為包含的日期和目前的原始程式檔，由 C 執行階段程式庫的縮寫、 固定長度形式的上次修改時間字串常值[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式，例如`Fri 19 Aug 13:32:58 2016`。 一律定義此巨集。

- **&#95;VC&#95;/NODEFAULTLIB**定義為 1 時， [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md)編譯器選項設定。 否則，未定義。

- **&#95;WCHAR&#95;T&#95;定義**定義為 1 時，預設值[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項設定。 **&#95;WCHAR&#95;T&#95;定義**巨集已定義，但是沒有任何值，如果`/Zc:wchar_t-`編譯器選項設定，以及**wchar_t**中包含的系統標頭檔中定義您專案。 否則，未定義。

- **&#95;WIN32**定義為 1 時的編譯目標為 32 位元 ARM，64 位元 ARM x86 或 x64。 否則，未定義。

- **&#95;WIN64**定義為 1，當編譯目標為 64 位元 ARM 或 x64。 否則，未定義。

- **&#95;WINRT&#95;DLL**定義為 1 時，編譯為 c + + 和兩者[/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)並[/LD 或 /LDd](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項設定。 否則，未定義。

編譯器不預先定義前置處理器巨集，用來判斷 ATL 或 MFC 程式庫版本。 這些巨集是在程式庫、 標頭中定義的所以並未在前置處理器指示詞中定義，才會包含所需的標頭。

- **&#95;ATL&#95;VER**中定義\<atldef.h > 編碼 ATL 版本號碼的整數常值。

- **&#95;MFC&#95;VER**中定義\<afxver_.h > 編碼 MFC 版本號碼的整數常值。

## <a name="see-also"></a>另請參閱

[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[前置處理器運算子](../preprocessor/preprocessor-operators.md)<br/>
[前置處理器指示詞](../preprocessor/preprocessor-directives.md)