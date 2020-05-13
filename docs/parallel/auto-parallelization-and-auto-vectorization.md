---
title: 自動平行處理和自訂向量化
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: adc0dd9346cc2850b02e01804e26044c367f2d14
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538619"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>自動平行處理和自訂向量化

Auto-Parallelizer 和 Auto-Vectorizer 的設計目的是為您程式碼中的迴圈提供自動效能提升。

## <a name="auto-parallelizer"></a>Auto-Parallelizer

[/Qpar](../build/reference/qpar-auto-parallelizer.md)編譯器參數可讓您在程式碼中*自動*平行處理迴圈。 當您指定這個旗標而不變更現有的程式碼時，編譯器便會評估程式碼，以尋找可能受益於平行處理的迴圈。 因為它可能會發現沒有什麼作用、因此不會受益於平行處理的迴圈，而且，因為每個不必要的平行處理可能會引起執行緒集區繁衍 (Sprawning)、額外的同步處理，或其他容易導致效能變慢 (而非改善效能) 的處理序，所以編譯器會保守地選取它平行處理的迴圈。 下列範例中，在編譯期間，迴圈的上限為未知：

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

因為 `u` 可能是較小的值，所以編譯器不會自動平行處理此迴圈。 不過，您可能仍想將它平行處理，因為您知道 `u` 永遠會是大的值。 若要啟用自動平行處理，請指定[#pragma 迴圈（hint_parallel （n））](../preprocessor/loop.md)， `n`其中是要平行處理的執行緒數目。 在下列範例中，編譯器會嘗試在 8 個執行緒之間平行處理迴圈。

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

如同所有的[pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)指示詞，也支援替代`__pragma(loop(hint_parallel(n)))`的 pragma 語法。

對於部分迴圈，即使您希望平行處理它們，編譯器仍無法處理。 範例如下：

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

每次呼叫函式 `upper_bound()` 時，它可能會有所變更。 因為無法知道上限，編譯器可發出診斷訊息，說明它為何無法平行處理此迴圈。 下列範例將展示可平行處理的迴圈、無法平行處理的迴圈、在命令提示字元中使用的編譯器語法，以及每個命令列選項的編譯器輸出：

```cpp
int A[1000];
void test() {
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) {
        A[i] = A[i] + 1;
    }

    for (int i=1000; i<2000; ++i) {
        A[i] = A[i] + 1;
    }
}
```

使用下列命令進行編譯：

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

會產生以下輸出：

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

使用下列命令進行編譯：

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

會產生以下輸出：

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

請注意兩個不同[/Qpar-report （自動平行化工具報告層級）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)選項之間的輸出差異。 `/Qpar-report:1` 只會針對平行處理成功的迴圈輸出平行化工具訊息。 `/Qpar-report:2` 會對平行處理成功和失敗的迴圈輸出平行化工具訊息。

如需原因代碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

## <a name="auto-vectorizer"></a>自動向量化工具

自動向量化工具會分析您程式碼中的迴圈，並嘗試在目標電腦上使用向量暫存器和指令，以執行這些迴圈。 這可以改善您程式碼的效能。 編譯器會根據[/arch](../build/reference/arch-minimum-cpu-architecture.md)交換器，以 INTEL 或 AMD 處理器中的 SSE2、AVX 和 AVX2 指示為目標，或 ARM 處理器上的霓虹燈指示。

自動向量化工具可能會產生不同的指令，而非 `/arch` 參數所指定的指令。 這些指令受執行階段檢查保護，以確定該程式碼仍然能夠正確執行。 例如，當您編譯 `/arch:SSE2` 時，可能會發出 SSE4.2 指令。 執行階段檢查會驗證目標處理器是否適用 SSE4.2，若該處理器不支援這些指令的話，便會跳到非 SSE4.2 版本的迴圈。

根據預設，會啟用自動向量化工具。 如果您想要比較您的程式碼在向量化之下的效能，可以使用[#pragma 迴圈（no_vector）](../preprocessor/loop.md)來停用任何給定迴圈的向量化。

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

如同所有的[pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)指示詞，也支援替代`__pragma(loop(no_vector))`的 pragma 語法。

如同自動平行化工具，您可以指定[/Qvec-report （自動向量化工具報告層級）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)命令列選項，只`/Qvec-report:1`報告成功向量化的迴圈，或成功和失敗的向量化迴圈—`/Qvec-report:2`）。

如需原因代碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

如需示範向量化工具如何實際運作的範例，請參閱[Project 奧斯丁第2部，共6頁：頁面 Curling](https://devblogs.microsoft.com/cppblog/project-austin-part-2-of-6-page-curling/)

## <a name="see-also"></a>請參閱

[進入](../preprocessor/loop.md)<br/>
[機器碼中的平行程式設計](/archive/blogs/nativeconcurrency)<br/>
[/Qpar (自動平行化工具)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-report (自動平行化工具報告層級)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report (自動向量化工具報告層級)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)
