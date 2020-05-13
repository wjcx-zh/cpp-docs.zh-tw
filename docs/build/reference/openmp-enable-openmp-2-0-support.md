---
title: /開啟(開啟 OpenMP 支援)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336198"
---
# <a name="openmp-enable-openmp-support"></a>/開啟(開啟 OpenMP 支援)

使編譯器處理[`#pragma omp`](../../preprocessor/omp.md)指令以支援 OpenMP。

## <a name="syntax"></a>語法

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__實驗__|

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>備註

`#pragma omp`指定[指令](../../parallel/openmp/reference/openmp-directives.md)與[子語](../../parallel/openmp/reference/openmp-clauses.md)。 如果編譯中未指定 **/openmp,** 編譯器將忽略 OpenMP 子句和指令。 即使未指定 **/openmp,** 編譯器也會處理[openMP 函數](../../parallel/openmp/reference/openmp-functions.md)呼叫。

::: moniker range=">= vs-2019"

C++編譯器目前支援 OpenMP 2.0 標準。 然而,Visual Studio 2019 現在也提供 SIMD 功能。 要使用 SIMD,請使用 **/openmp:實驗**選項進行編譯。 此選項支援常用的 OpenMP 功能,以及使用 **/openmp**開關時不可用的其他 OpenMP SIMD 功能。

::: moniker-end

使用 **/openmp**和 **/clr**編譯的應用程式只能在單個應用程式域進程中運行。 不支援多個應用程式域。 也就是說,當運行模組建構函數 ()`.cctor`時,它會檢測進程是否使用 **/openmp**編譯,以及應用是否載入到非預設運行時。 有關詳細資訊,請參閱[應用程式網](../../cpp/appdomain.md)[域 /clr(通用語言執行時編譯)](clr-common-language-runtime-compilation.md)和[混合程式集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。

如果嘗試將使用 **/openmp**和 **/clr**編譯的應用載入非預設應用程式<xref:System.TypeInitializationException>域中, 則異常將引發調試器之外,除`OpenMPWithMultipleAppdomainsException`錯器中將引發異常。

在以下情況下也可以引發這些異常:

- 如果應用程式使用 **/clr**編譯,但使用 **/openmp**編譯,並且載入非預設應用程式域中,其中該過程包括使用 **/openmp**編譯的應用程式。

- 如果將 **/clr**應用傳遞給實用程式,例如[regasm.exe,](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)該實用程式將其目標程式集載入到非預設應用程式域中。

通用語言運行時的代碼訪問安全性在OpenMP區域中不起作用。 如果在並行區域之外應用 CLR 代碼存取安全屬性,則該屬性在並行區域中無效。

Microsoft 不建議您編寫允許部分受信任的調用方的 **/openmp**應用。 不要使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>或任何 CLR 代碼存取安全屬性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開**配置屬性** > **C/C++** > **語言**屬性頁。

1. 修改**OpenMP 支援**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>＞。

## <a name="example"></a>範例

下面的示例顯示了線程池啟動與啟動后使用線程池的一些影響。 假設一個x64,單核,雙處理器,線程池需要大約16毫秒啟動。 之後,線程池的額外費用很小。

使用 **/openmp**編譯時,對 test2 的第二個調用永遠不會比使用 **/openmp-** 編譯時運行的時間長,因為沒有線程池啟動。 在一百萬次反覆運算中 **,/openmp**版本比第二個調用 test2 的 **/openmp 版本**快。 在 25 次反覆運算中 **,/openmp 和** **/openmp**版本註冊小於時鐘粒度。

如果應用程式中只有一個循環,並且運行在小於 15 ms(根據電腦上的大致開銷進行調整)中 **,/openmp**可能不合適。 如果它更高,您可能需要考慮使用 **/openmp**。

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md) \
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md) \
[MSVC 中的 OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)
