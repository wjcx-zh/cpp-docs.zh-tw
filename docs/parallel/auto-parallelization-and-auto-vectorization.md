---
title: 自動平行處理和自動向量化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1ec19065647f78b4d9b2665003c0aa3a2795ba
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="auto-parallelization-and-auto-vectorization"></a>自動平行處理和自訂向量化
Auto-Parallelizer 和 Auto-Vectorizer 的設計目的是為您程式碼中的迴圈提供自動效能提升。  
  
## <a name="auto-parallelizer"></a>Auto-Parallelizer  
 [/Qpar](../build/reference/qpar-auto-parallelizer.md)編譯器參數可讓*自動平行處理*您的程式碼中的迴圈。 當您指定這個旗標而不變更現有的程式碼時，編譯器便會評估程式碼，以尋找可能受益於平行處理的迴圈。 因為它可能會發現沒有什麼作用、因此不會受益於平行處理的迴圈，而且，因為每個不必要的平行處理可能會引起執行緒集區繁衍 (Sprawning)、額外的同步處理，或其他容易導致效能變慢 (而非改善效能) 的處理序，所以編譯器會保守地選取它平行處理的迴圈。 下列範例中，在編譯期間，迴圈的上限為未知：  
  
```cpp  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 因為 `u` 可能是較小的值，所以編譯器不會自動平行處理此迴圈。 不過，您可能仍想將它平行處理，因為您知道 `u` 永遠會是大的值。 若要啟用自動平行化作業，請指定[#pragma loop(hint_parallel(n))](../preprocessor/loop.md)，其中`n`是要平行處理的執行緒數目。 在下列範例中，編譯器會嘗試在 8 個執行緒之間平行處理迴圈。  
  
```cpp  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 如同所有[pragma 指示詞](../preprocessor/pragma-directives-and-the-pragma-keyword.md)，替代的 pragma 語法`__pragma(loop(hint_parallel(n)))`也支援。  
  
 對於部分迴圈，即使您希望平行處理它們，編譯器仍無法處理。 以下為範例：  
  
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
  
 **cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-: 1**  
  
 會產生以下輸出：  
  
 **---分析函式： 失效的 __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4)： 迴圈平行化**  
  
 使用下列命令進行編譯：  
  
 **cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-: 2**  
  
 會產生以下輸出：  
  
 **---分析函式： 失效的 __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4)： 迴圈平行化**   
 **d:\myproject\mytest.cpp(4)： 迴圈未平行化，原因 '1008'**  
  
 請注意之間兩個不同的輸出差異[/qpar （自動平行化工具報告層級）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)選項。 **/Qpar-: 1**輸出僅供平行處理成功的迴圈平行化工具訊息。 **/Qpar-: 2**輸出這兩個成功和失敗迴圈會對平行處理的平行化工具訊息。  
  
 如需原因碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
## <a name="auto-vectorizer"></a>自動向量化工具  
 自動向量化工具會分析您程式碼中的迴圈，並嘗試在目標電腦上使用向量暫存器和指令，以執行這些迴圈。 這可以改善您程式碼的效能。 SSE2、 AVX 和 AVX2 指令在 Intel 或 AMD 處理器或 ARM 處理器上的 NEON 指令為目標的編譯器根據[/arch](../build/reference/arch-minimum-cpu-architecture.md)切換。  
  
 自動向量化工具可能會產生不同的指示，與所指定 **/arch**切換。 這些指令受執行階段檢查保護，以確定該程式碼仍然能夠正確執行。 例如，當您編譯 **/arch:SSE2**，可能會發出 SSE4.2 指令。 執行階段檢查會驗證目標處理器是否適用 SSE4.2，若該處理器不支援這些指令的話，便會跳到非 SSE4.2 版本的迴圈。  
  
 根據預設，會啟用自動向量化工具。 如果您想要比較您的程式碼在向量化之後的效能，您可以使用[#pragma loop （no_vector)](../preprocessor/loop.md)來針對任何特定迴圈停用。  
  
```  
  
      #pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 如同所有[pragma 指示詞](../preprocessor/pragma-directives-and-the-pragma-keyword.md)，替代的 pragma 語法`__pragma(loop(no_vector))`也支援。  
  
 使用自動平行化工具，您可以指定為[/Qvec-report （自動向量化工具報告層級）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)命令列選項，成功報告向量化迴圈只 —**/Qvec-: 1**— 或成功和失敗向量化迴圈 —**/Qvec-: 2**)。  
  
 如需原因碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
 如需顯示向量化工具實際上的運作方式的範例，請參閱[Project Austin 的第 2 部分 6： 頁面捲曲](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [迴圈](../preprocessor/loop.md)   
 [原生程式碼以進行平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=263662)   
 [/Qpar （自動平行化工具）](../build/reference/qpar-auto-parallelizer.md)   
 [/Qpar-report （自動平行化工具報告層級）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [/Qvec-report （自動向量化工具報告層級）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [向量化工具和平行化工具訊息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)