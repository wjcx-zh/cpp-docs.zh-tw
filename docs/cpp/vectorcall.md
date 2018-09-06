---
title: __vectorcall |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 463f005388a066776d7db8b1701850e08888de76
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895093"
---
# <a name="vectorcall"></a>__vectorcall

**Microsoft 專屬**

**__Vectorcall**呼叫慣例會指定函數的引數會傳入暫存器，盡可能中。 **__vectorcall**使用更多的暫存器引數比[__fastcall](../cpp/fastcall.md)則是預設[x64 呼叫慣例](../build/overview-of-x64-calling-conventions.md)使用。 **__Vectorcall**呼叫慣例僅適用於原生程式碼及更新版本包含 Streaming SIMD Extensions 2 (SSE2) 的 x86 和 x64 處理器上。 使用 **__vectorcall**加速函式，傳遞多個浮點或 SIMD 向量引數，並執行作業，利用引數的暫存器中載入。 下列清單顯示的 x86 和 x64 實作通用的功能 **__vectorcall**。 這些差異稍後會在本文中加以說明。

|元素|實作|
|-------------|--------------------|
|C 名稱裝飾慣例|函式名稱會加上兩個"@"符號 (\@\@) 後面接著位元組數 （十進位） 的參數清單中。|
|大小寫轉譯慣例|不會執行大小寫轉譯。|

使用[/Gv](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會造成編譯為模組中的每個函式 **__vectorcall**函式是成員函式，除非以衝突的呼叫慣例屬性宣告，會使用`vararg`變數引數清單中，或具有名稱`main`。

您可以由暫存器中傳遞的引數的三種 **__vectorcall**函式：*整數型別*值*向量類型*的值，和*同質性向量彙總*(HVA) 值。

整數類型符合兩個需求：它符合處理器的原生暫存器大小 (例如，在 x86 電腦上為 4 位元組，在 x64 電腦上為 8 位元組)，且可轉換為各種暫存器長度的整數，而不會變更它的位元表示。 比方說，可以提升為任何型別**int** x86 上 (**long long** x64) — 比方說， **char**或**簡短**— 或可以轉換成**int** (**long long** x64) 並沒有變更是整數類型傳回到其原始型別。 整數類型包括指標、 參考及**結構**或**聯集**類型的 4 個位元組 （在 x64 上的 8 位元組） 或更少。 X64 平台，較大**結構**並**聯集**類型由參考傳遞至呼叫端; 在 x86 上配置記憶體平台，它們會在堆疊上傳遞的值。

向量型別是浮點類型 — 例如，**浮點數**或**double**— 或 SIMD 向量類型 — 比方說， **__m128**或 **__m256**.

HVA 類型是一種複合類型，具有四個相同向量類型的資料成員。 HVA 類型與其成員的向量類型具有相同的對齊需求。 這是範例的 hva**結構**包含三個相同向量類型，且具有 32 位元組對齊的定義：

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```  

宣告您的函式，明確 **__vectorcall**關鍵字在標頭檔，以允許另行編譯的程式碼連結正確無誤。 函式必須是原型才能使用 **__vectorcall**，而且不能使用`vararg`可變長度引數清單。

成員函式可能會宣告可透過 **__vectorcall**規範。 隱藏**這**指標會傳遞由暫存器做為第一個整數型別引數。

在 ARM 電腦上 **__vectorcall**會接受並忽略編譯器。

對於非靜態類別成員函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義：

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

**__Vectorcall**呼叫慣例修飾詞時，必須指定一個指向 **__vectorcall**建立函式。 下一個範例會建立**typedef**指標 **__vectorcall**接受四個函式**double**引數並傳回 **__m256**值：

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```  

## <a name="vectorcall-convention-on-x64"></a>在 x64 上的 __vectorcall 慣例

**__Vectorcall** x64 呼叫慣例會擴充標準 x64 呼叫慣例以運用其他暫存器。 整數型別引數和向量型別引數都是根據引數清單中的位置對應到暫存器。 HVA 引數會配置給未使用的向量暫存器。

當前四個引數 (由左至右的順序) 的任何一個為整數型別引數時，會在對應於該位置的暫存器 (RCX、RDX、R8 或 R9) 中傳遞。 隱藏**這**指標會被視為第一個整數型別引數。 當 HVA 引數 (前四個引數的其中一個) 無法在可用暫存器中傳遞時，呼叫端配置記憶體的參考會在對應的整數類型暫存器中傳遞。 第四個參數位置之後的整數型別引數會在堆疊上傳遞。

當前六個引數 (由左至右的順序) 的任何一個為向量型別引數時，會根據引數位置，在 SSE 向量暫存器 0 到 5 中以傳值方式傳遞。 浮點數和 **__m128**傳遞類型在 xmm 暫存器和 **__m256**類型會在 YMM 暫存器。 這不同於標準的 x64 呼叫慣例，因為向量類型是以傳值方式傳遞而不是以傳址方式傳遞，因此會使用其他的暫存器。 向量類型引數配置陰影堆疊空間固定為 8 個位元組，而[/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md)選項不會套用。 在第七個和後面的參數位置上的向量型別引數，是在堆疊上以傳址方式傳遞到呼叫端所配置的記憶體。

配置向量引數的暫存器之後，配置 HVA 引數的資料成員，以遞增順序，到未使用的向量暫存器 XMM0 到 XMM5 (或 YMM0 到 YMM5，用於 **__m256**類型)，只要有足夠的暫存器可供整個 hva 使用即可。 如果沒有足夠的暫存器可供使用，HVA 引數會以傳址方式傳遞至呼叫端所配置的記憶體。 HVA 引數的堆疊陰影空間會固定為 8 個位元組，且具有未定義的內容。 HVA 引數是以參數清單中由左至右的順序指派給暫存器，而且可以位於任何位置。 位於未指派給向量暫存器的前四個引數位置其中之一的 HVA 引數，會在對應至該位置的整數暫存器中以傳址方式傳遞。 在第四個參數位置之後以傳址方式傳遞的 HVA 引數會推送至堆疊上。

結果 **__vectorcall**函式會傳回盡可能的暫存器中的值。 整數類型 (包括 8 位元組或較少的結構或等位) 的結果會在 RAX 中以傳值方式傳回。 視大小而定，向量類型的結果是以傳值方式在 XMM0 或 YMM0 中傳回。 HVA 結果的每個資料項目會視大小而定，以傳值方式從暫存器 XMM0:XMM3 或 YMM0:YMM3 中傳回。 對應暫存器無法容納的結果類型會以傳址方式傳回至呼叫端配置的記憶體。

堆疊由呼叫端 x64 維護實作 **__vectorcall**。 呼叫端初構和終解程式碼會配置並清除所呼叫函式的堆疊。 堆疊上的引數會從右至左推入，並且為暫存器中傳遞的引數配置陰影堆疊空間。

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

## <a name="vectorcall-convention-on-x86"></a>x86 上的 __vectorcall 慣例

**__Vectorcall**呼叫慣例遵循 **__fastcall** 32 位元整數型別引數，並且能夠充分 SSE 向量暫存器的向量類型和 HVA 引數的慣例。

存在於參數清單中的前兩個整數型別引數，會由左至右分別放置在 ECX 和 EDX 中。 隱藏**這**指標會被視為第一個整數型別引數，並在 ECX 中傳遞。 前六個向量型別引數會透過 SSE 向量暫存器 0 到 5，或者在 YMM 或 XMM 暫存器中 (視引數大小而定)，以傳值方式傳遞。

前六個向量型別引數依序由左至右，在 SSE 向量暫存器 0 到 5 中，以傳值方式傳遞。 浮點數和 **__m128**傳遞類型在 xmm 暫存器和 **__m256**類型會在 YMM 暫存器。 陰影堆疊空間不會配置給暫存器所傳遞的向量型別引數。 第七個和後續向量型別引數，會在堆疊上以傳址方式傳遞至呼叫端配置的記憶體。 編譯器錯誤的限制[C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md)不適用於這些引數。

配置向量引數的暫存器之後，按遞增順序未使用的向量來配置 HVA 引數的成員資料暫存器 XMM0 到 XMM5 (或 YMM0 到 YMM5，用於 **__m256**類型)，只要有足夠的暫存器可供整個 hva 使用即可。 如果沒有足夠的暫存器可供使用，HVA 引數會在堆疊上以傳址方式傳遞至呼叫端所配置的記憶體。 不會配置 HVA 引數的陰影堆疊空間。 HVA 引數是以參數清單中由左至右的順序指派給暫存器，而且可以位於任何位置。

結果 **__vectorcall**函式會傳回盡可能的暫存器中的值。 整數類型 (包括 4 位元組或較少的結構或等位) 的結果會在 EAX 中以傳值方式傳回。 8 位元組或較少的整數類型結構或等位會在 EDX:EAX 中，以傳值方式傳回。 視大小而定，向量類型的結果是以傳值方式在 XMM0 或 YMM0 中傳回。 HVA 結果的每個資料項目會視大小而定，以傳值方式從暫存器 XMM0:XMM3 或 YMM0:YMM3 中傳回。 其他結果類型是以傳址方式，由呼叫端所配置的記憶體傳回。

X86 實作 **__vectorcall**如下所示在返回之前會推送到堆疊上由右至左依呼叫者和呼叫的函式的引數的慣例清除堆疊。 只有未放置在暫存器上的引數會推入至堆疊。

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

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
[關鍵字](../cpp/keywords-cpp.md)