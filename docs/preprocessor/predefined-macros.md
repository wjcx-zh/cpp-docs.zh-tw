---
title: "預先定義的巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_VER"
  - "__ATOM__"
  - "__AVX__"
  - "__AVX2__"
  - "_CHAR_UNSIGNED"
  - "__CLR_VER"
  - "_CONTROL_FLOW_GUARD"
  - "__COUNTER__"
  - "__cplusplus"
  - "__cplusplus_cli"
  - "__cplusplus_winrt"
  - "_CPPRTTI"
  - "_CPPUNWIND"
  - "__DATE__"
  - "_DEBUG"
  - "_DLL"
  - "__FILE__"
  - "__FUNCDNAME__"
  - "__FUNCSIG__"
  - "__FUNCTION__"
  - "_INTEGRAL_MAX_BITS"
  - "_ISO_VOLATILE"
  - "_KERNEL_MODE"
  - "__LINE__"
  - "_M_AMD64"
  - "_M_ARM"
  - "_M_ARM_ARMV7VE"
  - "_M_ARM_FP"
  - "_M_ARM64"
  - "_M_CEE"
  - "_M_CEE_PURE"
  - "_M_CEE_SAFE"
  - "_M_FP_EXCEPT"
  - "_M_FP_FAST"
  - "_M_FP_PRECISE"
  - "_M_FP_STRICT"
  - "_M_IX86"
  - "_M_IX86_FP"
  - "_M_X64"
  - "_MANAGED"
  - "_MFC_VER"
  - "_MSC_BUILD"
  - "_MSC_EXTENSIONS"
  - "_MSC_FULL_VER"
  - "_MSC_VER"
  - "_MSVC_LANG"
  - "__MSVC_RUNTIME_CHECKS"
  - "_MT"
  - "_NATIVE_WCHAR_T_DEFINED"
  - "_NO_SIZED_DEALLOCATION"
  - "_OPENMP"
  - "_PREFAST_"
  - "_RESUMABLE_FUNCTIONS_SUPPORTED"
  - "_RTC_CONVERSION_CHECKS_ENABLED"
  - "__STDC__"
  - "__STDC_HOSTED__"
  - "__STDCPP_THREADS__"
  - "__TIME__"
  - "__TIMESTAMP__"
  - "__VA_ARGS__"
  - "_VC_NODEFAULTLIB"
  - "_WCHAR_T_DEFINED"
  - "_WIN32"
  - "_WIN64"
  - "_WINRT_DLL"
  - "__func__"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "時間戳記，前置處理器巨集"
  - "cl.exe 編譯器，版本號碼"
  - "版本號碼，C/c + + 編譯器 (cl.exe)"
  - "預先定義的巨集，c + +"
  - "前置處理器，巨集"
  - "預先定義的巨集"
  - "_ATL_VER 巨集"
  - "__ATOM__ 巨集"
  - "__AVX__ 巨集"
  - "__AVX2__ 巨集"
  - "_CHAR_UNSIGNED 巨集"
  - "__CLR_VER 巨集"
  - "_CONTROL_FLOW_GUARD 巨集"
  - "__COUNTER__ 巨集"
  - "__cplusplus 巨集"
  - "__cplusplus_cli 巨集"
  - "__cplusplus_winrt 巨集"
  - "_CPPRTTI 巨集"
  - "_CPPUNWIND 巨集"
  - "__DATE__ 巨集"
  - "_DEBUG 巨集"
  - "_DLL 巨集"
  - "__FILE__ 巨集"
  - "__FUNCDNAME__ 巨集"
  - "__FUNCSIG__ 巨集"
  - "__FUNCTION__ 巨集"
  - "_INTEGRAL_MAX_BITS 巨集"
  - "_ISO_VOLATILE 巨集"
  - "_KERNEL_MODE 巨集"
  - "__LINE__ 巨集"
  - "_M_AMD64 巨集"
  - "_M_ARM 巨集"
  - "_M_ARM_ARMV7VE 巨集"
  - "_M_ARM_FP 巨集"
  - "_M_ARM64 巨集"
  - "_M_CEE 巨集"
  - "_M_CEE_PURE 巨集"
  - "_M_CEE_SAFE 巨集"
  - "_M_FP_EXCEPT 巨集"
  - "_M_FP_FAST 巨集"
  - "_M_FP_PRECISE 巨集"
  - "_M_FP_STRICT 巨集"
  - "_M_IX86 巨集"
  - "_M_IX86_FP 巨集"
  - "_M_X64 巨集"
  - "_MANAGED 巨集"
  - "_MFC_VER 巨集"
  - "_MSC_BUILD 巨集"
  - "_MSC_EXTENSIONS 巨集"
  - "_MSC_FULL_VER 巨集"
  - "_MSC_VER 巨集"
  - "_MSVC_LANG 巨集"
  - "__MSVC_RUNTIME_CHECKS 巨集"
  - "_MT 巨集"
  - "_NATIVE_WCHAR_T_DEFINED 巨集"
  - "_NO_SIZED_DEALLOCATION 巨集"
  - "_OPENMP 巨集"
  - "_PREFAST_ 巨集"
  - "_RESUMABLE_FUNCTIONS_SUPPORTED 巨集"
  - "_RTC_CONVERSION_CHECKS_ENABLED 巨集"
  - "__STDC__ 巨集"
  - "__STDC_HOSTED__ 巨集"
  - "__STDCPP_THREADS__ 巨集"
  - "__TIME__ 巨集"
  - "__TIMESTAMP__ 巨集"
  - "__VA_ARGS__ 巨集"
  - "_VC_NODEFAULTLIB 巨集"
  - "_WCHAR_T_DEFINED 巨集"
  - "_WIN32 巨集"
  - "_WIN64 巨集"
  - "_WINRT_DLL 巨集"
  - "__func__ 識別碼"
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
caps.latest.revision: 75
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 75
---
# 預先定義的巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual c + + 編譯器會預先定義特定的前置處理器巨集，視語言 （C 或 c + +）、 編譯目標，以及選擇的編譯器選項而定。  
  
 Visual c + + 支援需要預先定義前置處理器巨集的 ANSI/ISO C99 標準和 ISO C + + 14 標準所指定。 實作也支援數個多個 Microsoft 專有前置處理器巨集。 只針對特定組建的環境或編譯器選項定義一些巨集。 除非另有說明，巨集定義整個轉譯單位為它們指定為 **/D** 編譯器選項引數。 定義時，巨集就會被編譯前前置處理器展開指定的值。 預先定義的巨集不接受引數，並且不能重新定義。  
  
## <a name="standard-predefined-identifier"></a>標準預先定義的識別項  
 編譯器支援由 ISO C99 和 ISO C + + 11 指定這個預先定義的識別項。  
  
-   **__func\_\_** 不合格的及未修飾的名稱做為函式本機封入函式 `static``const` 陣列 `char`。  
  
    ```cpp  
    void example(){  
        printf("%s\n", __func__);  
    } // prints "example"  
    ```  
  
## <a name="standard-predefined-macros"></a>標準的預先定義巨集  
 編譯器支援下列 ISO C99 和 ISO C + + 14 標準所指定的預先定義巨集。  
  
-   **__cplusplus** 轉譯單位會編譯為 c + + 時定義為整數常值。 否則，未定義。  
  
-   **__DATE\_\_** 目前原始程式檔的編譯日期。 日期是固定長度字串常值格式的 *Mmm dd yyyy*。 月份名稱 *Mmm* 是中的縮寫的月份名稱相同的 C 執行階段程式庫所產生的日期 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 函式。 日期的第一個字元 *dd* 是空格，如果值低於 10。 一律定義這個巨集。  
  
-   **__FILE\_\_** 目前原始程式檔的名稱。 **__FILE\_\_** 展開字元字串常值。 若要確保顯示檔案的完整路徑，使用 [/FC （完整路徑的原始程式檔的診斷）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 一律定義這個巨集。  
  
-   **__LINE\_\_** 定義為目前原始程式檔中的整數行號。 值 **__LINE\_\_** 巨集可以藉由變更 `#line` 指示詞。 一律定義這個巨集。  
  
-   **__STDC\_\_** 定義為 1，只有當編譯為 C 且 [/Za](../build/reference/za-ze-disable-language-extensions.md) 編譯器選項指定。 否則，未定義。  
  
-   **__STDC_HOSTED\_\_** 定義為 1，如果實作是 *裝載實作*, ，可支援整個必要的標準程式庫。 否則，定義為 0。  
  
-   **__STDCPP_THREADS\_\_** 定義為 1，如果且只有一個程式可以擁有多個執行的執行緒，且編譯為 c + +。 否則，未定義。  
  
-   **__TIME\_\_** 轉譯前置處理過的轉譯單位的時間。 時間是字元字串常值格式的 *hh: mm:*, ，C 執行階段程式庫所傳回的時間與相同 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 函式。 一律定義這個巨集。  
  
## <a name="microsoft-specific-predefined-macros"></a>Microsoft 專有的預先定義巨集  
 Microsoft Visual c + + 支援這些其他的預先定義巨集。  
  
-   **__ATOM\_\_** 定義為 1 時 [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) 設定編譯器選項和編譯器目標為 x86 或 x64。 否則，未定義。  
  
-   **__AVX\_\_** 定義為 1 時 [/arch: avx](../build/reference/arch-x86.md) 或 [/arch: avx2](../build/reference/arch-x86.md) 編譯器選項會設定，而且編譯器目標為 x86 或 x64。 否則，未定義。  
  
-   **__AVX2\_\_** 定義為 1 時 [/arch: avx2](../build/reference/arch-x86.md) 設定編譯器選項和編譯器目標為 x86 或 x64。 否則，未定義。  
  
-   **_CHAR_UNSIGNED** 定義為 1，否則預設 `char` 類型是不帶正負號。 這會設定當 [/J (預設 char 類型為 unsigned)](../build/reference/j-default-char-type-is-unsigned.md) 設定編譯器選項。 否則，未定義。  
  
-   **__CLR_VER** 定義為整數常值，表示應用程式編譯時使用 common language runtime 版本。 這個值應該在表單中 `Mmmbbbbb`, ，其中 `M` 是主要版本的執行階段， `mm` 是執行階段的次要版本和 `bbbbb` 是組建編號。 **__CLR_VER** 定義若 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
    ```cpp  
    // clr_ver.cpp  
    // compile with: /clr  
    using namespace System;  
    int main() {  
       Console::WriteLine(__CLR_VER);  
    }  
    ```  
  
-   **_CONTROL_FLOW_GUARD** 定義為 1 時 [/guard:cf （啟用控制流程防護）](../build/reference/guard-enable-control-flow-guard.md) 設定編譯器選項。 否則，未定義。  
  
-   **__COUNTER\_\_** Expands 為整數常值從 0 開始，並且每次原始程式檔中使用時遞增 1，或包含原始程式檔的標頭。 **__COUNTER\_\_** 會記住其狀態，當您使用先行編譯標頭。 一律定義這個巨集。  
  
     這個範例會使用 `__COUNTER__` 指派給三個不同的物件相同類型的唯一識別碼。  `exampleClass` 建構函式接受整數做為參數。 在 `main`, ，應用程式會宣告三個物件的型別 `exampleClass`, ，並使用 `__COUNTER__` 做為唯一識別項參數︰  
  
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
  
-   **__cplusplus_cli** 定義為整數常值 200406 時編譯為 c + + 和 [/clr](../build/reference/clr-common-language-runtime-compilation.md), ，[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md), ，或 [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。 定義時， **__cplusplus_cli** 適用於整個轉譯單位。  
  
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
  
-   **__cplusplus_winrt** 定義為整數常值 201009 時編譯為 c + + 和 [/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_CPPRTTI** 定義為 1，否則 [/GR （啟用執行階段類型資訊）](../build/reference/gr-enable-run-time-type-information.md) 設定編譯器選項。 否則，未定義。  
  
-   **_CPPUNWIND** 定義為 1，如果一或多個 [/GX （啟用例外狀況處理）](../build/reference/gx-enable-exception-handling.md), ，[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md), ，或 [/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md) 編譯器選項設定。 否則，未定義。  
  
-   **_DEBUG** 定義為 1 時 [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), ，[/MDd](../build/reference/md-mt-ld-use-run-time-library.md), ，或 [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) 設定編譯器選項。 否則，未定義。  
  
-   **_DLL** 定義為 1 時 [/MD](../build/reference/md-mt-ld-use-run-time-library.md) 或 [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 設定 (多執行緒 DLL) 編譯器選項。 否則，未定義。  
  
-   **__FUNCDNAME\_\_** 定義為字串常值，其中包含 [裝飾名稱](../build/reference/decorated-names.md) 封入函式。 只出現在函式定義的巨集。  **__FUNCDNAME\_\_** 巨集不會展開，如果您使用 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 編譯器選項。  
  
     這個範例會使用 `__FUNCDNAME__`, ，`__FUNCSIG__`, ，和 `__FUNCTION__` 巨集來顯示函式資訊。  
  
     [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]  
  
-   **__FUNCSIG\_\_** 定義為字串常值，其中包含封入函式的簽章。 只出現在函式定義的巨集。  **__FUNCSIG\_\_** 巨集不會展開，如果您使用 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 編譯器選項。 當針對 64 位元目標編譯時，呼叫慣例是 `__cdecl` 預設。 如需使用方式的範例，請參閱 `__FUNCDNAME__` 巨集。  
  
-   **__FUNCTION\_\_** 定義為包含封入函式的未裝飾的名稱的字串常值。 只出現在函式定義的巨集。  **__FUNCTION\_\_** 巨集不會展開，如果您使用 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 編譯器選項。 如需使用方式的範例，請參閱 `__FUNCDNAME__` 巨集。  
  
-   **_INTEGRAL_MAX_BITS** 為 64 的整數常值的定義、 非向量的整數類資料類型的大小上限 （以位元為單位）。 一律定義這個巨集。  
  
    ```cpp  
    // integral_max_bits.cpp  
    #include <stdio.h>  
    int main() {  
       printf("%d\n", _INTEGRAL_MAX_BITS);  
    }  
    ```  
  
-   **__INTELLISENSE\_\_** 定義為 1，IntelliSense 編譯器期間傳遞 Visual Studio IDE 中。 否則，未定義。 您可以使用這個巨集來保護程式碼 IntelliSense 編譯器不會了解，或使用它來建置和 IntelliSense 編譯器之間切換。 如需詳細資訊，請參閱 [IntelliSense 緩慢疑難排解秘訣](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/)。  
  
-   **_ISO_VOLATILE** 定義為 1，否則 [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_KERNEL_MODE** 定義為 1，否則 [/kernel （建立核心模式二進位檔）](../build/reference/kernel-create-kernel-mode-binary.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_AMD64** 定義為整數常值數值 100 編譯該目標 x64 處理器。 否則，未定義。  
  
-   **_M_ARM** 定義為 ARM 處理器為目標的編譯的整數常值 7。 否則，未定義。  
  
-   **_M_ARM_ARMV7VE** 定義為 1 時 [/arch: armv7ve](../build/reference/arch-arm.md) 對 ARM 處理器為目標的編譯設定編譯器選項。 否則，未定義。  
  
-   **_M_ARM_FP** 定義為整數常值，會指出 [/arch](../build/reference/arch-arm.md) 編譯器選項已設定，如果編譯目標為 ARM 處理器。 否則，未定義。  
  
    -   在範圍內 30-39，如果沒有 **/arch** 指定 ARM 選項，指出預設架構 arm 設定 (`VFPv3`)。  
  
    -   在範圍 40-49 如果 **/arch: vfpv4** 已設定。  
  
    -   請參閱 [/arch (ARM)](../build/reference/arch-arm.md) 如需詳細資訊。  
  
-   **_M_ARM64** 定義為 1，對 64 位元 ARM 處理器為目標的編譯。 否則，未定義。  
  
-   **_M_CEE** 任何定義為 001 如果 [/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_CEE_PURE** 定義為 001 如果 [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_CEE_SAFE** 定義為 001 如果 [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_FP_EXCEPT** 定義為 1，否則 [/fp︰ 除了](../build/reference/fp-specify-floating-point-behavior.md) 或 [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_FP_FAST** 定義為 1，否則 [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_FP_PRECISE** 定義為 1，否則 [/fp︰ 精確](../build/reference/fp-specify-floating-point-behavior.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_FP_STRICT** 定義為 1，否則 [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) 設定編譯器選項。 否則，未定義。  
  
-   **_M_IX86** 定義為整數常值的值 600 編譯該目標 x86 處理器。 X64 或 ARM 編譯目標未定義此巨集。  
  
-   **_M_IX86_FP** 定義為整數常值，指出 [/arch](../build/reference/arch-arm.md) 已設定或預設的編譯器選項。 這個巨集一律定義當編譯目標為 x86 處理器。 否則，未定義。 定義時，這個值會是︰  
  
    -   0 代表 **/arch:IA32** 編譯器選項已設定。  
  
    -   1 則 **/arch:SSE** 編譯器選項已設定。  
  
    -   2 如果 **/arch:SSE2**, ，**/arch: avx** 或 **/arch: avx2** 編譯器選項已設定。 如果此值為預設 **/arch** 未指定編譯器選項。 當 **/arch: avx** 指定，則巨集 **__AVX\_\_** 也會定義。 當 **/arch: avx2** 指定，則兩者 **__AVX\_\_** 和 **__AVX2\_\_** 也會定義。  
  
    -   請參閱 [/arch (x86)](../build/reference/arch-x86.md) 如需詳細資訊。  
  
-   **_M_X64** 定義為整數常值數值 100 編譯該目標 x64 處理器。 否則，未定義。  
  
-   **_MANAGED** 定義為 1 時 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 設定編譯器選項。 否則，未定義。  
  
-   **_MSC_BUILD** 定義為整數常值，其中包含編譯器版本號碼的修訂編號項目。 修訂編號是句號分隔版本號碼的第四個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01， **_MSC_BUILD** 巨集判斷值為 1。 一律定義這個巨集。  
  
-   **_MSC_EXTENSIONS** 定義為 1，否則 [/Ze （啟用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) 編譯器選項會設定，這是預設值。 否則，未定義。  
  
-   **_MSC_FULL_VER** 定義為整數常值，它可將主要、 次要、 和建置編譯器的版本號碼的數字的項目。 主要版本號碼是句號分隔版本號碼的第一個項目、 次要版本號碼是第二個元素，和組建編號是第三個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 15.00.20706.01， **_MSC_FULL_VER** 巨集判斷值為 150020706。 輸入 **cl /？** 在命令列，以檢視編譯器的版本號碼。 一律定義這個巨集。  
  
-   **_MSC_VER** 定義為編譯器版本號碼的主要和次要編號項目會將編碼的整數常值。 主要版本號碼是句號分隔版本號碼的第一個項目和次要版本號碼是第二個項目。 例如，如果 Visual c + + 編譯器的版本號碼是 17.00.51106.1， **_MSC_VER** 巨集判斷值為 1700年。 輸入 **cl /？** 在命令列，以檢視編譯器的版本號碼。 一律定義這個巨集。  
  
-   **_MSVC_LANG** 定義為整數常值，指定目標的編譯器的 c + + 語言標準。 如果巨集時編譯為 c + +，是整數常值 201402 [/std:c + + 14](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 編譯器選項是集，或預設值，而且它是設定為較高時，未指定值時 [/std:c + + 最新](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 設定編譯器選項。 否則，巨集未定義。  **_MSVC_LANG** 巨集和 [/std （指定語言標準版）](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 編譯器選項會從開始使用 Visual Studio 2015 Update 3。  
  
-   **__MSVC_RUNTIME_CHECKS** 定義為 1 時的 [/RTC](../build/reference/rtc-run-time-error-checks.md) 設定編譯器選項。 否則，未定義。  
  
-   **_MT** 定義為 1 時 [/MD 或 /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded DLL) 或 [/MT 或 /MTd](../build/reference/md-mt-ld-use-run-time-library.md) 指定 （多執行緒）。 否則，未定義。  
  
-   **_NATIVE_WCHAR_T_DEFINED** 定義為 1 時 [/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 設定編譯器選項。 否則，未定義。  
  
-   **_OPENMP** 定義為整數常值 200203，表示 Visual c + + 所實作的 OpenMP 規格的日期，如果 [/openmp （啟用 OpenMP 2.0 支援）](../build/reference/openmp-enable-openmp-2-0-support.md) 設定編譯器選項。 否則，未定義。  
  
    ```cpp  
    // _OPENMP_dir.cpp  
    // compile with: /openmp   
    #include <stdio.h>   
    int main() {  
       printf("%d\n", _OPENMP);  
    }  
    ```  
  
-   **_PREFAST\_** 定義為 1 時 [/analyze](../build/reference/analyze-code-analysis.md) 設定編譯器選項。 否則，未定義。  
  
-   **__TIMESTAMP\_\_** 定義為字串常值，其中包含目前的原始程式檔，縮寫的固定長度形式傳回 C 執行階段程式庫的上次修改時間與日期 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 函式，例如 `Fri 19 Aug 13:32:58 2016`。 一律定義這個巨集。  
  
-   **_VC_NODEFAULTLIB** 定義為 1 時 [/Zl （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md) 設定編譯器選項。 否則，未定義。  
  
-   **_WCHAR_T_DEFINED** 定義為 1 時，預設 [/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 設定編譯器選項。  **_WCHAR_T_DEFINED** 巨集已定義，但是沒有任何值，如果 **/Zc:wchar_t-** 設定編譯器選項時，和 `wchar_t` 定義包含在專案中的系統標頭檔中。 否則，未定義。  
  
-   **_WIN32** 定義為 1 時編譯目標為 32 位元 ARM、 64 位元 ARM、 x86，或 x64。 否則，未定義。  
  
-   **_WIN64** 編譯目標為 64 位元 ARM 或 x64 時定義為 1。 否則，未定義。  
  
-   **_WINRT_DLL** 定義為 1 時，會編譯為 c + +，兩者均 [/ZW （Windows 執行階段編譯）](../build/reference/zw-windows-runtime-compilation.md) 和 [/LD 或 /LDd](../build/reference/md-mt-ld-use-run-time-library.md) 編譯器選項設定。 否則，未定義。  
  
 編譯器不會預先定義用來判斷 ATL 或 MFC 程式庫版本的前置處理器巨集。 這些巨集被定義在程式庫標頭，因此它們未定義的前置處理器指示詞中包含必要的標頭之前。  
  
-   **_ATL_VER** \< atldef.h > 中定義為整數常值，可以編碼 ATL 版本號碼。  
  
-   **_MFC_VER** \< afxver_.h > 中定義為整數常值，可以編碼 MFC 版本號碼。  
  
## <a name="see-also"></a>另請參閱  
 [巨集 （C/c + +）](../preprocessor/macros-c-cpp.md)   
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)   
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)