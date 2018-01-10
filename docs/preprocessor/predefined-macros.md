---
title: "預先定義巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "75"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86905a879abe9b81302a8f196e200c1d0c227bb7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-macros"></a>預先定義的巨集

Visual c + + 編譯器預先定義了特定的前置處理器巨集，根據語言 （C 或 c + +）、 編譯目標，以及選擇的編譯器選項。

Visual c + + 支援需要預先定義前置處理器巨集的 ANSI/ISO C99 標準與 ISO C + + 14 標準所指定。 實作也支援數個多個 Microsoft 專有前置處理器巨集。 定義一些巨集只對特定的建置環境或編譯器選項。 若為已指定為除非另有說明，巨集會定義整個轉譯單位**/D**編譯器選項引數。 定義時，巨集就是由編譯前前置處理器展開為指定的值。 預先定義的巨集不接受引數，並不能重新定義。

## <a name="standard-predefined-identifier"></a>標準預先定義的識別項

編譯器支援由 ISO C99 和 ISO C + + 11 指定這個預先定義的識別項。

- **&#95; &#95; func &#95; &#95;**做為函式本機封入函式不合格及未修飾名稱`static const`陣列`char`。

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>標準的預先定義巨集

編譯器支援這些 ISO C99 與 ISO C + + 17 標準所指定的預先定義巨集。

- **&#95; &#95; cplusplus**轉譯單位就會編譯為 c + + 時定義為整數常值。 否則為未定義。

- **&#95; &#95; 日期 #95; &#95;**目前的原始程式檔的編譯日期。 日期是固定長度字串常值格式的*Mmm dd yyyy*。 月份名稱*Mmm*是中的縮寫的月份名稱相同的 C 執行階段程式庫產生的日期[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式。 日期的第一個字元*dd*是一個空格，如果值低於 10。 一律定義此巨集。

- **&#95; &#95;檔案 #95; &#95;**目前的原始程式檔的名稱。 **&#95; &#95;檔案 #95; &#95;**展開字元字串常值。 若要確保顯示檔案的完整路徑，使用[/FC （完整路徑的原始程式碼檔中診斷）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 一律定義此巨集。

- **&#95; &#95;資料行 &#95; #95;**定義為整數的行號，在目前的原始程式檔中。 值**&#95; &#95;資料行 &#95; #95;**巨集可以透過變更`#line`指示詞。 一律定義此巨集。

- **&#95; &#95;STDC #95; &#95;**定義為 1，只有當編譯為 C，而且如果[/Za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項已指定。 否則為未定義。

- **&#95; &#95;STDC &#95;裝載 &#95; &#95;**定義為 1，如果實作是*裝載實作*，支援整個必要的標準程式庫。 否則，定義為 0。

- **&#95; &#95;STDCPP &#95;執行緒 #95; &#95;**定義為 1，如果且只有一個程式可以擁有多個執行的執行緒，且編譯為 c + +。 否則為未定義。

- **&#95; &#95;時間 &#95; &#95;**轉譯的前置處理過的轉譯單位的時間。 時間是字元字串常值格式的*hh: mm:*，C 執行階段程式庫所傳回的時間相同[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式。 一律定義此巨集。

## <a name="microsoft-specific-predefined-macros"></a>Microsoft 專有的預先定義巨集

Microsoft Visual c + + 支援這些額外的預先定義巨集。

- **&#95; &#95;ATOM &#95; &#95;**定義為 1 時[/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md)編譯器選項設定，且編譯器目標為 x86 或 x64。 否則為未定義。

- **&#95; &#95;AVX #95; &#95;**定義為 1 時[/arch: avx](../build/reference/arch-x86.md)或[/arch: avx2](../build/reference/arch-x86.md)編譯器選項會設定，而且編譯器目標為 x86 或 x64。 否則為未定義。

- **&#95; &#95;AVX&#2;95; &#95;**定義為 1 時[/arch: avx2](../build/reference/arch-x86.md)編譯器選項設定，且編譯器目標為 x86 或 x64。 否則為未定義。

- **&#95;CHAR &#95;不帶正負號**定義為 1，否則預設`char`類型是不帶正負號。 這個設定時[/J (預設 char 類型為 unsigned)](../build/reference/j-default-char-type-is-unsigned.md)編譯器選項設定。 否則為未定義。

- **&#95; &#95;Clr&#95;VER**定義為整數常值，表示已編譯的應用程式時使用的 common language runtime 版本。 值編碼格式`Mmmbbbbb`，其中`M`是由執行階段的主要版本`mm`是由執行階段的次要版本和`bbbbb`是組建編號。 **&#95; &#95;Clr&#95;VER**如果定義[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;控制與 #95;流程 &#95;保護**定義為 1 時[/guard: cf （啟用控制流程防護）](../build/reference/guard-enable-control-flow-guard.md)編譯器選項設定。 否則為未定義。

- **&#95; &#95;計數器 #95; &#95;**展開為整數常值從 0 開始，並且每次原始程式檔中使用時遞增 1，或包含原始程式檔的標頭。 **&#95; &#95;計數器 #95; &#95;**會記住其狀態，當您使用先行編譯標頭。 一律定義此巨集。

  這個範例會使用`__COUNTER__`將三個不同的物件相同類型的唯一識別碼。 `exampleClass`建構函式接受整數做為參數。 在`main`，應用程式會宣告三個物件的型別`exampleClass`，並使用`__COUNTER__`做為唯一識別項參數：

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

- **（& s) #95; &#95; cplusplus &#95; cli**定義為整數常值 200406 編譯為 c + + 和[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。 定義時， **&#95; &#95; cplusplus &#95; cli**整個轉譯單位就是作用中。

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

- **（& s) #95; &#95; cplusplus &#95; winrt**定義為整數常值 201009 編譯為 c + + 和[/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)編譯器選項設定。 否則為未定義。

- **&#95;CPPRTTI**定義為 1，否則[/GR （啟用執行階段類型資訊）](../build/reference/gr-enable-run-time-type-information.md)編譯器選項設定。 否則為未定義。

- **&#95;CPPUNWIND**定義為 1，如果一或多個[/GX （啟用例外狀況處理）](../build/reference/gx-enable-exception-handling.md)， [/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)，或[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項設定。 否則為未定義。

- **&#95; 偵錯**定義為 1 時[/LDd](../build/reference/md-mt-ld-use-run-time-library.md)， [/MDd](../build/reference/md-mt-ld-use-run-time-library.md)，或[/MTd](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項設定。 否則為未定義。

- **&#95; DLL**定義為 1 時[/MD](../build/reference/md-mt-ld-use-run-time-library.md)或[/MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded DLL) 編譯器選項設定。 否則為未定義。

- **&#95; &#95;FUNCDNAME #95; &#95;**定義為字串常值包含[裝飾名稱](../build/reference/decorated-names.md)的封入函式。 巨集只能在函式定義。 **&#95; &#95;FUNCDNAME #95; &#95;**如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。

   這個範例會使用`__FUNCDNAME__`， `__FUNCSIG__`，和`__FUNCTION__`巨集來顯示函式資訊。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; &#95;FUNCSIG #95; &#95;**定義為字串常值，其中包含封入函式的簽章。 巨集只能在函式定義。 **&#95; &#95;FUNCSIG #95; &#95;**如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。 當針對 64 位元目標編譯時，呼叫慣例是`__cdecl`預設。 如需使用方式的範例，請參閱`__FUNCDNAME__`巨集。

- **&#95; &#95;函式 &#95; &#95;**定義為包含封入函式的未裝飾的名稱的字串常值。 巨集只能在函式定義。 **&#95; &#95;函式 &#95; &#95;**如果您使用，不會展開巨集[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/P](../build/reference/p-preprocess-to-a-file.md)編譯器選項。 如需使用方式的範例，請參閱`__FUNCDNAME__`巨集。

- **&#95; 整數類資料類型 &#95;最大 &#95;位元**為 64 的整數常值的定義、 非向量的整數類資料類型的大小上限 （以位元為單位）。 一律定義此巨集。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; &#95; &#95; intellisense&#95;**定義為 Visual Studio IDE 中的 IntelliSense 編譯器期間的 1 傳遞。 否則為未定義。 您可以使用這個巨集來保護程式碼，IntelliSense 編譯器不了解，或使用它來組建和 IntelliSense 編譯器之間切換。 如需詳細資訊，請參閱[IntelliSense 緩慢疑難排解秘訣](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/)。

- **&#95; ISO &#95;VOLATILE**定義為 1，否則[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項設定。 否則為未定義。

- **&#95;核心 &#95;模式**定義為 1，否則[/kernel （建立核心模式二進位檔）](../build/reference/kernel-create-kernel-mode-binary.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;AMD64**定義為整數常值數值 100 編譯該目標 x64 處理器。 否則為未定義。

- **&#95;&#95;ARM**定義為整數常值 7 ARM 處理器為目標的編譯。 否則為未定義。

- **&#95;&#95;ARM &#95;ARMV7VE**定義為 1 時[/arch: armv7ve](../build/reference/arch-arm.md)編譯器選項設定為 ARM 處理器為目標的編譯。 否則為未定義。

- **&#95;&#95;ARM &#95;FP**定義為整數常值，指出哪些[/arch](../build/reference/arch-arm.md)編譯器選項已設定，如果編譯目標為 ARM 處理器。 否則為未定義。

  - 在範圍內 30-39，如果沒有**/arch**指定 ARM 選項，指出預設架構 arm 已設定 (`VFPv3`)。

  - 在範圍 40-49 如果**/arch: vfpv4**已設定。

  - 請參閱[/arch (ARM)](../build/reference/arch-arm.md)如需詳細資訊。

- **&#95;&#95;ARM64**定義為 1，對 64 位元 ARM 處理器為目標的編譯。 否則為未定義。

- **&#95;&#95;CEE**任何定義為 001 如果[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;CEE &#95;純**開始，Visual Studio 2015 中的已被取代。 定義為 001 如果[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;CEE &#95;安全**開始，Visual Studio 2015 中的已被取代。 定義為 001 如果[/clr: safe](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;FP &#95;除了**定義為 1，否則[/fp： 除了](../build/reference/fp-specify-floating-point-behavior.md)或[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;FP &#95;快速**定義為 1，否則[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;FP &#95;精確**定義為 1，否則[/fp： 精確](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則為未定義。

- **&#95;&#95;FP &#95;STRICT**定義為 1，否則[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項設定。 否則為未定義。

- **&#95;M &#95; IX86**定義為整數常值的值 600 編譯該目標 x86 處理器。 適用於 x64 或 ARM 編譯目標未定義此巨集。

- **&#95;M &#95; IX86 &#95;FP**定義為整數常值，指出[/arch](../build/reference/arch-arm.md)已設定或預設的編譯器選項。 此巨集一律定義當編譯目標為 x86 處理器。 否則為未定義。 定義時，這個值會是：

  - 0 代表**/arch:IA32**編譯器選項已設定。

  - 1，否則**/arch:SSE**編譯器選項已設定。

  - 2 如果**/arch:SSE2**， **/arch: avx**或**/arch: avx2**編譯器選項已設定。 如果這個值會是預設**/arch**未指定編譯器選項。 當**/arch: avx**指定，則巨集**&#95; &#95;AVX #95; &#95;**也有定義。 當**/arch: avx2**指定，則兩者**&#95; &#95;AVX #95; &#95;**和**&#95; &#95;AVX&#2;95; &#95;**也會定義。

  - 請參閱[/arch (x86)](../build/reference/arch-x86.md)如需詳細資訊。

- **&#95;&#95;X64**定義為整數常值數值 100 編譯該目標 x64 處理器。 否則為未定義。

- **&#95;管理**定義為 1 時[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項設定。 否則為未定義。

- **&#95;MSC &#95;建置**定義為整數常值，其中包含編譯器的版本號碼的修訂編號項目。 修訂編號是句號分隔版本號碼的第四個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01， **&#95;MSC &#95;建置**巨集判斷值為 1。 一律定義此巨集。

- **&#95;MSC &#95;擴充功能**定義為 1，否則[/Ze （啟用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md)編譯器選項會設定，這是預設值。 否則為未定義。

- **&#95;MSC &#95;完整 &#95;VER**定義為整數常值，可以編碼主要、 次要、 和建置編譯器的版本號碼的數字的項目。 主要號碼是句號分隔版本號碼的第一個元素、 次要版本號碼是第二個項目，和組建編號是第三個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01， **&#95;MSC &#95;完整 &#95;VER**巨集判斷值為 150020706。 輸入**cl /？** 在命令列，以檢視編譯器的版本號碼。 一律定義此巨集。

- **&#95;MSC &#95;VER**定義為整數常值，可以編碼編譯器的版本號碼的主要和次要編號項目。 主要號碼是句號分隔版本號碼的第一個元素，而次要號碼是第二個元素。 例如，如果 Visual c + + 編譯器的版本號碼是 17.00.51106.1， **&#95;MSC &#95;VER**巨集判斷值為 1700年。 輸入**cl /？** 在命令列，以檢視編譯器的版本號碼。 一律定義此巨集。

- **&#95;MSVC &#95;LANG**定義為整數常值，指定編譯器為目標的 c + + 語言標準。 當編譯為 c + +，巨集如果是整數常值 201402 [/std:c + + 14](../build/reference/std-specify-language-standard-version.md)編譯器選項設定，或根據預設，它設定為 201703 如果[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)編譯器選項設定;，且設定為較高、 未指定值時[/std:c + + 最新](../build/reference/std-specify-language-standard-version.md)。 否則，巨集未定義。 **&#95;MSVC &#95;LANG**巨集和[/std （指定語言標準版）](../build/reference/std-specify-language-standard-version.md)編譯器選項會從開始使用 Visual Studio 2015 Update 3。

- **&#95; &#95;MSVC &#95;RUNTIME &#95;檢查**定義為當一 1 的[/RTC](../build/reference/rtc-run-time-error-checks.md)編譯器選項設定。 否則為未定義。

- **&#95; MT**定義為 1 時[/MD 或 /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded DLL) 或[/MT 或 /MTd](../build/reference/md-mt-ld-use-run-time-library.md)指定 （多執行緒）。 否則為未定義。

- **&#95;原生 &#95;WCHAR &#95;T &#95; 定義**定義為 1 時[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項設定。 否則為未定義。

- **&#95; OPENMP**定義為整數常值 200203，代表由 Visual c + + 中，實作的 OpenMP 規格的日期，如果[/openmp （啟用 OpenMP 2.0 支援）](../build/reference/openmp-enable-openmp-2-0-support.md)編譯器選項設定。 否則為未定義。

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST &#95;**定義為 1 時[/ 分析](../build/reference/analyze-code-analysis.md)編譯器選項設定。 否則為未定義。

- **&#95; &#95;時間戳記 #95; &#95;**定義為包含的日期和時間的上次修改目前的原始程式檔，在縮寫的固定長度表單 C 執行階段程式庫所傳回的字串常值[asctime](../c-runtime-library/reference/asctime-wasctime.md)函式，例如，`Fri 19 Aug 13:32:58 2016`. 一律定義此巨集。

- **&#95;VC &#95;NODEFAULTLIB**定義為 1 時[/Zl （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md)編譯器選項設定。 否則為未定義。

- **&#95;WCHAR &#95;T &#95; 定義**定義為 1 時，預設值[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項設定。 **&#95;WCHAR &#95;T &#95; 定義**巨集已定義，但是沒有任何值，如果**/Zc:wchar_t-**編譯器選項設定，和`wchar_t`定義包含在您的專案系統標頭檔中。 否則為未定義。

- **&#95;WIN32**定義為 1，當編譯目標為 32 位元 ARM、 64 位元 ARM、 x86、 時或 x 64。 否則為未定義。

- **&#95;WIN64**編譯目標為 64 位元 ARM 或 x64 時定義為 1。 否則為未定義。

- **&#95;WINRT &#95; DLL**定義為 1 時，編譯為 c + +，兩者均[/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)和[/LD 或 /LDd](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項設定。 否則為未定義。

 編譯器不會預先定義前置處理器巨集用來判斷 ATL 或 MFC 程式庫版本。 這些巨集是在程式庫的標頭中定義的所以它們會中未定義前置處理器指示詞再包含必要的標頭。

- **&#95;ATL &#95;VER**中定義\<atldef.h > 做為編碼的 ATL 版本號碼的整數常值。

- **&#95;MFC &#95;VER**中定義\<afxver_.h > 做為編碼 MFC 版本號碼的整數常值。

## <a name="see-also"></a>請參閱

[巨集 （C/c + +）](../preprocessor/macros-c-cpp.md)   
[前置處理器運算子](../preprocessor/preprocessor-operators.md)   
[前置處理器指示詞](../preprocessor/preprocessor-directives.md)
