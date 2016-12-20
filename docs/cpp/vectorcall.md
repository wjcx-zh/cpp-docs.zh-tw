---
title: "__vectorcall | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __vectorcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `__vectorcall` 呼叫慣例會指定函式的引數應該盡可能在暫存器中傳遞。  `__vectorcall` 用於引數的暫存器比 [\_\_fastcall](../cpp/fastcall.md) 或預設的 [x64 呼叫慣例](../build/overview-of-x64-calling-conventions.md)使用的多。  只有在包含 Streaming SIMD Extensions 2 \(SSE2\) \(含\) 以上版本的 x86 和 x64 處理器機器碼中才支援 `__vectorcall` 呼叫慣例。  使用 `__vectorcall` 加速傳遞多個浮點引數或 SIMD 向量引數的函式，並執行可利用暫存器中載入之引數的作業。  下列清單顯示 `__vectorcall` 的 x86 和 x64 實作通用的功能。  這些差異稍後會在本文中加以說明。  
  
|元素|實作|  
|--------|--------|  
|C 名稱裝飾慣例|函式名稱後面會加上兩個 @ 符號 \(@@\)，後面接著參數清單中的位元組數 \(十進位\)。|  
|大小寫轉譯慣例|不會執行大小寫轉譯。|  
  
 使用 [\/Gv](../build/reference/gd-gr-gv-gz-calling-convention.md) 編譯器選項會導致模組中的每個函式編譯為 `__vectorcall`，除非該函式為成員函式、以衝突的呼叫慣例屬性宣告、使用 `vararg` 變數引數清單，或函式的名稱為 `main`。  
  
 您可以透過暫存器，在 `__vectorcall` 函式中傳遞下列三種引數：「*整數類型*」\(integer type\) 值、「*向量類型*」\(vector type\) 值和「*同質性向量彙總*」\(homogeneous vector aggregate，HVA\) 值。  
  
 整數類型符合兩個需求：它符合處理器的原生暫存器大小 \(例如，在 x86 電腦上為 4 位元組，在 x64 電腦上為 8 位元組\)，且可轉換為各種暫存器長度的整數，而不會變更它的位元表示。  例如，可以在 x86 上升級為 `int` \(在 x64 上為 `long long`\) 的任何類型 \(例如 `char` 或 `short`\)，或是可以轉型為 `int` \(在 x64 上為 `long long`\) 再還原為其原始類型而不需變更的任何類型，都是整數類型。  整數類型包含指標、參考以及 4 個位元組 \(在 x64 上為 8 個位元組\) 或較小的 `struct` 或 `union` 類型。  在 x64 平台上，較大的 `struct` 和 `union` 類型是以傳址方式傳遞至呼叫端所配置的記憶體。在 x86 平台上，則以傳值方式在堆疊上傳遞。  
  
 向量類型可以是浮點數類型 \(例如，`float` 或 `double`\)，或是 SIMD 向量類型 \(例如，`__m128` 或 `__m256`\)。  
  
 HVA 類型是一種複合類型，具有四個相同向量類型的資料成員。  HVA 類型與其成員的向量類型具有相同的對齊需求。  以下為包含三個相同向量類型，以及具有 32 位元組對齊的 HVA `struct` 定義範例：  
  
```cpp  
typedef struct {  
   __m256 x;  
   __m256 y;  
   __m256 z;  
} hva3;    // 3 element HVA type on __m256  
  
```  
  
 在標頭檔中使用 `__vectorcall` 關鍵字明確宣告函式，以允許另行編譯的程式碼連結，而不會發生錯誤。  函式必須是原型才能使用 `__vectorcall`，而且不能使用 `vararg` 可變長度的引數清單。  
  
 使用 `__vectorcall` 規範可宣告成員函式。  隱藏的 `this` 指標會由暫存器做為第一個整數類型引數傳遞。  
  
 在 ARM 電腦上，編譯器會接受並忽略 `__vectorcall`。  
  
 對於非靜態類別成員函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。  也就是說，對於類別非靜態成員而言，宣告時所指定的呼叫慣例是在定義時假設。  如果已指定此類別定義：  
  
```cpp  
struct MyClass {  
   void __vectorcall mymethod();  
};  
```  
  
 這個：  
  
```cpp  
void MyClass::mymethod() { return; }  
```  
  
 相當於這個：  
  
```cpp  
void __vectorcall MyClass::mymethod() { return; }  
```  
  
 建立 `__vectorcall` 函式的指標時，必須指定 `__vectorcall` 呼叫慣例修飾詞。  下一個範例會建立 `__vectorcall` 函式之指標的 `typedef`，該函式接受四個 `double` 引數並傳回 `__m256` 值：  
  
```cpp  
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);  
```  
  
## 在 x64 上的 \_\_vectorcall 慣例  
 x64 上的 `__vectorcall` 呼叫慣例會擴充標準 x64 呼叫慣例以運用其他暫存器。  整數類型引數和向量類型引數都是根據引數清單中的位置對應到暫存器。  HVA 引數會配置給未使用的向量暫存器。  
  
 當前四個引數 \(由左至右的順序\) 的任何一個為整數類型引數時，會在對應於該位置的暫存器 \(RCX、RDX、R8 或 R9\) 中傳遞。  隱藏的 `this` 指標會是第一個整數類型引數。  當 HVA 引數 \(前四個引數的其中一個\) 無法在可用暫存器中傳遞時，呼叫端配置記憶體的參考會在對應的整數類型暫存器中傳遞。  第四個參數位置之後的整數類型引數會在堆疊上傳遞。  
  
 當前六個引數 \(由左至右的順序\) 的任何一個為向量類型引數時，會根據引數位置，在 SSE 向量暫存器 0 到 5 中以傳值方式傳遞。  浮點和 `__m128` 類型會在 XMM 暫存器中傳遞，`__m256` 類型則會在 YMM 暫存器中傳遞。  這不同於標準的 x64 呼叫慣例，因為向量類型是以傳值方式傳遞而不是以傳址方式傳遞，因此會使用其他的暫存器。  向量類型引數配置的陰影堆疊空間固定為 8 個位元組，而 [\/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) 選項並不適用。  在第七個和後面的參數位置上的向量類型引數，是在堆疊上以傳址方式傳遞到呼叫端所配置的記憶體。  
  
 配置向量引數暫存器之後，會按遞增順序將 HVA 引數的資料成員分配至未使用的向量暫存器 XMM0 到 XMM5 \(或 YMM0 到 YMM5，用於 `__m256` 類型\)，只要有足夠的可用暫存器供整個 HVA 使用即可。  如果沒有足夠的暫存器可供使用，HVA 引數會以傳址方式傳遞至呼叫端所配置的記憶體。  HVA 引數的堆疊陰影空間會固定為 8 個位元組，且具有未定義的內容。  HVA 引數是以參數清單中由左至右的順序指派給暫存器，而且可以位於任何位置。  位於未指派給向量暫存器的前四個引數位置其中之一的 HVA 引數，會在對應至該位置的整數暫存器中以傳址方式傳遞。  在第四個參數位置之後以傳址方式傳遞的 HVA 引數會推送至堆疊上。  
  
 `__vectorcall` 函式的結果會盡可能在暫存器中以傳值方式傳回。  整數類型 \(包括 8 位元組或較少的結構或等位\) 的結果會在 RAX 中以傳值方式傳回。  視大小而定，向量類型的結果是以傳值方式在 XMM0 或 YMM0 中傳回。  HVA 結果的每個資料項目會視大小而定，以傳值方式從暫存器 XMM0:XMM3 或 YMM0:YMM3 中傳回。  對應暫存器無法容納的結果類型會以傳址方式傳回至呼叫端配置的記憶體。  
  
 堆疊是由 `__vectorcall` x64 實作中的呼叫端維護。  呼叫端初構和終解程式碼會配置並清除所呼叫函式的堆疊。  堆疊上的引數會從右至左推入，並且為暫存器中傳遞的引數配置陰影堆疊空間。  
  
 例如：  
  
```cpp  
// crt_vc64.c  
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c  
// This example creates an annotated assembly listing in  
// crt_vc64.asm.  
  
#include <intrin.h>  
#include <xmmintrin.h>  
  
typedef struct {  
   __m128 array[2];  
} hva2;    // 2 element HVA type on __m128  
  
typedef struct {  
   __m256 array[4];  
} hva4;    // 4 element HVA type on __m256  
  
// Example 1: All vectors  
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.  
// Return value in XMM0.  
__m128 __vectorcall   
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {  
   return d;  
}  
  
// Example 2: Mixed int, float and vector parameters  
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,   
// f in XMM5, g pushed on stack.   
// Return value in YMM0.  
__m256 __vectorcall   
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {  
   return e;  
}  
  
// Example 3: Mixed int and HVA parameters  
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.  
// Passes b by element in [XMM0:XMM1];   
// b's stack shadow area is 8-bytes of undefined value.   
// Return value in XMM0.  
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {  
   return b.array[0];  
}  
  
// Example 4: Discontiguous HVA   
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.  
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because  
// vector arguments b and d were allocated first.   
// Shadow area for c is an 8-byte undefined value.  
// Return value in XMM0.  
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {  
   return b;  
}  
  
// Example 5: Multiple HVA arguments  
// Passes a in RCX, c in R8, e pushed on stack.  
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with   
// stack shadow areas of an 8-byte undefined value.  
// Return value in RAX.  
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {  
   return c + e;  
}  
  
// Example 6: HVA argument passed by reference, returned by register  
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,   
// d in [XMM3:XMM4].   
// Register space was insufficient for b, but not for d.  
// Return value in [YMM0:YMM3].  
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {  
   return b;  
}  
  
int __cdecl main( void )  
{  
   hva4 h4;  
   hva2 h2;  
   int i;  
   float f;  
   __m128 a, b, d;  
   __m256 c, e;  
  
   a = b = d = _mm_set1_ps(3.0f);  
   c = e = _mm256_set1_ps(5.0f);  
   h2.array[0] = _mm_set1_ps(6.0f);  
   h4.array[0] = _mm256_set1_ps(7.0f);  
  
   b = example1(a, b, c, d, e);  
   e = example2(1, b, 3, d, e, 6.0f, 7);  
   d = example3(1, h2, 3, 4, 5);  
   f = example4(1, 2.0f, h4, d, 5);  
   i = example5(1, h2, 3, h4, 5);  
   h4 = example6(h2, h4, c, h2);  
}  
  
```  
  
## x86 上的 \_\_vectorcall 慣例  
 `__vectorcall` 呼叫慣例遵循 32 位元整數類型引數適用的 `__fastcall` 慣例，並將 SSE 向量暫存器運用在向量類型和 HVA 引數。  
  
 存在於參數清單中的前兩個整數類型引數，會由左至右分別放置在 ECX 和 EDX 中。  隱藏的 `this` 指標會做為第一個整數類型引數，並在 ECX 中傳遞。  前六個向量類型引數會透過 SSE 向量暫存器 0 到 5，或者在 YMM 或 XMM 暫存器中 \(視引數大小而定\)，以傳值方式傳遞。  
  
 前六個向量類型引數依序由左至右，在 SSE 向量暫存器 0 到 5 中，以傳值方式傳遞。  浮點和 `__m128` 類型會在 XMM 暫存器中傳遞，`__m256` 類型則會在 YMM 暫存器中傳遞。  陰影堆疊空間不會配置給暫存器所傳遞的向量類型引數。  第七個和後續向量類型引數，會在堆疊上以傳址方式傳遞至呼叫端配置的記憶體。  編譯器錯誤 [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) 的限制不適用於這些引數。  
  
 配置向量引數的暫存器之後，會按遞增順序將 HVA 引數的資料成員分配至未使用的向量暫存器 XMM0 到 XMM5 \(或 YMM0 到 YMM5，用於 `__m256` 類型\)，只要有足夠的可用暫存器供整個 HVA 使用即可。  如果沒有足夠的暫存器可供使用，HVA 引數會在堆疊上以傳址方式傳遞至呼叫端所配置的記憶體。  不會配置 HVA 引數的陰影堆疊空間。  HVA 引數是以參數清單中由左至右的順序指派給暫存器，而且可以位於任何位置。  
  
 `__vectorcall` 函式的結果會盡可能在暫存器中以傳值方式傳回。  整數類型 \(包括 4 位元組或較少的結構或等位\) 的結果會在 EAX 中以傳值方式傳回。  8 位元組或較少的整數類型結構或等位會在 EDX:EAX 中，以傳值方式傳回。  視大小而定，向量類型的結果是以傳值方式在 XMM0 或 YMM0 中傳回。  HVA 結果的每個資料項目會視大小而定，以傳值方式從暫存器 XMM0:XMM3 或 YMM0:YMM3 中傳回。  其他結果類型是以傳址方式，由呼叫端所配置的記憶體傳回。  
  
 `__vectorcall` 的 x86 實作遵循引數由呼叫端從右至左推入至堆疊的慣例，而且被呼叫的函式會在返回之前清除堆疊。  只有未放置在暫存器上的引數會推入至堆疊。  
  
 例如：  
  
```cpp  
// crt_vc86.c  
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c  
// This example creates an annotated assembly listing in  
// crt_vc86.asm.  
  
#include <intrin.h>  
#include <xmmintrin.h>  
  
typedef struct {  
   __m128 array[2];  
} hva2;    // 2 element HVA type on __m128  
  
typedef struct {  
   __m256 array[4];  
} hva4;    // 4 element HVA type on __m256  
  
// Example 1: All vectors  
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.  
// Return value in XMM0.  
__m128 __vectorcall   
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {  
   return d;  
}  
  
// Example 2: Mixed int, float and vector parameters  
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,   
// f in XMM3, g pushed on stack.   
// Return value in YMM0.  
__m256 __vectorcall   
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {  
   return e;  
}  
  
// Example 3: Mixed int and HVA parameters  
// Passes a in ECX, c in EDX, d and e pushed on stack.  
// Passes b by element in [XMM0:XMM1].   
// Return value in XMM0.  
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {  
   return b.array[0];  
}  
  
// Example 4: HVA assigned after vector types  
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.  
// Passes c by element in [YMM2:YMM5].   
// Return value in XMM0.  
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {  
   return b;  
}  
  
// Example 5: Multiple HVA arguments  
// Passes a in ECX, c in EDX, e pushed on stack.  
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].  
// Return value in EAX.  
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {  
   return c + e;  
}  
  
// Example 6: HVA argument passed by reference, returned by register  
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,   
// d in [XMM3:XMM4].   
// Register space was insufficient for b, but not for d.  
// Return value in [YMM0:YMM3].  
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {  
   return b;  
}  
  
int __cdecl main( void )  
{  
   hva4 h4;  
   hva2 h2;  
   int i;  
   float f;  
   __m128 a, b, d;  
   __m256 c, e;  
  
   a = b = d = _mm_set1_ps(3.0f);  
   c = e = _mm256_set1_ps(5.0f);  
   h2.array[0] = _mm_set1_ps(6.0f);  
   h4.array[0] = _mm256_set1_ps(7.0f);  
  
   b = example1(a, b, c, d, e);  
   e = example2(1, b, 3, d, e, 6.0f, 7);  
   d = example3(1, h2, 3, 4, 5);  
   f = example4(1, 2.0f, h4, d, 5);  
   i = example5(1, h2, 3, h4, 5);  
   h4 = example6(h2, h4, c, h2);  
}  
  
```  
  
 **結束 Microsoft 專有**  
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)