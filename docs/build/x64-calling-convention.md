---
title: x64 呼叫慣例
description: 預設的 x64 ABI 的呼叫慣例的詳細資料。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 02bf4719766366049b600b148ad88fc238f4e54e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313609"
---
# <a name="x64-calling-convention"></a>x64 呼叫慣例

本章節描述的標準程序和一個函式 （呼叫者） 使用在 x64 進行另一個函式 （被呼叫端） 的呼叫慣例的程式碼。

## <a name="calling-convention-defaults"></a>呼叫慣例預設值

X64 應用程式二進位介面 (ABI) 會使用四個註冊快速呼叫的呼叫慣例的預設值。 呼叫堆疊上配置空間，作為被呼叫者來儲存這些暫存器的陰影存放區。 函式呼叫的引數和用於這些引數的暫存器之間沒有嚴格的一對一對應。 任何引數的不符合 8 個位元組，或不是 1、 2、 4 或 8 個位元組，必須傳址方式傳遞。 單一引數則會永遠不會分散到多個暫存器。 X87 暫存器堆疊是未使用，並可由被呼叫端，但必須考慮 volatile 跨函式呼叫。 所有的浮點數作業會完成使用 16 XMM 暫存器。 整數引數會傳入暫存器 RCX、 RDX、 R8 和 R9。 浮點引數會傳入 XMM0L、 XMM1L、 XMM2L 和 XMM3L。 16 位元組引數是傳址方式傳遞。 在將詳細說明參數傳遞[參數傳遞](#parameter-passing)。 這些暫存器中，除了 RAX、 R10，R11，XMM4 和 XMM5 會視為 volatile。 所有其他暫存器是靜態。 暫存器使用方式中有詳細記載[註冊使用量](../build/x64-software-conventions.md#register-usage)並[呼叫端/被呼叫端儲存註冊](#callercallee-saved-registers)。

原型的函式中，所有引數會轉換成預期的被呼叫端類型，然後才會傳遞。 呼叫端會負責配置的空間被呼叫端，參數，而且即使被呼叫端不需要那麼多的參數，則一律必須配置足夠的空間來儲存四個的暫存器參數。 這個慣例會簡化支援沒有原型 C 語言函式和 vararg C /C++函式。 Vararg 或 unprototyped 函式中，任何浮點值必須在對應一般用途的暫存器中重複。 任何超過前四個參數必須儲存在堆疊上之後在呼叫之前儲存的陰影。 Vararg 函式詳細資料可在[Varargs](#varargs)。 沒有原型的函式資訊詳述[沒有原型的函式](#unprototyped-functions)。

## <a name="alignment"></a>對齊

大部分的結構對齊至其自然對齊。 主要的例外狀況是堆疊指標並`malloc`或`alloca`專為 16 個位元組，以協助效能的記憶體。 16 個位元組以上的對齊必須手動完成，但由於 16 個位元組是常用的對齊方式大小 XMM 作業，這個值應該適合大部分的程式碼。 如需有關結構配置和對齊方式的詳細資訊，請參閱[型別和儲存體](../build/x64-software-conventions.md#types-and-storage)。 堆疊配置的相關資訊，請參閱[x64 堆疊使用方式](../build/stack-usage.md)。

## <a name="unwindability"></a>Unwindability

分葉函式是函式，不會變更任何非暫時性暫存器。 非分葉函式可能會變更非揮發性 RSP 比方說，呼叫函式，或為區域變數配置額外的堆疊空間。 若要處理的例外狀況時，請復原靜態暫存器，非分葉函式都必須以說明如何正確回溯任意指令處函式的靜態資料註解。 這項資料會儲存為*pdata*，或程序的資料，依序指向*xdata*、 例外狀況處理的資料。 Xdata 包含回溯的資訊，並可以指向其他 pdata 或例外狀況處理常式函式。 初構和終都具有高度限制，使它們可以適當地述 xdata。 堆疊指標必須對齊 16 個位元組，但不屬於初構的終解，在分葉函式內的程式碼的任何區域中。 分葉函式可以藉由模擬傳回，因此不需要 pdata 和 xdata 進行回溯。 如需函式初構和終適當的結構的詳細資訊，請參閱[x64 初構和終解](../build/prolog-and-epilog.md)。 如需例外狀況處理和例外狀況處理和 pdata 和 xdata 回溯的詳細資訊，請參閱[x64 例外狀況處理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>參數傳遞

前四個整數引數會傳入暫存器。 整數值會由左到右依序傳遞在 RCX、 RDX、 R8 和 R9，分別。 引數 5 和更新版本會在堆疊上傳遞。 所有引數會靠右對齊的暫存器，因此被呼叫端可以忽略暫存器的較高的位元，並只存取部分的所需的暫存器。

前四個參數中的任何浮點數和雙精確度引數會傳入 XMM0-XMM3，視位置而定。 RCX、 RDX、 R8 和通常會用於那些職位的 R9 整數暫存器會被忽略，除非在 varargs 引數的情況下。 如需詳細資訊，請參閱 < [Varargs](#varargs)。 同樣地，XMM0-XMM3 時對應的引數是整數或指標類型，會忽略暫存器。

[__m128](../cpp/m128.md)類型、 陣列和字串一律不會以即時運算值傳遞。 相反地，指標會傳遞至呼叫端所配置的記憶體。 如同它們是相同大小的整數，會傳遞結構和等位的大小為 8、 16、 32 或 64 位元為單位和 __m64 類型。 呼叫端所配置的記憶體，會將結構或等位的其他規模之傳遞的指標。 傳遞的指標，這些彙總類型包括\__m128，呼叫端配置的暫存記憶體必須對齊 16 位元組。

內建函式不會配置堆疊空間，不要呼叫其他函式中，有時會使用其他動態暫存器，來傳遞其他暫存器引數。 此最佳化可由編譯器和內建函式實作之間緊密的繫結。

被呼叫端負責傾印到其陰影空間，如有需要的暫存器參數。

下表摘要說明如何傳遞參數：

|參數類型|如何傳遞|
|--------------------|----------------|
|浮點|第一次參數 4-透過 XMM3 XMM0。 其他項目堆疊上傳遞。|
|整數|前 4 個參數-RCX，RDX，R8 R9。 其他項目堆疊上傳遞。|
|彙總 （8、 16、 32、 或 64 位元） 及 __m64|前 4 個參數-RCX，RDX，R8 R9。 其他項目堆疊上傳遞。|
|彙總 （其他）|指標。 作為指標在 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|
|__m128|指標。 作為指標在 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|

### <a name="example-of-argument-passing-1---all-integers"></a>傳遞 1-所有整數引數的範例

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>引數傳遞 2-所有的浮點數的範例

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>引數傳遞 3-混合式的整數和浮點數的範例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>範例中的引數傳遞 4-__m64、 \__m128，和彙總

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果參數傳遞透過 varargs （比方說，省略引數），然後正常的暫存器參數傳遞慣例適用於，包括溢出至堆疊的第五個和後續引數。 它負責被呼叫端的傾印的引數，取得其位址。 僅限浮點值，整數暫存器和浮點暫存器必須包含值，以免被呼叫者預期整數暫存器中的值。

## <a name="unprototyped-functions"></a>沒有原型的函式

不完全原型的函式，呼叫端會傳遞整數值，以整數和浮點數的值為雙精確度。 對於只有浮點數值，整數暫存器和浮點暫存器包含浮點值如果被呼叫端需要整數暫存器值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>傳回值

透過 RAX; 則會傳回純量傳回值可納入 64 位元其中包括 __m64 類型。 非純量類型包括浮點數、 雙精度浮點數和向量類型，例如[__m128](../cpp/m128.md)， [__m128i](../cpp/m128i.md)， [__m128d](../cpp/m128d.md) XMM0 中傳回。 對於 RAX 或 XMM0 中傳回的值，其中未使用之位元的狀態尚未定義。

使用者定義的類型可透過全域函式和靜態成員函式的值傳回。 若要在 RAX 中的值所傳回的使用者定義型別，它的長度必須為 1、 2、 4、 8、 16、 32 或 64 位元。 它也必須擁有任何使用者定義的建構函式、 解構函式或複製指派運算子;沒有私人或受保護的非靜態資料成員;參考型別; 沒有任何非靜態資料成員沒有基底類別;沒有虛擬函式;並沒有也不符合這些需求的資料成員。 (這基本上是 C++03 POD 類型的定義。 在 C + + 11 標準，定義已變更，因為我們不建議使用`std::is_pod`這項測試。)否則，呼叫端會負責配置記憶體，並且為傳回值傳遞一個指標做為第一個引數。 後續的引數將向右移一個引數。 在 RAX 中的被呼叫端必須傳回相同的指標。

這些範例展示有指定之宣告的函式如何傳遞參數和傳回值：

### <a name="example-of-return-value-1---64-bit-result"></a>傳回值 1-64 位元結果的範例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>傳回值 2-128 位元結果的範例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>傳回值 3-由指標產生使用者類型結果的範例

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>傳回值 4-依值的使用者類型結果的範例

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器

暫存器 RAX、 RCX、 RDX、 R8，R9、 R10、 R11 會視為 volatile 和視為必須終結函式呼叫 (除非否則安全-可證明之分析整個程式最佳化 」 等)。

暫存器 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 會被視為靜態的而且必須儲存和還原函式使用它們。

## <a name="function-pointers"></a>函式指標

函式指標是只需標籤的個別函式的指標。 不有任何資料表的函式指標的目錄 (TOC) 需求。

## <a name="floating-point-support-for-older-code"></a>舊版程式碼的浮點支援

MMX 和浮點堆疊暫存器 (MM0-MM7/ST0-ST7) 會保留在內容切換。 沒有任何明確的呼叫慣例，這些暫存器。 這些暫存器使用嚴格禁止在核心模式程式碼。

## <a name="fpcsr"></a>FpCsr

註冊狀態也會包含 x87 FPU 控制字組。 呼叫慣例會要求此暫存器為靜態。

X87 FPU 控制字組暫存器設為下列的標準值開頭的程式執行：

| 註冊\[位元] | 設定 |
|-|-|
| FPCSR\[0:6] | 例外狀況遮罩所有 1 的 （加上遮罩的所有例外狀況） |
| FPCSR\[7] | 保留-0 |
| FPCSR\[8:9] | 精確度控制-10B （雙精確度） |
| FPCSR\[10:11] | 捨入控制-0 （四捨五入至最接近） |
| FPCSR\[12] | 無限大控制項-0 （未使用） |

修改任何 fpcsr 欄位被呼叫端必須將它們還原，然後傳回給其呼叫端。 此外，修改這些欄位的任何呼叫端必須將它們還原至其標準的值之前叫用被呼叫端，除非由合約被呼叫端必須要有修改過的值。

有兩個規則的例外狀況為非變動性的相關的控制旗標：

1. 在函式中指定的函式的文件的目的為修改靜態 FpCsr 旗標。

1. 當它可以證明是更正這些規則的違規會導致行為與這些規則不違反規則的程式，例如，透過整個程式分析相同的程式。

## <a name="mxcsr"></a>MxCsr

註冊狀態也會包含 MxCsr。 呼叫慣例會將此註冊分成變動性的部分和靜態部分。 動態部分所組成的六個狀態旗標，在 MXCSR\[0:5]，而其餘的 MXCSR 暫存器，\[6:15]，會被視為靜態。

靜態部分設為下列的標準值開頭的程式執行：

| 註冊\[位元] | 設定 |
|-|-|
| MXCSR\[6] | Denormals 是 0-0 |
| MXCSR\[7:12] | 例外狀況遮罩所有 1 的 （加上遮罩的所有例外狀況） |
| MXCSR\[13:14] | 捨入控制-0 （四捨五入至最接近） |
| MXCSR\[15] | 排清到零遮罩反向溢位-0 （關閉） |

修改的任何靜態欄位 mxcsr 被呼叫端必須將它們還原，然後傳回給其呼叫端。 此外，修改這些欄位的任何呼叫端必須將它們還原至其標準的值之前叫用被呼叫端，除非由合約被呼叫端必須要有修改過的值。

有兩個規則的例外狀況為非變動性的相關的控制旗標：

- 在函式中指定的函式的文件的目的為修改靜態 MxCsr 旗標。

- 當它可以證明是更正這些規則的違規會導致行為與這些規則不違反規則的程式，例如，透過整個程式分析相同的程式。

除非特別說明函式的文件中做任何限制性規定可以不進行跨函式界限，變動部分的 MXCSR 狀態相關。

## <a name="setjmplongjmp"></a>setjmp/longjmp

當您包含 setjmpex.h 或 setjmp.h 時，所有呼叫[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)導致叫用解構函式回溯和`__finally`呼叫。  這不同於 x86，包括 setjmp.h 會導致`__finally`子句和解構函式不被叫用。

呼叫`setjmp`會保留目前的堆疊指標、 非靜態暫存器中，與 MxCsr 暫存器。  若要呼叫`longjmp`返回最近`setjmp`呼叫站台和重設堆疊指標、 靜態暫存器和 MxCsr 暫存器，為狀態為保留的最新`setjmp`呼叫。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)
