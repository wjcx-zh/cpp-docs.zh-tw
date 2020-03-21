---
title: x64 呼叫慣例
description: 預設 x64 ABI 呼叫慣例的詳細資料。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 5b9801eff6a9789313d083fdd6ed69c3076643ad
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078074"
---
# <a name="x64-calling-convention"></a>x64 呼叫慣例

本節說明一個函式（呼叫者）用來對 x64 程式碼中的另一個函式（被呼叫端）進行呼叫的標準進程和慣例。

## <a name="calling-convention-defaults"></a>呼叫慣例預設值

X64 應用程式二進位介面（ABI）預設會使用四個註冊的快速呼叫呼叫慣例。 在呼叫堆疊上配置空間做為被呼叫端的陰影存放區，以儲存這些暫存器。 函式呼叫的引數與用於這些引數的暫存器之間，有一個嚴格的一對一對應。 不符合8個位元組，或不是1、2、4或8個位元組的任何引數，都必須以傳址方式傳遞。 單一引數永遠不會散佈到多個暫存器中。 X87 暫存器堆疊未使用，可供被呼叫端使用，但必須在函式呼叫中被視為 volatile。 所有的浮點運算都是使用16個 XMM 暫存器來完成。 整數引數會在暫存器 RCX、RDX、R8 和 R9 中傳遞。 浮點引數會以 XMM0L、XMM1L、XMM2L 和 XMM3L 傳遞。 16位元組引數是以傳址方式傳遞。 參數傳遞中會詳細說明參數[傳遞。](#parameter-passing) 除了這些暫存器以外，RAX、R10、R11、XMM4 和 XMM5 都會被視為 volatile。 所有其他暫存器都是不可變動的。 註冊使用方式記載于[註冊使用方式](../build/x64-software-conventions.md#register-usage)和[呼叫者/被](#callercallee-saved-registers)呼叫端儲存的暫存器中。

若為原型函式，所有引數都會先轉換成預期的被呼叫端類型，然後才傳遞。 呼叫端負責將參數的空間配置給被呼叫端，而且必須一律配置足夠的空間來儲存四個暫存器參數，即使被呼叫端不接受這許多參數也一樣。 此慣例可簡化沒有原型 C 語言函式和 vararg C/C++函數的支援。 對於 vararg 或沒有原型函數，任何浮點值都必須在對應的一般用途暫存器中重複。 在呼叫之前，在陰影存放區之後，必須將前四個以外的任何參數儲存在堆疊上。 Vararg 函數詳細資料可以在[Varargs](#varargs)中找到。 [沒有原型](#unprototyped-functions)函式中會詳細說明沒有原型函數資訊。

## <a name="alignment"></a>Alignment

大部分的結構會對齊其自然對齊方式。 主要的例外狀況是堆疊指標和 `malloc` 或 `alloca` 記憶體，其會對齊16個位元組，以協助效能。 超過16個位元組的對齊必須手動完成，但由於 XMM 作業的一般對齊大小是16個位元組，所以這個值應該適用于大部分的程式碼。 如需結構配置和對齊的詳細資訊，請參閱[類型和儲存體](../build/x64-software-conventions.md#types-and-storage)。 如需堆疊版面配置的詳細資訊，請參閱[x64 stack 使用](../build/stack-usage.md)方式。

## <a name="unwindability"></a>Unwindability

分葉函數是不會變更任何非 volatile 暫存器的函式。 非分葉函式可能會變更非變動性的 .RSP，例如，藉由呼叫函式或為區域變數配置額外的堆疊空間。 若要在處理例外狀況時復原非暫時性暫存器，必須以靜態資料標注非分葉函式，其描述如何在任意指令中適當地回溯函數。 這項資料會儲存為*pdata*，而程式資料則是指例外狀況處理資料的 *.xdata*。 .Xdata 包含回溯資訊，而且可以指向其他 pdata 或例外狀況處理常式函式。 初構和 epilogs 受到嚴格限制，因此可以在 .xdata 中適當地加以描述。 堆疊指標必須對齊不屬於終解或初構的任何程式碼區域中的16個位元組，但分葉函數內除外。 分葉函數可以藉由模擬傳回來進行展開，因此不需要 pdata 和 .xdata。 如需函式初構和 epilogs 之適當結構的詳細資訊，請參閱 x64 初構[和](../build/prolog-and-epilog.md)終解。 如需例外狀況處理的詳細資訊，以及 pdata 和 .xdata 的例外狀況處理和回溯，請參閱[x64 例外狀況處理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>參數傳遞

前四個整數引數會在暫存器中傳遞。 整數值會分別在 RCX、RDX、R8 和 R9 中以由左至右的順序傳遞。 五個以上的引數會在堆疊上傳遞。 所有引數都在暫存器中靠右對齊，因此被呼叫者可以忽略暫存器的上限，並只存取必要的暫存器部分。

前四個參數中的任何浮點和雙精確度引數會在 XMM0-XMM3 中傳遞，視位置而定。 除非在 varargs 引數的情況下，否則會忽略那些位置通常會使用的 RCX、RDX、R8 和 R9 的整數。 如需詳細資訊，請參閱[Varargs](#varargs)。 同樣地，當對應的引數是整數或指標類型時，會忽略 XMM0-XMM3 暫存器。

立即的值永遠不會傳遞[__m128](../cpp/m128.md)類型、陣列和字串。 相反地，指標會傳遞至呼叫端所配置的記憶體。 大小8、16、32或64位的結構和聯集，以及 __m64 類型，會如同相同大小的整數一樣傳遞。 其他大小的結構或等位會以指標的形式傳遞給呼叫端所配置的記憶體。 針對當做指標傳遞的這些匯總類型（包括 \__m128），呼叫端配置的暫存記憶體必須是16個位元組的對齊。

內建函式不會配置堆疊空間，也不會呼叫其他函式，有時會使用其他 volatile 暫存器來傳遞額外的暫存器引數。 編譯器與內建函式執行之間的緊密系結可以達成這項優化。

被呼叫端會負責將暫存器參數傾印到其陰影空間（如有需要）。

下表摘要說明如何傳遞參數：

|參數類型|傳遞方式|
|--------------------|----------------|
|浮點數|前4個參數-XMM0 至 XMM3。 堆疊上傳遞的其他專案。|
|整數|前4個參數-RCX、RDX、R8、R9。 堆疊上傳遞的其他專案。|
|匯總（8、16、32或64位）和 __m64|前4個參數-RCX、RDX、R8、R9。 堆疊上傳遞的其他專案。|
|匯總（其他）|By 指標。 在 RCX、RDX、R8 和 R9 中傳遞為指標的前4個參數|
|__m128|By 指標。 在 RCX、RDX、R8 和 R9 中傳遞為指標的前4個參數|

### <a name="example-of-argument-passing-1---all-integers"></a>傳遞 1-所有整數的引數範例

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>傳遞 2-全部浮點數的引數範例

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>傳遞3混合整數和浮點數的引數範例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>傳遞 4 __m64、\__m128 和匯總之引數的範例

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果透過 varargs 傳遞參數（例如，省略號引數），則會套用一般的 register 參數傳遞慣例，包括溢出堆疊的第五個和後續引數。 被呼叫者負責傾印其位址所採用的引數。 僅針對浮點值，如果被呼叫端預期整數暫存器中的值，則整數暫存器和浮點數暫存器都必須包含值。

## <a name="unprototyped-functions"></a>沒有原型函式

對於不是完全原型的函式，呼叫端會將整數值當做整數和浮點值，以雙精確度的方式傳遞。 僅針對浮點值，當被呼叫端預期整數暫存器中的值時，整數暫存器和浮點暫存器都會包含 float 值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>傳回值

可放入64位的純量傳回值會透過 RAX 傳回;這包括 __m64 類型。 包含浮點數、雙精確度和向量類型的非純量類型（例如[__m128](../cpp/m128.md)、 [__m128i](../cpp/m128i.md)、 [__m128d](../cpp/m128d.md)會在 XMM0 中傳回。 對於 RAX 或 XMM0 中傳回的值，其中未使用之位元的狀態尚未定義。

使用者定義的類型可透過全域函式和靜態成員函式的值傳回。 若要在 RAX 中以傳值方式傳回使用者定義型別，它的長度必須是1、2、4、8、16、32或64位。 它也必須沒有使用者定義的函式、析構函數或複製指派運算子;沒有私用或受保護的非靜態資料成員;沒有參考型別的非靜態資料成員;沒有基類;沒有虛擬函式;而且沒有任何資料成員也不符合這些需求。 (這基本上是 C++03 POD 類型的定義。 因為 c + + 11 標準中的定義已變更，所以不建議在此測試中使用 `std::is_pod`）。否則，呼叫者會負責配置記憶體，並將傳回值的指標當做第一個引數來傳遞。 後續的引數將向右移一個引數。 在 RAX 中的被呼叫端必須傳回相同的指標。

這些範例展示有指定之宣告的函式如何傳遞參數和傳回值：

### <a name="example-of-return-value-1---64-bit-result"></a>傳回值 1-64 位結果的範例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>傳回值 2-128 位結果的範例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>傳回值3的範例-依指標的使用者類型結果

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>傳回值4的範例-依值區分的使用者類型結果

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>呼叫端/被呼叫端儲存的暫存器

暫存器 RAX、RCX、RDX、R8、R9、R10、R11、XMM0-5 以及 YMM0-15 和 ZMM0-15 的上半部視為 volatile，而且必須被視為在函式呼叫上終結（除非以整個程式優化之類的分析來進行安全且可證明）。 在 AVX512VL 上，ZMM、YMM 和 XMM 暫存器16-31 為 volatile。

暫存器 RBX、RBP、RDI、RSI、.RSP、R12、R13、R14、R15 和 XMM6-15 視為非易失，必須由使用它們的函式加以儲存和還原。

## <a name="function-pointers"></a>函式指標

函式指標只是個別函式標籤的指標。 函式指標沒有目錄（TOC）需求。

## <a name="floating-point-support-for-older-code"></a>舊版程式碼的浮點支援

會跨內容切換保留 MMX 和浮點堆疊暫存器（MM0-MM7/ST0-ST7）。 這些暫存器沒有明確的呼叫慣例。 在核心模式程式碼中，嚴格禁止使用這些暫存器。

## <a name="fpcsr"></a>FpCsr

註冊狀態也包含 x87 FPU 控制字組。 呼叫慣例會指示此暫存器為非靜態。

在程式執行開始時，x87 FPU 控制字暫存器會設定為下列標準值：

| 註冊\[位] | 設定 |
|-|-|
| FPCSR\[0:6] | 例外狀況遮罩全部1（所有例外狀況都會遮罩） |
| FPCSR\[7] | 已保留-0 |
| FPCSR\[8:9] | 精確度控制-通過（雙精確度） |
| FPCSR\[10:11] | 進位控制項-0 （四捨五入至最接近） |
| FPCSR\[12] | 無限大控制-0 （未使用） |

修改 FPCSR 內任何欄位的被呼叫端必須先還原，才能回到其呼叫者。 此外，除非被呼叫者預期修改過的值，否則，已修改任何欄位的呼叫者必須先將其還原成其標準值，然後再叫用被呼叫端。

控制旗標的非變動性規則有兩個例外：

1. 在函式中，指定函式的用途是修改非靜態 FpCsr 旗標。

1. 當可證明正確時，違反這些規則會產生一個程式，其行為與不違反這些規則的程式有關，例如透過整個程式分析。

## <a name="mxcsr"></a>MxCsr

註冊狀態也包括 MxCsr。 呼叫慣例會將此暫存器分成一個 volatile 部分和一個非靜態部分。 Volatile 部分包含六個狀態旗標（在 MXCSR\[0:5] 中），而註冊 MXCSR\[6:15] 的其餘部分則視為非易失。

在程式執行開始時，非靜態部分會設定為下列標準值：

| 註冊\[位] | 設定 |
|-|-|
| MXCSR\[6] | Denormals 為零-0 |
| MXCSR\[7:12] | 例外狀況遮罩全部1（所有例外狀況都會遮罩） |
| MXCSR\[13:14] | 進位控制項-0 （四捨五入至最接近） |
| MXCSR\[15] | 針對已遮罩的下溢-0 （關閉）清除為零 |

修改 MXCSR 內任何非靜態欄位的被呼叫端必須先還原它們，才能回到其呼叫端。 此外，除非被呼叫者預期修改過的值，否則，已修改任何欄位的呼叫者必須先將其還原成其標準值，然後再叫用被呼叫端。

控制旗標的非變動性規則有兩個例外：

- 在函式中，指定函式的用途是修改非靜態 MxCsr 旗標。

- 當可證明正確時，違反這些規則會產生一個程式，其行為與不違反這些規則的程式有關，例如透過整個程式分析。

除非函式的檔中有特別說明，否則不會對整個函式界限的 MXCSR 變動性部分進行任何假設。

## <a name="setjmplongjmp"></a>setjmp/longjmp

當您包含 setjmpex.h 或 setjmp 時，所有對[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)的呼叫都會導致叫用析構函數和 `__finally` 呼叫的回溯。  這與 x86 不同，其中包括 setjmp. h 會導致 `__finally` 子句和不被叫用的析構函數。

`setjmp` 的呼叫會保留目前的堆疊指標、非 volatile 暫存器和 MxCsr 暫存器。  呼叫 `longjmp` 會回到最近的 `setjmp` 呼叫網站，並將堆疊指標、非 volatile 暫存器和 MxCsr 暫存器重新設回最近 `setjmp` 呼叫所保留的狀態。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)
