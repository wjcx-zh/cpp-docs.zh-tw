---
title: 預先定義巨集
description: 列出並描述 Microsoft c + + 編譯器預先定義的預處理器宏。
ms.custom: update_every_version
ms.date: 06/08/2020
f1_keywords:
- ':::no-loc(_ATL_VER):::'
- ':::no-loc(__ATOM__):::'
- ':::no-loc(__AVX__):::'
- ':::no-loc(__AVX2__):::'
- ':::no-loc(__AVX512BW__):::'
- ':::no-loc(__AVX512CD__):::'
- ':::no-loc(__AVX512DQ__):::'
- ':::no-loc(__AVX512F__):::'
- ':::no-loc(__AVX512VL__):::'
- ':::no-loc(_CHAR_UNSIGNED):::'
- ':::no-loc(__CLR_VER):::'
- ':::no-loc(_CONTROL_FLOW_GUARD):::'
- ':::no-loc(__COUNTER__):::'
- ':::no-loc(__cplusplus):::'
- ':::no-loc(__cplusplus_cli):::'
- ':::no-loc(__cplusplus_winrt):::'
- ':::no-loc(_CPPRTTI):::'
- ':::no-loc(_CPPUNWIND):::'
- ':::no-loc(__DATE__):::'
- ':::no-loc(_DEBUG):::'
- ':::no-loc(_DLL):::'
- ':::no-loc(__FILE__):::'
- ':::no-loc(__FUNCDNAME__):::'
- ':::no-loc(__FUNCSIG__):::'
- ':::no-loc(__FUNCTION__):::'
- ':::no-loc(_INTEGRAL_MAX_BITS):::'
- ':::no-loc(_ISO_VOLATILE):::'
- ':::no-loc(_KERNEL_MODE):::'
- ':::no-loc(__LINE__):::'
- ':::no-loc(_M_AMD64):::'
- ':::no-loc(_M_ARM):::'
- ':::no-loc(_M_ARM_ARMV7VE):::'
- ':::no-loc(_M_ARM_FP):::'
- ':::no-loc(_M_ARM64):::'
- ':::no-loc(_M_CEE):::'
- ':::no-loc(_M_CEE_PURE):::'
- ':::no-loc(_M_CEE_SAFE):::'
- ':::no-loc(_M_FP_EXCEPT):::'
- ':::no-loc(_M_FP_FAST):::'
- ':::no-loc(_M_FP_PRECISE):::'
- ':::no-loc(_M_FP_STRICT):::'
- ':::no-loc(_M_IX86):::'
- ':::no-loc(_M_IX86_FP):::'
- ':::no-loc(_M_X64):::'
- ':::no-loc(_MANAGED):::'
- ':::no-loc(_MFC_VER):::'
- ':::no-loc(_MSC_BUILD):::'
- ':::no-loc(_MSC_EXTENSIONS):::'
- ':::no-loc(_MSC_FULL_VER):::'
- ':::no-loc(_MSC_VER):::'
- ':::no-loc(_MSVC_LANG):::'
- ':::no-loc(__MSVC_RUNTIME_CHECKS):::'
- ':::no-loc(_MT):::'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED):::'
- ':::no-loc(_NO_SIZED_DEALLOCATION):::'
- ':::no-loc(_OPENMP):::'
- ':::no-loc(_PREFAST_):::'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED):::'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED):::'
- ':::no-loc(__STDC__):::'
- ':::no-loc(__STDC_HOSTED__):::'
- ':::no-loc(__STDCPP_THREADS__):::'
- ':::no-loc(__TIME__):::'
- ':::no-loc(__TIMESTAMP__):::'
- ':::no-loc(__VA_ARGS__):::'
- ':::no-loc(_VC_NODEFAULTLIB):::'
- ':::no-loc(_WCHAR_T_DEFINED):::'
- ':::no-loc(_WIN32):::'
- ':::no-loc(_WIN64):::'
- ':::no-loc(_WINRT_DLL):::'
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- ':::no-loc(_ATL_VER)::: macro'
- ':::no-loc(__ATOM__)::: macro'
- ':::no-loc(__AVX__)::: macro'
- ':::no-loc(__AVX2__)::: macro'
- ':::no-loc(__AVX512BW__)::: macro'
- ':::no-loc(__AVX512CD__)::: macro'
- ':::no-loc(__AVX512DQ__)::: macro'
- ':::no-loc(__AVX512F__)::: macro'
- ':::no-loc(__AVX512VL__)::: macro'
- ':::no-loc(_CHAR_UNSIGNED)::: macro'
- ':::no-loc(__CLR_VER)::: macro'
- ':::no-loc(_CONTROL_FLOW_GUARD)::: macro'
- ':::no-loc(__COUNTER__)::: macro'
- ':::no-loc(__cplusplus)::: macro'
- ':::no-loc(__cplusplus_cli)::: macro'
- ':::no-loc(__cplusplus_winrt)::: macro'
- ':::no-loc(_CPPRTTI)::: macro'
- ':::no-loc(_CPPUNWIND)::: macro'
- ':::no-loc(__DATE__)::: macro'
- ':::no-loc(_DEBUG)::: macro'
- ':::no-loc(_DLL)::: macro'
- ':::no-loc(__FILE__)::: macro'
- ':::no-loc(__FUNCDNAME__)::: macro'
- ':::no-loc(__FUNCSIG__)::: macro'
- ':::no-loc(__FUNCTION__)::: macro'
- ':::no-loc(_INTEGRAL_MAX_BITS)::: macro'
- ':::no-loc(_ISO_VOLATILE)::: macro'
- ':::no-loc(_KERNEL_MODE)::: macro'
- ':::no-loc(__LINE__)::: macro'
- ':::no-loc(_M_AMD64)::: macro'
- ':::no-loc(_M_ARM)::: macro'
- ':::no-loc(_M_ARM_ARMV7VE)::: macro'
- ':::no-loc(_M_ARM_FP)::: macro'
- ':::no-loc(_M_ARM64)::: macro'
- ':::no-loc(_M_CEE)::: macro'
- ':::no-loc(_M_CEE_PURE)::: macro'
- ':::no-loc(_M_CEE_SAFE)::: macro'
- ':::no-loc(_M_FP_EXCEPT)::: macro'
- ':::no-loc(_M_FP_FAST)::: macro'
- ':::no-loc(_M_FP_PRECISE)::: macro'
- ':::no-loc(_M_FP_STRICT)::: macro'
- ':::no-loc(_M_IX86)::: macro'
- ':::no-loc(_M_IX86_FP)::: macro'
- ':::no-loc(_M_X64)::: macro'
- ':::no-loc(_MANAGED)::: macro'
- ':::no-loc(_MFC_VER)::: macro'
- ':::no-loc(_MSC_BUILD)::: macro'
- ':::no-loc(_MSC_EXTENSIONS)::: macro'
- ':::no-loc(_MSC_FULL_VER)::: macro'
- ':::no-loc(_MSC_VER)::: macro'
- ':::no-loc(_MSVC_LANG)::: macro'
- ':::no-loc(__MSVC_RUNTIME_CHECKS)::: macro'
- ':::no-loc(_MT)::: macro'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED)::: macro'
- ':::no-loc(_NO_SIZED_DEALLOCATION)::: macro'
- ':::no-loc(_OPENMP)::: macro'
- ':::no-loc(_PREFAST_)::: macro'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED)::: macro'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED)::: macro'
- ':::no-loc(__STDC__)::: macro'
- ':::no-loc(__STDC_HOSTED__)::: macro'
- ':::no-loc(__STDCPP_THREADS__)::: macro'
- ':::no-loc(__TIME__)::: macro'
- ':::no-loc(__TIMESTAMP__)::: macro'
- ':::no-loc(__VA_ARGS__)::: macro'
- ':::no-loc(_VC_NODEFAULTLIB)::: macro'
- ':::no-loc(_WCHAR_T_DEFINED)::: macro'
- ':::no-loc(_WIN32)::: macro'
- ':::no-loc(_WIN64)::: macro'
- ':::no-loc(_WINRT_DLL)::: macro'
- ':::no-loc(__func__)::: identifier'
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
no-loc:
- ':::no-loc(_ATL_VER):::'
- ':::no-loc(__ATOM__):::'
- ':::no-loc(__AVX__):::'
- ':::no-loc(__AVX2__):::'
- ':::no-loc(__AVX512BW__):::'
- ':::no-loc(__AVX512CD__):::'
- ':::no-loc(__AVX512DQ__):::'
- ':::no-loc(__AVX512F__):::'
- ':::no-loc(__AVX512VL__):::'
- ':::no-loc(_CHAR_UNSIGNED):::'
- ':::no-loc(__CLR_VER):::'
- ':::no-loc(_CONTROL_FLOW_GUARD):::'
- ':::no-loc(__COUNTER__):::'
- ':::no-loc(__cplusplus):::'
- ':::no-loc(__cplusplus_cli):::'
- ':::no-loc(__cplusplus_winrt):::'
- ':::no-loc(_CPPRTTI):::'
- ':::no-loc(_CPPUNWIND):::'
- ':::no-loc(__DATE__):::'
- ':::no-loc(_DEBUG):::'
- ':::no-loc(_DLL):::'
- ':::no-loc(__FILE__):::'
- ':::no-loc(__FUNCDNAME__):::'
- ':::no-loc(__FUNCSIG__):::'
- ':::no-loc(__FUNCTION__):::'
- ':::no-loc(_INTEGRAL_MAX_BITS):::'
- ':::no-loc(_ISO_VOLATILE):::'
- ':::no-loc(_KERNEL_MODE):::'
- ':::no-loc(__LINE__):::'
- ':::no-loc(_M_AMD64):::'
- ':::no-loc(_M_ARM):::'
- ':::no-loc(_M_ARM_ARMV7VE):::'
- ':::no-loc(_M_ARM_FP):::'
- ':::no-loc(_M_ARM64):::'
- ':::no-loc(_M_CEE):::'
- ':::no-loc(_M_CEE_PURE):::'
- ':::no-loc(_M_CEE_SAFE):::'
- ':::no-loc(_M_FP_EXCEPT):::'
- ':::no-loc(_M_FP_FAST):::'
- ':::no-loc(_M_FP_PRECISE):::'
- ':::no-loc(_M_FP_STRICT):::'
- ':::no-loc(_M_IX86):::'
- ':::no-loc(_M_IX86_FP):::'
- ':::no-loc(_M_X64):::'
- ':::no-loc(_MANAGED):::'
- ':::no-loc(_MFC_VER):::'
- ':::no-loc(_MSC_BUILD):::'
- ':::no-loc(_MSC_EXTENSIONS):::'
- ':::no-loc(_MSC_FULL_VER):::'
- ':::no-loc(_MSC_VER):::'
- ':::no-loc(_MSVC_LANG):::'
- ':::no-loc(__MSVC_RUNTIME_CHECKS):::'
- ':::no-loc(_MT):::'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED):::'
- ':::no-loc(_NO_SIZED_DEALLOCATION):::'
- ':::no-loc(_OPENMP):::'
- ':::no-loc(_PREFAST_):::'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED):::'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED):::'
- ':::no-loc(__STDC__):::'
- ':::no-loc(__STDC_HOSTED__):::'
- ':::no-loc(__STDCPP_THREADS__):::'
- ':::no-loc(__TIME__):::'
- ':::no-loc(__TIMESTAMP__):::'
- ':::no-loc(__VA_ARGS__):::'
- ':::no-loc(_VC_NODEFAULTLIB):::'
- ':::no-loc(_WCHAR_T_DEFINED):::'
- ':::no-loc(_WIN32):::'
- ':::no-loc(_WIN64):::'
- ':::no-loc(_WINRT_DLL):::'
- ':::no-loc(__func__):::'
ms.openlocfilehash: 1c7b2f18aede84d8067c36537f33261554c16c17
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222637"
---
# <a name="predefined-macros"></a>預先定義巨集

Microsoft C/c + + 編譯器（MSVC）會根據語言（C 或 c + +）、編譯目標和所選擇的編譯器選項，預先定義特定的預處理器宏。

MSVC 支援 ANSI/ISO C99 標準和 ISO c + + 14 和 c + + 17 標準所需的預先定義預處理器宏。 此執行也支援數個 Microsoft 專屬的預處理器宏。 某些宏只會針對特定組建環境或編譯器選項來定義。 除非另有注明，否則宏會定義在整個轉譯單位中，就像是指定為 **`/D`** 編譯器選項引數一樣。 當定義時，在編譯之前，預處理器會將宏擴充為指定的值。 預先定義的宏不接受引數，也無法重新定義。

## <a name="standard-predefined-identifier"></a>標準預先定義的識別碼

編譯器支援 ISO C99 和 ISO c + + 11 所指定的這個預先定義識別碼。

- `:::no-loc(__func__):::`封入函式的不合格和未名稱，做為的函數區域**靜態常數**陣列 **`char`** 。

    ```cpp
    void example(){
        printf("%s\n", :::no-loc(__func__):::);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>標準預先定義的宏

編譯器支援 ISO C99 和 ISO c + + 17 標準所指定的這些預先定義宏。

- `:::no-loc(__cplusplus):::`當轉譯單位編譯為 c + + 時，定義為整數常值。 否則為未定義。

- `:::no-loc(__DATE__):::`目前原始檔案的編譯日期。 日期是格式為*Mmm dd yyyy*的常數長度字串常值。 月份名稱*Mmm*與 C 執行時間程式庫（CRT） [asctime](../c-runtime-library/reference/asctime-wasctime.md)函數所產生的縮寫月份名稱相同。 如果值小於10，則日期*dd*的第一個字元是空格。 這個宏一律會定義。

- `:::no-loc(__FILE__):::`目前來源檔案的名稱。 `:::no-loc(__FILE__):::`展開為字元字串常值。 若要確保顯示檔案的完整路徑，請使用[ **`/FC`** （診斷中的原始程式碼檔的完整路徑）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 這個宏一律會定義。

- `:::no-loc(__LINE__):::`定義為目前原始程式檔中的整數行號。 您可以使用指示詞來 `:::no-loc(__LINE__):::` 變更宏的值 `#line` 。 這個宏一律會定義。

- `:::no-loc(__STDC__):::`只有在編譯為 C 且已指定編譯器選項時，才會定義為 1 [**`/Za`**](../build/reference/za-ze-disable-language-extensions.md) 。 否則為未定義。

- `:::no-loc(__STDC_HOSTED__):::`如果實作為裝載的*執行*，則定義為1，其中一個支援整個必要的標準程式庫。 否則，定義為0。

- `:::no-loc(__STDCPP_THREADS__):::`只有在程式可以有一個以上的執行執行緒，而且編譯為 c + + 時，才定義為1。 否則為未定義。

- `:::no-loc(__TIME__):::`前置處理過的轉譯單位的轉譯時間。 時間是格式為*hh： mm： ss*的字元字串常值，與 CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md)函數所傳回的時間相同。 這個宏一律會定義。

## <a name="microsoft-specific-predefined-macros"></a>Microsoft 特有的預先定義宏

MSVC 支援這些額外預先定義的宏。

- `:::no-loc(__ATOM__):::`當 [**`/favor:ATOM`**](../build/reference/favor-optimize-for-architecture-specifics.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX__):::`當 [**`/arch:AVX`**](../build/reference/arch-x86.md) 、 [**`/arch:AVX2`**](../build/reference/arch-x86.md) 或 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定，且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX2__):::`當 [**`/arch:AVX2`**](../build/reference/arch-x86.md) [**`/arch:AVX512`**](../build/reference/arch-x86.md) 設定或編譯器選項，且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX512BW__):::`當 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX512CD__):::`當 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX512DQ__):::`當 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX512F__):::`當 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(__AVX512VL__):::`當 [**`/arch:AVX512`**](../build/reference/arch-x86.md) 編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(_CHAR_UNSIGNED):::`如果預設 **`char`** 類型不帶正負號，則定義為1。 此值是在設定[ **`/J`** （預設 char 類型不帶正負號）](../build/reference/j-default-char-type-is-unsigned.md)編譯器選項時所定義。 否則為未定義。

- `:::no-loc(__CLR_VER):::`定義為整數常值，表示用來編譯應用程式的 Common Language Runtime （CLR）版本。 此值會以形式編碼 `Mmmbbbbb` ，其中 `M` 是執行時間的主要版本，是執行時間的 `mm` 次要版本，而 `bbbbb` 是組建編號。 `:::no-loc(__CLR_VER):::`如果已設定編譯器選項，則會定義 [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) 。 否則為未定義。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(:::no-loc(__CLR_VER):::);
    }
    ```

- `:::no-loc(_CONTROL_FLOW_GUARD):::`已設定[ **`/guard:cf`** （啟用控制流程防護）](../build/reference/guard-enable-control-flow-guard.md)編譯器選項時，定義為1。 否則為未定義。

- `:::no-loc(__COUNTER__):::`展開為從0開始的整數常值。 每次在原始程式檔或原始程式檔的內含標頭中使用時，此值會遞增1。 `:::no-loc(__COUNTER__):::`當您使用先行編譯標頭檔時， 會記住其狀態。 這個宏一律會定義。

  這個範例會使用 `:::no-loc(__COUNTER__):::` ，將唯一識別碼指派給相同類型的三個不同物件。 此函 `exampleClass` 式會採用整數做為參數。 在中 `main` ，應用程式會 `exampleClass` 使用 `:::no-loc(__COUNTER__):::` 做為唯一識別碼參數，宣告類型的三個物件：

    ```cpp
    // macro:::no-loc(__COUNTER__):::.cpp
    // Demonstration of :::no-loc(__COUNTER__):::, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro:::no-loc(__COUNTER__):::.cpp
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
        // :::no-loc(__COUNTER__)::: is initially defined as 0
        exampleClass e1(:::no-loc(__COUNTER__):::);

        // On the second reference, :::no-loc(__COUNTER__)::: is now defined as 1
        exampleClass e2(:::no-loc(__COUNTER__):::);

        // :::no-loc(__COUNTER__)::: is now defined as 2
        exampleClass e3(:::no-loc(__COUNTER__):::);

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

- `:::no-loc(__cplusplus_cli):::`在編譯為 c + + 且已設定編譯器選項時，定義為整數常值 200406 [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) 。 否則為未定義。 定義時， `:::no-loc(__cplusplus_cli):::` 會在整個轉譯單位中生效。

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef :::no-loc(__cplusplus_cli):::
          printf("%d\n", :::no-loc(__cplusplus_cli):::);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- `:::no-loc(__cplusplus_winrt):::`在編譯為 c + + 且已設定[ **`/ZW`** （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)編譯器選項時，定義為整數常值201009。 否則為未定義。

- `:::no-loc(_CPPRTTI):::`如果已設定[ **`/GR`** （啟用執行時間類型資訊）](../build/reference/gr-enable-run-time-type-information.md)編譯器選項，則定義為1。 否則為未定義。

- `:::no-loc(_CPPUNWIND):::`如果已設定一或多個[ **`/GX`** （啟用例外狀況處理）](../build/reference/gx-enable-exception-handling.md)、 [ **`/clr`** （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)或[ **`/EH`** （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項，則定義為1。 否則為未定義。

- `:::no-loc(_DEBUG):::`當 [**`/LDd`**](../build/reference/md-mt-ld-use-run-time-library.md) [**`/MDd`**](../build/reference/md-mt-ld-use-run-time-library.md) 已設定、或編譯器選項時，定義為 1 [**`/MTd`**](../build/reference/md-mt-ld-use-run-time-library.md) 。 否則為未定義。

- `:::no-loc(_DLL):::`當 [**`/MD`**](../build/reference/md-mt-ld-use-run-time-library.md) [**`/MDd`**](../build/reference/md-mt-ld-use-run-time-library.md) 設定或（多執行緒 DLL）編譯器選項時，定義為1。 否則為未定義。

- `:::no-loc(__FUNCDNAME__):::`定義為字串常值，其中包含封入函式的[裝飾名稱](../build/reference/decorated-names.md)。 宏只會在函式內定義。 `:::no-loc(__FUNCDNAME__):::`如果您使用 [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或編譯器選項，則不會展開宏 [**`/P`**](../build/reference/p-preprocess-to-a-file.md) 。

   這個範例會使用 `:::no-loc(__FUNCDNAME__):::` 、 `:::no-loc(__FUNCSIG__):::` 和 `:::no-loc(__FUNCTION__):::` 宏來顯示函式資訊。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- `:::no-loc(__FUNCSIG__):::`定義為字串常值，其中包含封入函式的簽章。 宏只會在函式內定義。 `:::no-loc(__FUNCSIG__):::`如果您使用 [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或編譯器選項，則不會展開宏 [**`/P`**](../build/reference/p-preprocess-to-a-file.md) 。 針對64位目標進行編譯時，預設的呼叫慣例為 **`__cdecl`** 。 如需用法的範例，請參閱 `:::no-loc(__FUNCDNAME__):::` 宏。

- `:::no-loc(__FUNCTION__):::`定義為字串常值，其中包含封入函式的未裝飾名稱稱。 宏只會在函式內定義。 `:::no-loc(__FUNCTION__):::`如果您使用 [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或編譯器選項，則不會展開宏 [**`/P`**](../build/reference/p-preprocess-to-a-file.md) 。 如需用法的範例，請參閱 `:::no-loc(__FUNCDNAME__):::` 宏。

- `:::no-loc(_INTEGRAL_MAX_BITS):::`定義為整數常值64，非向量整數類型的大小上限（以位為單位）。 這個宏一律會定義。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", :::no-loc(_INTEGRAL_MAX_BITS):::);
   }
   ```

- `__INTELLISENSE__`在 Visual Studio IDE 中的 IntelliSense 編譯器傳遞期間定義為1。 否則為未定義。 您可以使用這個宏來保護 IntelliSense 編譯器不了解的程式碼，或使用它來切換組建和 IntelliSense 編譯器。 如需詳細資訊，請參閱[IntelliSense 緩慢的疑難排解秘訣](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/)。

- `:::no-loc(_ISO_VOLATILE):::`如果已設定編譯器選項，則定義為 1 [**`/volatile:iso`**](../build/reference/volatile-volatile-keyword-interpretation.md) 。 否則為未定義。

- `:::no-loc(_KERNEL_MODE):::`如果已設定[ **`/kernel`** （建立核心模式二進位）](../build/reference/kernel-create-kernel-mode-binary.md)編譯器選項，則定義為1。 否則為未定義。

- `:::no-loc(_M_AMD64):::`針對以 x64 處理器為目標的編譯，定義為整數常值100。 否則為未定義。

- `:::no-loc(_M_ARM):::`定義為以 ARM 處理器為目標之編譯的整數常值7。 否則為未定義。

- `:::no-loc(_M_ARM_ARMV7VE):::`當 [**`/arch:ARMv7VE`**](../build/reference/arch-arm.md) 編譯器選項設定為以 ARM 處理器為目標的編譯時，定義為1。 否則為未定義。

- `:::no-loc(_M_ARM_FP):::`定義為整數常值，表示為 [**`/arch`**](../build/reference/arch-arm.md) ARM 處理器目標設定的編譯器選項。 否則為未定義。

  - 如果未指定 arm 選項，則為範圍30-39 中的值 **`/arch`** ，表示已設定 arm 的預設架構（ `VFPv3` ）。

  - 如果已設定，則為範圍40-49 中的值 **`/arch:VFPv4`** 。

  - 如需詳細資訊，請參閱[ **`/arch`** （ARM）](../build/reference/arch-arm.md)。

- `:::no-loc(_M_ARM64):::`定義為1，用於以64位 ARM 處理器為目標的編譯。 否則為未定義。

- `:::no-loc(_M_CEE):::`定義為001，如果已設定任何[ **`/clr`** （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。 否則為未定義。

- `:::no-loc(_M_CEE_PURE):::`從 Visual Studio 2015 開始淘汰。 如果已設定編譯器選項，則定義為 001 [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) 。 否則為未定義。

- `:::no-loc(_M_CEE_SAFE):::`從 Visual Studio 2015 開始淘汰。 如果已設定編譯器選項，則定義為 001 [**`/clr:safe`**](../build/reference/clr-common-language-runtime-compilation.md) 。 否則為未定義。

- `:::no-loc(_M_FP_EXCEPT):::`如果 [**`/fp:except`**](../build/reference/fp-specify-floating-point-behavior.md) 已設定或編譯器選項，則定義為 1 [**`/fp:strict`**](../build/reference/fp-specify-floating-point-behavior.md) 。 否則為未定義。

- `:::no-loc(_M_FP_FAST):::`如果已設定編譯器選項，則定義為 1 [**`/fp:fast`**](../build/reference/fp-specify-floating-point-behavior.md) 。 否則為未定義。

- `:::no-loc(_M_FP_PRECISE):::`如果已設定編譯器選項，則定義為 1 [**`/fp:precise`**](../build/reference/fp-specify-floating-point-behavior.md) 。 否則為未定義。

- `:::no-loc(_M_FP_STRICT):::`如果已設定編譯器選項，則定義為 1 [**`/fp:strict`**](../build/reference/fp-specify-floating-point-behavior.md) 。 否則為未定義。

- `:::no-loc(_M_IX86):::`定義為以 x86 處理器為目標之編譯的整數常值600。 未針對 x64 或 ARM 編譯目標定義此宏。

- `:::no-loc(_M_IX86_FP):::`定義為整數常值，表示 [**`/arch`**](../build/reference/arch-arm.md) 已設定的編譯器選項，或預設值。 當編譯目標是 x86 處理器時，一律會定義此宏。 否則為未定義。 定義時，其值為：

  - 如果 `/arch:IA32` 已設定編譯器選項，則為0。

  - 如果 `/arch:SSE` 已設定編譯器選項，則為1。

  - 如果 `/arch:SSE2` `/arch:AVX` 已設定、、 `/arch:AVX2` 或 `/arch:AVX512` 編譯器選項，則為2。 如果未指定編譯器選項，則此值為預設值 `/arch` 。 當 `/arch:AVX` 指定時， `:::no-loc(__AVX__):::` 也會定義宏。 當 `/arch:AVX2` 指定時， `:::no-loc(__AVX__):::` 和 `:::no-loc(__AVX2__):::` 也會同時定義。 當 `/arch:AVX512` 指定時， `:::no-loc(__AVX__):::` 、 `:::no-loc(__AVX2__):::` 、 `:::no-loc(__AVX512BW__):::` 、 `:::no-loc(__AVX512CD__):::` 、 `:::no-loc(__AVX512DQ__):::` 、 `:::no-loc(__AVX512F__):::` 和 `:::no-loc(__AVX512VL__):::` 也會一併定義。

  - 如需詳細資訊，請參閱[ **`/arch`** （x86）](../build/reference/arch-x86.md)。

- `:::no-loc(_M_X64):::`針對以 x64 處理器為目標的編譯，定義為整數常值100。 否則為未定義。

- `:::no-loc(_MANAGED):::`設定編譯器選項時，定義為 1 [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) 。 否則為未定義。

- `:::no-loc(_MSC_BUILD):::`定義為整數常值，其中包含編譯器版本號碼的修訂編號元素。 修訂編號是句號分隔版本號碼的第四個元素。 例如，如果 Microsoft C/c + + 編譯器的版本號碼是15.00.20706.01，則 `:::no-loc(_MSC_BUILD):::` 宏會評估為1。 這個宏一律會定義。

- `:::no-loc(_MSC_EXTENSIONS):::`如果設定了預設的[ **`/Ze`** （啟用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md)編譯器選項，則定義為1。 否則為未定義。

- `:::no-loc(_MSC_FULL_VER):::`定義為整數常值，用來編碼編譯器版本號碼的主要、次要和組建編號元素。 主要數位是句號分隔版本號碼的第一個元素，次要編號是第二個元素，而組建編號是第三個元素。 例如，如果 Microsoft C/c + + 編譯器的版本號碼是15.00.20706.01，則 `:::no-loc(_MSC_FULL_VER):::` 宏會評估為150020706。 `cl /?`在命令列中輸入，以查看編譯器的版本號碼。 這個宏一律會定義。

- `:::no-loc(_MSC_VER):::`定義為整數常值，用來編碼編譯器版本號碼的主要和次要數位元素。 主要數位是句號分隔版本號碼的第一個元素，次要數位則是第二個元素。 例如，如果 Microsoft C/c + + 編譯器的版本號碼是17.00.51106.1，則 `:::no-loc(_MSC_VER):::` 宏會評估為1700。 `cl /?`在命令列中輸入，以查看編譯器的版本號碼。 這個宏一律會定義。

   | Visual Studio 版本 | `:::no-loc(_MSC_VER):::` |
   |--|--|
   | Visual Studio 6.0 | 1200 |
   | Visual Studio .NET 2002 （7.0） | 1300 |
   | Visual Studio .NET 2003 （7.1） | 1310 |
   | Visual Studio 2005 （8.0） | 1400 |
   | Visual Studio 2008 （9.0） | 1500 |
   | Visual Studio 2010 （10.0） | 1600 |
   | Visual Studio 2012 （11.0） | 1700 |
   | Visual Studio 2013 （12.0） | 1800 |
   | Visual Studio 2015 （14.0） | 1900 |
   | Visual Studio 2017 RTW （15.0） | 1910 |
   | Visual Studio 2017 15.3 版 | 1911 |
   | Visual Studio 2017 15.5 版 | 1912 |
   | Visual Studio 2017 15.6 版 | 1913 |
   | Visual Studio 2017 15.7 版 | 1914 |
   | Visual Studio 2017 15.8 版 | 1915 |
   | Visual Studio 2017 15.9 版 | 1916 |
   | Visual Studio 2019 RTW （16.0） | 1920 |
   | Visual Studio 2019 16.1 版 | 1921 |
   | Visual Studio 2019 16.2 版 | 1922 |
   | Visual Studio 2019 16.3 版 | 1923 |
   |  Visual Studio 2019 16.4 版 | 1924 |
   | Visual Studio 2019 16.5 版 | 1925 |
   | Visual Studio 2019 16.6 版 | 1926 |
   | Visual Studio 2019 16.7 版 | 1927 |

   若要在指定的 Visual Studio 版本或之後測試編譯器版本或更新，請使用 `>=` 運算子。 您可以在條件指示詞中使用它來與 `:::no-loc(_MSC_VER):::` 該已知版本進行比較。 如果您有多個相互獨立的版本要進行比較，請依照版本號碼的遞減順序來排序您的比較。 例如，此程式碼會檢查 Visual Studio 2017 和更新版本中所發行的編譯器。 接下來，它會檢查 Visual Studio 2015 之後或之後發行的編譯器。 然後，它會檢查 Visual Studio 2015 之前發行的所有編譯器：

   ```cpp
   #if :::no-loc(_MSC_VER)::: >= 1910
   // . . .
   #elif :::no-loc(_MSC_VER)::: >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   如需詳細資訊，請參閱 Microsoft c + + 小組 Blog 中的[Visual C++ 編譯器版本](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/)。

- `:::no-loc(_MSVC_LANG):::`定義為整數常值，指定編譯器的目標 c + + 語言標準。 它只會在編譯為 c + + 的程式碼中設定。 宏是預設201402L 的整數常值，或當 [**`/std:c++14`**](../build/reference/std-specify-language-standard-version.md) 指定編譯器選項時。 如果指定編譯器選項，宏會設定為 201703L [**`/std:c++17`**](../build/reference/std-specify-language-standard-version.md) 。 當指定選項時，它會設定為較高、未指定的值 [**`/std:c++latest`**](../build/reference/std-specify-language-standard-version.md) 。 否則，宏會是未定義的。 `:::no-loc(_MSVC_LANG):::`從 Visual Studio 2015 Update 3 開始提供宏和[ **`/std`** （指定語言標準版本）](../build/reference/std-specify-language-standard-version.md)編譯器選項。

- `:::no-loc(__MSVC_RUNTIME_CHECKS):::`當設定其中一個編譯器選項時，定義為 1 [**`/RTC`**](../build/reference/rtc-run-time-error-checks.md) 。 否則為未定義。

- `_MSVC_TRADITIONAL`設定預處理器一致性模式編譯器選項時，定義為 0 [**`/experimental:preprocessor`**](../build/reference/experimental-preprocessor.md) 。 預設定義為1，或 [**`/experimental:preprocessor-`**](../build/reference/experimental-preprocessor.md) 設定編譯器選項時，表示正在使用傳統預處理器。 `_MSVC_TRADITIONAL`從 Visual Studio 2017 版15.8 開始，提供宏和[ **`/experimental:preprocessor`** （啟用預處理器一致性模式）](../build/reference/experimental-preprocessor.md)編譯器選項。

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- `:::no-loc(_MT):::`指定[ **`/MD`** 或 **`/MDd`** （多執行緒 DLL）](../build/reference/md-mt-ld-use-run-time-library.md)或[ **`/MT`** 或 **`/MTd`** （多執行緒）](../build/reference/md-mt-ld-use-run-time-library.md)時，定義為1。 否則為未定義。

- `:::no-loc(_NATIVE_WCHAR_T_DEFINED):::`設定編譯器選項時，定義為 1 [**`/Zc:wchar_t`**](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 。 否則為未定義。

- `:::no-loc(_OPENMP):::`如果已設定[ **`/openmp`** （啟用 OpenMP 2.0 支援）](../build/reference/openmp-enable-openmp-2-0-support.md)編譯器選項，則定義為整數常值200203。 此值代表 MSVC 所實作為 OpenMP 規格的日期。 否則為未定義。

   ```cpp
   // :::no-loc(_OPENMP):::_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", :::no-loc(_OPENMP):::);
   }
   ```

- `:::no-loc(_PREFAST_):::`設定編譯器選項時，定義為 1 [**`/analyze`**](../build/reference/analyze-code-analysis.md) 。 否則為未定義。

- `:::no-loc(__TIMESTAMP__):::`定義為字串常值，其中包含上次修改目前原始程式檔的日期和時間，其格式為 CRT 函式所傳回的縮寫、常數長度表單， [`asctime`](../c-runtime-library/reference/asctime-wasctime.md) 例如 `Fri 19 Aug 13:32:58 2016` 。 這個宏一律會定義。

- `:::no-loc(_VC_NODEFAULTLIB):::`設定為[ **`/Zl`** （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md)編譯器選項時，定義為1。 否則為未定義。

- `:::no-loc(_WCHAR_T_DEFINED):::`設定預設編譯器選項時，定義為 1 [**`/Zc:wchar_t`**](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 。 已 `:::no-loc(_WCHAR_T_DEFINED):::` 定義宏，但如果已設定編譯器選項，則不會有任何值 **`/Zc:wchar_t-`** ，而且 **`wchar_t`** 會定義在專案所包含的系統標頭檔中。 否則為未定義。

- `:::no-loc(_WIN32):::`當編譯目標為32位 ARM、64位 ARM、x86 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(_WIN64):::`當編譯目標為64位 ARM 或 x64 時，定義為1。 否則為未定義。

- `:::no-loc(_WINRT_DLL):::`編譯為 c + + 並同時設定[ **`/ZW`** （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)和[ **`/LD`** 或 **`/LDd`** ](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項時，定義為1。 否則為未定義。

識別 ATL 或 MFC 程式庫版本的預處理器宏不是由編譯器預先定義的。 ATL 和 MFC 程式庫標頭會在內部定義這些版本宏。 在包含必要標頭之前所做的預處理器指示詞中，它們是未定義的。

- `:::no-loc(_ATL_VER):::`在中定義 \<atldef.h> 為編碼 ATL 版本號碼的整數常值。

- `:::no-loc(_MFC_VER):::`在中定義 \<afxver_.h> 為以整數常值編碼 MFC 版本號碼。

## <a name="see-also"></a>另請參閱

[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[前置處理器運算子](../preprocessor/preprocessor-operators.md)<br/>
[前置處理器指示詞](../preprocessor/preprocessor-directives.md)
