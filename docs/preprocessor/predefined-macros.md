---
title: 預先定義巨集
ms.custom: update_every_version
ms.date: 10/01/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
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
- __AVX512BW__ macro
- __AVX512CD__ macro
- __AVX512DQ__ macro
- __AVX512F__ macro
- __AVX512VL__ macro
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
ms.openlocfilehash: 57982e32da75aa7f364c51146e50c3d75b4b7710
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163343"
---
# <a name="predefined-macros"></a>預先定義巨集

Microsoft C/C++編譯器（MSVC）會根據語言（C 或C++）、編譯目標和所選擇的編譯器選項，預先定義特定的預處理器宏。

MSVC 支援 ANSI/ISO C99 標準和 ISO c + + 14 和 c + + 17 標準所需的預先定義預處理器宏。 此執行也支援數個 Microsoft 專屬的預處理器宏。 某些宏只會針對特定組建環境或編譯器選項來定義。 除非另有注明，否則宏會定義在整個轉譯單位中，如同已指定為 **/d**編譯器選項引數一樣。 當定義時，在編譯之前，預處理器會將宏擴充為指定的值。 預先定義的宏不接受引數，也無法重新定義。

## <a name="standard-predefined-identifier"></a>標準預先定義的識別碼

編譯器支援 ISO C99 和 ISO c + + 11 所指定的這個預先定義識別碼。

- **&#95; func &#95; &#95;** 封入函式的不合格和未名稱，做為**char**的函數區域**靜態 const**陣列。

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>標準預先定義的宏

編譯器支援 ISO C99 和 ISO c + + 17 標準所指定的這些預先定義宏。

- **&#95;cplusplus &#95;** 當轉譯單位編譯為C++時，定義為整數常值。 否則為未定義。

- **&#95;日期&#95; &#95;** 目前原始檔案的編譯日期。 日期是格式為*Mmm dd yyyy*的常數長度字串常值。 月份名稱*Mmm*與 C 執行時間程式庫（CRT） [asctime](../c-runtime-library/reference/asctime-wasctime.md)函數所產生的縮寫月份名稱相同。 如果值小於10，則日期*dd*的第一個字元是空格。 這個宏一律會定義。

- **&#95;檔案&#95; &#95;** 目前來源檔案的名稱。 檔案會展開至字元字串常值。 **&#95; &#95; &#95;** 若要確保顯示檔案的完整路徑，請使用[/FC （診斷中的原始程式碼檔的完整路徑）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 這個宏一律會定義。

- **&#95;行&#95; &#95;** 定義為目前原始程式檔中的整數行號。 您可以使用 `#line` 指示詞來變更 **&#95; &#95;LINE&#95;** 宏的值。 這個宏一律會定義。

- **&#95; STDC &#95; &#95;** 只有在編譯為 C 且指定[/za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項時，才會定義為1。 否則為未定義。

- **&#95;&#95;如果&#95;實&#95;** 作為裝載的*執行*，則定義為1的 STDC 託管，其中一個支援整個必要的標準程式庫。 否則，定義為0。

- **&#95;&#95;只有&#95;在&#95;** 程式可以有一個以上的執行執行緒，而且編譯為C++時，才將定義為1的 STDCPP 執行緒。 否則為未定義。

- **&#95;時間&#95; &#95;** 前置處理過的轉譯單位的轉譯時間。 時間是格式為*hh： mm： ss*的字元字串常值，與 CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md)函數所傳回的時間相同。 這個宏一律會定義。

## <a name="microsoft-specific-predefined-macros"></a>Microsoft 特有的預先定義宏

MSVC 支援這些額外預先定義的宏。

- **&#95; ATOM &#95; &#95;** 當[/favor： ATOM](../build/reference/favor-optimize-for-architecture-specifics.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX &#95; &#95;** 當[/arch： AVX](../build/reference/arch-x86.md)、 [/arch： AVX2](../build/reference/arch-x86.md)或[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定，而且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX2 &#95; &#95;** 當已設定[/arch： AVX2](../build/reference/arch-x86.md)或[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項，且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX512BW &#95; &#95;** 當[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX512CD &#95; &#95;** 當[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX512DQ &#95; &#95;** 當[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX512F &#95; &#95;** 當[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95; AVX512VL &#95; &#95;** 當[/arch： AVX512](../build/reference/arch-x86.md)編譯器選項已設定且編譯器目標為 x86 或 x64 時，定義為1。 否則為未定義。

- **&#95;如果&#95;** 預設**char**類型不帶正負號，則會將 CHAR 不帶正負號定義為1。 此值是在設定[/j （預設 Char 類型不帶正負號）](../build/reference/j-default-char-type-is-unsigned.md)編譯器選項時所定義。 否則為未定義。

- **&#95;CLR VER &#95; &#95;** 定義為整數常值，表示用來編譯應用程式的 Common Language Runtime （CLR）版本。 此值的編碼格式為 `Mmmbbbbb`，其中 `M` 是執行時間的主要版本，`mm` 是執行時間的次要版本，而 `bbbbb` 是組建編號。 **&#95;&#95;如果&#95;** 已設定[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，則會定義 CLR VER。 否則為未定義。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;設定&#95; &#95;**  [/Guard： cf （啟用控制流程防護）](../build/reference/guard-enable-control-flow-guard.md)編譯器選項時，定義為1的控制流程防護。 否則為未定義。

- **&#95;計數器&#95; &#95;** 展開為從0開始的整數常值。 每次在原始程式檔或原始程式檔的內含標頭中使用時，此值會遞增1。 當您使用先行編譯標頭檔時， **&#95; COUNTER 會記住它的狀態。 &#95; &#95;** 這個宏一律會定義。

  這個範例會使用 `__COUNTER__`，將唯一識別碼指派給相同類型的三個不同物件。 `exampleClass` 的函式會採用整數做為參數。 在 `main`中，應用程式會使用 `__COUNTER__` 做為唯一識別碼參數，宣告 `exampleClass`類型的三個物件：

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

- **&#95;&#95;當&#95;** 編譯為C++且已設定[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項時，cplusplus cli 會定義為整數常值200406。 否則為未定義。 定義時，  **&#95; &#95;cplusplus&#95;cli**會在整個轉譯單位中生效。

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

- **&#95;&#95;當&#95;** 編譯為C++且已設定[/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)編譯器選項時，cplusplus winrt 定義為整數常值201009。 否則為未定義。

- **&#95;CPPRTTI**如果已設定[/GR （啟用執行時間類型資訊）](../build/reference/gr-enable-run-time-type-information.md)編譯器選項，則定義為1。 否則為未定義。

- **&#95;CPPUNWIND**如果已設定一或多個[/gx （啟用例外狀況處理）](../build/reference/gx-enable-exception-handling.md)、 [/Clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)或[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項，則定義為1。 否則為未定義。

- **&#95;DEBUG**設定[/LDd](../build/reference/md-mt-ld-use-run-time-library.md)、 [/MDd](../build/reference/md-mt-ld-use-run-time-library.md)或[/MTd](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項時，定義為1。 否則為未定義。

- 設定[/md](../build/reference/md-mt-ld-use-run-time-library.md)或[/MDd](../build/reference/md-mt-ld-use-run-time-library.md) （多執行緒 DLL）編譯器選項時，定義為1的 DLL。 **&#95;** 否則為未定義。

- **&#95; FUNCDNAME &#95; &#95;** 定義為字串常值，其中包含封入函式的[裝飾名稱](../build/reference/decorated-names.md)。 宏只會在函式內定義。 如果 **&#95; &#95;您&#95;** 使用[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/p](../build/reference/p-preprocess-to-a-file.md)編譯器選項，則不會展開 FUNCDNAME 宏。

   這個範例會使用 `__FUNCDNAME__`、`__FUNCSIG__`和 `__FUNCTION__` 宏來顯示函式資訊。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; FUNCSIG &#95; &#95;** 定義為字串常值，其中包含封入函式的簽章。 宏只會在函式內定義。 如果 **&#95; &#95;您&#95;** 使用[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/p](../build/reference/p-preprocess-to-a-file.md)編譯器選項，則不會展開 FUNCSIG 宏。 針對64位目標進行編譯時，預設會 `__cdecl` 呼叫慣例。 如需用法的範例，請參閱 `__FUNCDNAME__` 宏。

- 函式 **&#95; &#95; &#95;** 定義為字串常值，其中包含封入函式的未裝飾名稱稱。 宏只會在函式內定義。 如果 **&#95; &#95;您&#95;** 使用[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或[/p](../build/reference/p-preprocess-to-a-file.md)編譯器選項，則不會展開函數宏。 如需用法的範例，請參閱 `__FUNCDNAME__` 宏。

- **整數&#95;最&#95;大位&#95;** 定義為整數常值64，非向量整數類型的大小上限（以位為單位）。 這個宏一律會定義。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; INTELLISENSE &#95; &#95;** 在 Visual Studio IDE 中的 IntelliSense 編譯器傳遞期間定義為1。 否則為未定義。 您可以使用這個宏來保護 IntelliSense 編譯器不了解的程式碼，或使用它來切換組建和 IntelliSense 編譯器。 如需詳細資訊，請參閱[IntelliSense 緩慢的疑難排解秘訣](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/)。

- **&#95;如果&#95;** 設定了[/volatile： ISO](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，ISO VOLATILE 會定義為1。 否則為未定義。

- **&#95;如果&#95;** 設定了[/Kernel （建立核心模式二進位）](../build/reference/kernel-create-kernel-mode-binary.md)編譯器選項，則核心模式會定義為1。 否則為未定義。

- **&#95;M&#95;AMD64**針對以 x64 處理器為目標的編譯，定義為整數常值100。 否則為未定義。

- **&#95;M&#95;ARM**定義為以 ARM 處理器為目標之編譯的整數常值7。 否則為未定義。

- **&#95;當&#95;針對&#95;** 以 ARM 處理器為目標的編譯設定[/arch： ARMV7VE](../build/reference/arch-arm.md)編譯器選項時，已將 M ARM ARMV7VE 定義為1。 否則為未定義。

- **&#95;M&#95;ARM&#95;FP**定義為整數常值，表示已針對 ARM 處理器目標設定的[/arch](../build/reference/arch-arm.md)編譯器選項。 否則為未定義。

  - 如果未指定 `/arch` ARM 選項，則為範圍30-39 中的值，表示已設定 ARM 的預設架構（`VFPv3`）。

  - 如果已設定 `/arch:VFPv4`，則為範圍40-49 中的值。

  - 如需詳細資訊，請參閱[/arch （ARM）](../build/reference/arch-arm.md)。

- **&#95;M&#95;ARM64**定義為1，用於以64位 ARM 處理器為目標的編譯。 否則為未定義。

- **&#95;如果&#95;** 設定了任何[/Clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，則會將 M 產生 cee 定義為001。 否則為未定義。

- **M&#95;產生 CEE&#95;純粹&#95;** 從 Visual Studio 2015 開始淘汰。 如果已設定[/clr： pure](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，則定義為001。 否則為未定義。

- **M&#95;產生 CEE&#95;SAFE &#95;** 從 Visual Studio 2015 開始淘汰。 如果已設定[/clr： safe](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，則定義為001。 否則為未定義。

- **&#95;如果&#95;已&#95;** 設定[/fp： EXCEPT](../build/reference/fp-specify-floating-point-behavior.md)或[/Fp： strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項，則除了定義為1以外，M FP 除外。 否則為未定義。

- **&#95;如果&#95;已&#95;** 設定[/fp： fast](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項，則會將 M FP FAST 定義為1。 否則為未定義。

- **&#95;如果&#95;已&#95;** 設定[/fp：精確](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項，則會將 M FP 精確定義為1。 否則為未定義。

- **&#95;如果&#95;已&#95;** 設定[/fp： strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項，則會將 M FP STRICT 定義為1。 否則為未定義。

- **&#95;M&#95;IX86**定義為以 x86 處理器為目標之編譯的整數常值600。 未針對 x64 或 ARM 編譯目標定義此宏。

- **&#95;M&#95;IX86&#95;FP**定義為整數常值，表示已設定的[/arch](../build/reference/arch-arm.md)編譯器選項，或預設值。 當編譯目標是 x86 處理器時，一律會定義此宏。 否則為未定義。 定義時，其值為：

  - 如果已設定 `/arch:IA32` 編譯器選項，則為0。

  - 如果已設定 `/arch:SSE` 編譯器選項，則為1。

  - 如果已設定 `/arch:SSE2`、`/arch:AVX`、`/arch:AVX2`或 `/arch:AVX512` 編譯器選項，則為2。 如果未指定 `/arch` 編譯器選項，則此值為預設值。 當指定 `/arch:AVX` 時，也會定義宏 **&#95; &#95;AVX&#95;** 。 當指定 `/arch:AVX2` 時， **&#95; &#95; &#95;** 也會定義 AVX 和 **&#95; &#95;AVX2&#95;** 。 當指定 `/arch:AVX512` 時，  **&#95; &#95; &#95;** 也會定義 AVX、  **&#95; &#95;AVX2&#95;** 、  **&#95; &#95;AVX512BW&#95;** 、  **&#95; &#95;AVX512CD&#95;** 、 **&#95;AVX512DQ、 &#95; &#95;** **AVX512F &#95;和&#95; AVX512VL。 &#95;**  **&#95; &#95; &#95;**

  - 如需詳細資訊，請參閱 [/arch (x86)](../build/reference/arch-x86.md)。

- **&#95;M&#95;X64**針對以 x64 處理器為目標的編譯，定義為整數常值100。 否則為未定義。

- **&#95;受控**設定[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項時，定義為1。 否則為未定義。

- **&#95;MSC&#95;組建**定義為整數常值，其中包含編譯器版本號碼的修訂編號元素。 修訂編號是句號分隔版本號碼的第四個元素。 例如，如果 Microsoft C/C++編譯器的版本號碼是15.00.20706.01，則 **&#95;services.msc&#95;組建**宏會評估為1。 這個宏一律會定義。

- **&#95;如果&#95;** 已設定預設的[/Ze （啟用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md)編譯器選項，則定義為1的 MSC 延伸模組。 否則為未定義。

- **MSC&#95;完整&#95;版&#95;** 定義為整數常值，用來編碼編譯器版本號碼的主要、次要和組建編號元素。 主要數位是句號分隔版本號碼的第一個元素，次要編號是第二個元素，而組建編號是第三個元素。 例如，如果 MicrosoftC++ C/編譯器的版本號碼是15.00.20706.01，則 **&#95;services.msc&#95;FULL&#95;VER**宏會評估為150020706。 在命令列中輸入 `cl /?`，以查看編譯器的版本號碼。 這個宏一律會定義。

- **&#95;SERVICES.MSC&#95;** 版本定義為整數常值，用來編碼編譯器版本號碼的主要和次要數位元素。 主要數位是句號分隔版本號碼的第一個元素，次要數位則是第二個元素。 例如，如果 Microsoft C/C++編譯器的版本號碼是17.00.51106.1，則 **&#95;services.msc&#95;VER**宏會評估為1700。 在命令列中輸入 `cl /?`，以查看編譯器的版本號碼。 這個宏一律會定義。

   |Visual Studio 版本|**&#95;SERVICES.MSC&#95;版本**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 （7.0）|1300|
   |Visual Studio .NET 2003 （7.1）|1310|
   |Visual Studio 2005 （8.0）|1400|
   |Visual Studio 2008 （9.0）|1500|
   |Visual Studio 2010 （10.0）|1600|
   |Visual Studio 2012 （11.0）|1700|
   |Visual Studio 2013 （12.0）|1800|
   |Visual Studio 2015 （14.0）|1900|
   |Visual Studio 2017 RTW （15.0）|1910|
   |Visual Studio 2017 15.3 版|1911|
   |Visual Studio 2017 15.5 版|1912|
   |Visual Studio 2017 15.6 版|1913|
   |Visual Studio 2017 15.7 版|1914|
   |Visual Studio 2017 15.8 版|1915|
   |Visual Studio 2017 15.9 版|1916|
   |Visual Studio 2019 RTW （16.0）|1920|
   |Visual Studio 2019 16.1 版|1921|
   |Visual Studio 2019 16.2 版|1922|
   |Visual Studio 2019 16.3 版|1923|

   若要在指定的 Visual Studio 版本或之後測試編譯器版本或更新，請使用 **>=** 運算子。 您可以在條件指示詞中使用它，針對該已知版本比較 **&#95;services.msc&#95;VER** 。 如果您有多個相互獨立的版本要進行比較，請依照版本號碼的遞減順序來排序您的比較。 例如，此程式碼會檢查 Visual Studio 2017 和更新版本中所發行的編譯器。 接下來，它會檢查 Visual Studio 2015 之後或之後發行的編譯器。 然後，它會檢查 Visual Studio 2015 之前發行的所有編譯器：

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   如需詳細資訊，請參閱 Microsoft C++小組 Blog 中的[Visual C++編譯器版本](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/)。

- **&#95;MSVC&#95;LANG**定義為整數常值，指定編譯器C++的目的語言標準。 它只會在編譯為C++的程式碼中設定。 宏是預設201402L 的整數常值，或當指定了[/std： c + + 14](../build/reference/std-specify-language-standard-version.md)編譯器選項時。 如果指定了[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)編譯器選項，宏會設定為201703L。 當指定[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)的選項時，它會設定為較高、未指定的值。 否則，宏會是未定義的。 從 Visual Studio 2015 Update 3 開始提供 **&#95;MSVC&#95;LANG**宏和[/std （指定語言標準版本）](../build/reference/std-specify-language-standard-version.md)編譯器選項。

- **&#95;&#95;當&#95;設定&#95;** 了其中一個[/rtc](../build/reference/rtc-run-time-error-checks.md)編譯器選項時，會將 MSVC 執行時間檢查定義為1。 否則為未定義。

- **&#95;當&#95;** 預處理器一致性模式[/experimental：預](../build/reference/experimental-preprocessor.md)處理器編譯器選項已設定時，MSVC 傳統定義為0。 預設定義為1，或在設定[/experimental：預處理器-](../build/reference/experimental-preprocessor.md)編譯器選項時，表示正在使用傳統預處理器。 從 Visual Studio 2017 版15.8 開始，可以使用 **&#95;MSVC&#95;傳統**宏和[/experimental：預處理器（啟用預處理器一致性模式）](../build/reference/experimental-preprocessor.md)編譯器選項。

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- **&#95;MT**指定[/md 或/MDd](../build/reference/md-mt-ld-use-run-time-library.md) （多執行緒 DLL）或[/mt 或/MTd](../build/reference/md-mt-ld-use-run-time-library.md) （多執行緒）時，定義為1。 否則為未定義。

- **&#95;設定&#95; &#95; &#95;**  [/zc： wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項時，定義為1的 NATIVE WCHAR T 定義。 否則為未定義。

- **&#95;OPENMP**如果已設定[/openmp （啟用 openmp 2.0 支援）](../build/reference/openmp-enable-openmp-2-0-support.md)編譯器選項，則定義為整數常值200203。 此值代表 MSVC 所實作為 OpenMP 規格的日期。 否則為未定義。

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;** 設定[/analyze](../build/reference/analyze-code-analysis.md)編譯器選項時，定義為1。 否則為未定義。

- **&#95; &#95;時間&#95;戳**定義為字串常值，其中包含上次修改目前原始程式檔的日期和時間，其格式為 CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md)函數所傳回的縮寫、常數長度表單，例如 `Fri 19 Aug 13:32:58 2016`。 這個宏一律會定義。

- **&#95;設定&#95;** 了[/zl （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md)編譯器選項時，VC NODEFAULTLIB 定義為1。 否則為未定義。

- **&#95;設定&#95;預設&#95;**  [/zc： wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項時，WCHAR T 定義為1。 定義 **&#95;WCHAR&#95;T&#95;定義**宏，但如果設定了 `/Zc:wchar_t-` 編譯器選項，則沒有任何值，而且**wchar_t**定義于專案中所包含的系統標頭檔中。 否則為未定義。

- **&#95;WIN32**當編譯目標為32位 ARM、64位 ARM、x86 或 x64 時，定義為1。 否則為未定義。

- **&#95;WIN64**當編譯目標為64位 ARM 或 x64 時，定義為1。 否則為未定義。

- **&#95;&#95;** 在編譯C++為時，WINRT DLL 定義為1，同時設定[/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md)和[/ld 或/LDd](../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項。 否則為未定義。

識別 ATL 或 MFC 程式庫版本的預處理器宏不是由編譯器預先定義的。 ATL 和 MFC 程式庫標頭會在內部定義這些版本宏。 在包含必要標頭之前所做的預處理器指示詞中，它們是未定義的。

- **&#95;ATL&#95;VER**定義于 \<atldef 中，> 為編碼 ATL 版本號碼的整數常值。

- **&#95;MFC&#95;VER**在 \<> afxver_ 中定義為編碼 MFC 版本號碼的整數常值。

## <a name="see-also"></a>請參閱

[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[預處理器運算子](../preprocessor/preprocessor-operators.md)<br/>
[預處理器指示詞](../preprocessor/preprocessor-directives.md)
