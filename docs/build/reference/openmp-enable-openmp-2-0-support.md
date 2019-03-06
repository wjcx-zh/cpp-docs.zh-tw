---
title: /openmp (啟用 OpenMP 2.0 支援)
ms.date: 11/04/2016
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: bea51c7af41df666fd441555daa0d8d8387377ac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414131"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (啟用 OpenMP 2.0 支援)

可讓編譯器處理`#pragma` [omp](../../preprocessor/omp.md)。

## <a name="syntax"></a>語法

```
/openmp
```

## <a name="remarks"></a>備註

`#pragma omp` 用來指定[指示詞](../../parallel/openmp/reference/openmp-directives.md)並[子句](../../parallel/openmp/reference/openmp-clauses.md)。 如果 **/openmp**中未指定編譯中，編譯器會忽略 OpenMP 子句和指示詞。 [OpenMP 函式](../../parallel/openmp/reference/openmp-functions.md)呼叫會處理編譯器即使 **/openmp**未指定。

應用程式編譯 **/openmp**並 **/clr**只能在單一應用程式網域的程序中執行; 不支援多個應用程式定義域。 也就是執行的模組建構函式 (.cctor) 時，它會偵測處理程序會使用編譯 **/openmp**如果應用程式載入到非預設的執行階段。 如需詳細資訊，請參閱 < [appdomain](../../cpp/appdomain.md)， [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)，並[初始化混合組件](../../dotnet/initialization-of-mixed-assemblies.md)。

如果您嘗試載入以編譯應用程式 **/openmp**並 **/clr**非預設應用程式定義域，<xref:System.TypeInitializationException>會擲回例外狀況，偵錯工具之外，偵錯工具中，將會擲回 OpenMPWithMultipleAppdomainsException 例外狀況。

在下列情況下，可能也會引發這些例外狀況：

- 如果您的應用程式以編譯 **/clr**，但不是能搭配 **/openmp**，非預設應用程式定義域，但其中的程序包含使用已編譯的應用程式會載入 **/openmp**。

- 如果您傳遞您 **/clr**公用程式，例如 regasm.exe 的應用程式 ([Regasm.exe （組件登錄工具）](/dotnet/framework/tools/regasm-exe-assembly-registration-tool))，其目標組件載入至非預設應用程式定義域。

Common language runtime 的程式碼存取安全性並不適用於 OpenMP 區域。 如果您套用的 CLR 程式碼存取安全性 」 屬性，在平行區域之外，它不會處於作用中平行區域。

Microsoft 建議，您不會寫入 **/openmp**應用程式，可讓部分信任的呼叫端，使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>，或任何 CLR 程式碼存取安全性屬性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**C/c + +** 節點。

1. 選取 **語言**屬性頁。

1. 修改**OpenMP 支援**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。

## <a name="example"></a>範例

下列範例會示範一些與它在啟動之後，使用執行緒集區的執行緒集區啟動的影響。 假設 x64，單一核心，雙處理器執行緒集區需要大約 16ms年啟動。 之後，但會極少的執行緒集區的成本。

當您編譯 **/openmp**，test2 第二次呼叫永遠不會執行任何時間超過您使用如果編譯 **/openmp-**，因為沒有任何執行緒集區啟動。 百萬個反覆項目在 **/openmp**版本的速度比 **/openmp-** 版本的第二次呼叫這兩個 25 反覆項目在 test2，來回 **/openmp-** 和 **/openmp**版本註冊小於時鐘資料粒度。

因此，如果您在您的應用程式只能有一個迴圈，並小於 15ms （調整您的電腦上的額外負荷），在執行 **/openmp**可能不適當，但如果是它的任何項目，您可能要考慮使用 **/openmp**。

```
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

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
