---
title: x64 呼叫慣例
description: 預設 x64 ABI 調用約定的詳細資訊。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335136"
---
# <a name="x64-calling-convention"></a>x64 呼叫慣例

本節介紹一個函數(調用方)用於在 x64 代碼中調用另一個函數(被叫方)的標準進程和約定。

## <a name="calling-convention-defaults"></a>呼叫約定預設值

默認情況下,x64 應用程式二進位介面 (ABI) 使用四寄存器快速呼叫呼叫約定。 在調用堆疊上分配空間作為陰影存儲,供被調用方保存這些寄存器。 函數調用的參數與用於這些參數的寄存器之間有嚴格的一對一對應關係。 任何不適合 8 個字節或不是 1、2、4 或 8 位元組的參數都必須通過引用傳遞。 單個參數永遠不會跨多個寄存器分佈。 x87 寄存器堆疊未使用,可能被被調用者使用,但必須在函數調用之間被視為易失性。 所有浮點操作都使用 16 XMM 寄存器完成。 整數參數在寄存器 RCX、RDX、R8 和 R9 中傳遞。 浮點參數在 XMM0L、XMM1L、XMM2L 和 XMM3L 中傳遞。 16 位元組參數通過引用傳遞。 參數傳遞在[參數傳遞](#parameter-passing)中進行了詳細描述。 除了這些寄存器外,RAX、R10、R11、XMM4 和 XMM5 被認為是易揮發性的。 所有其他寄存器都是非易失性的。 寄存器使用方式在[註冊使用方式](../build/x64-software-conventions.md#register-usage)和[呼叫者/被叫者保存的寄存器](#callercallee-saved-registers)中詳細記錄。

對於原型函數,所有參數在傳遞之前都將轉換為預期的被叫者類型。 調用方負責為被調用方分配參數空間,並且必須始終分配足夠的空間來存儲四個寄存器參數,即使被調用方不採用那麼多參數也是如此。 此約定簡化了對未原型 C 語言函數和 vararg C/C++ 函數的支援。 對於 vararg 或未原型函數,必須在相應的通用寄存器中複製任何浮點值。 前四個以外的任何參數都必須在調用之前在捲影存儲之後存儲在堆疊上。 瓦拉格功能詳情可以在[瓦拉格找到](#varargs)。 未原型函數資訊在[未原型函數](#unprototyped-functions)中詳細說明。

## <a name="alignment"></a>Alignment

大多數結構與其自然對齊。 主要例外是堆疊指標和`malloc`或`alloca`記憶體,它們對齊為 16 個字節,以説明性能。 超過 16 個字節的對齊必須手動完成,但由於 16 個字節是 XMM 操作的常見對齊大小,此值應適用於大多數代碼。 有關結構佈局和對齊的詳細資訊,請參考[類型和儲存](../build/x64-software-conventions.md#types-and-storage)。 有關堆疊佈局的資訊,請參閱[x64 堆疊用法](../build/stack-usage.md)。

## <a name="unwindability"></a>可展開性

葉函數是不更改任何非易失寄存器的函數。 非葉函數可能會更改非易失性 RSP,例如,通過調用函數或為局部變數分配額外的堆疊空間。 為了在處理異常時恢復非易失寄存器,必須使用靜態數據來說明非葉函數,這些數據描述如何在任意指令下正確展開函數。 此資料儲存為*pdata*, 或程序資料, 反過來又指*xdata,* 異常處理資料. xdata 包含展開資訊,並可以指向其他 pdata 或異常處理程式函數。 Prologs 和表皮受到高度限制,因此可以在 xdata 中正確描述它們。 堆疊指標必須與不屬於表徵或 prolog 的任何代碼區域中的 16 個字節對齊,但葉函數中除外。 葉函數只需類比返回即可解覆,因此不需要 pdata 和 xdata。 有關函數序言和表徵的正確結構的詳細資訊,請參閱[x64 prolog 和 epilog](../build/prolog-and-epilog.md)。 有關例外處理以及 pdata 與 xdata 的例外處理與展開的詳細資訊,請參考[x64 例外處理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>參數傳遞

前四個整數參數在寄存器中傳遞。 整數值分別以 RCX、RDX、R8 和 R9 的從左至右順序傳遞。 參數 5 和更高版本在堆疊上傳遞。 所有參數在寄存器中都是正確的,因此被調用人可以忽略寄存器的上位,並且只訪問寄存器所需的部分。

前四個參數中的任何浮點和雙精度參數都以 XMM0 - XMM3 傳遞,具體取決於位置。 通常用於這些位置的整數寄存器 RCX、RDX、R8 和 R9 將被忽略,但 varargs 參數除外。 有關詳細資訊,請參閱[Varargs](#varargs)。 同樣,當相應的參數是整數或指標類型時,將忽略 XMM0 - XMM3 寄存器。

[__m128](../cpp/m128.md)類型、陣列和字串永遠不會通過即時值傳遞。 相反,指標將傳遞給調用方分配的記憶體。 大小 8、16、32 或 64 位元的結構並結合,以及__m64類型,傳遞它們就像大小相同的整數一樣傳遞。 其他大小的結構或聯合作為指標傳遞給調用方分配的記憶體。 對於作為指標傳遞的聚合類型(包括\__m128,調用方分配的臨時記憶體必須對齊 16 位元組。

不分配堆疊空間且不調用其他函數的內在函數,有時使用其他易失寄存器來傳遞其他寄存器參數。 編譯器和內部函數實現之間的緊密綁定使得這種優化成為可能。

如果需要,被調用人負責將寄存器參數轉儲到其陰影空間中。

下表總結了如何傳遞參數:

|參數類型|如何通過|
|--------------------|----------------|
|浮點|前 4 個參數 - XMM0 到 XMM3。 其他人在堆疊上傳遞。|
|整數|前 4 個參數 - RCX、RDX、R8、R9。 其他人在堆疊上傳遞。|
|聚合(8、16、32 或 64 位)和__m64|前 4 個參數 - RCX、RDX、R8、R9。 其他人在堆疊上傳遞。|
|聚合(其他)|按指標。 前 4 個參數在 RCX、RDX、R8 和 R9 中作為指標傳遞|
|__m128|按指標。 前 4 個參數在 RCX、RDX、R8 和 R9 中作為指標傳遞|

### <a name="example-of-argument-passing-1---all-integers"></a>參數傳遞 1 的範例 ─所有整數

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>參數傳遞 2 的範例 ─所有浮點

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>參數傳遞 3 - 混合 int 與 floats 的範例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>透過 4-__m64、_m128\_和聚合的參數範例

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果參數通過 varargs 傳遞(例如,省略號參數),則應用正常的寄存器參數傳遞約定,包括將第五個和後續參數溢出到堆疊中。 被調用人有責任轉儲具有其地址的參數。 對於僅浮點值,整數寄存器和浮點寄存器都必須包含該值,以防被叫者期望在整數寄存器中的值。

## <a name="unprototyped-functions"></a>未原型函數

對於未完全原型的函數,調用方將整數值作為整數和浮點值作為雙精度傳遞。 對於僅浮點值,整數寄存器和浮點寄存器都包含浮點值,以防被叫者期望在整數寄存器中的值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>傳回值

可放入 64 位的標量返回值通過 RAX 返回;這包括__m64類型。 非標量類型(包括浮點、雙精度值和向量類型(如[__m128、__m128i、__m128d)](../cpp/m128i.md)在 XMM0[__m128](../cpp/m128.md)[__m128d](../cpp/m128d.md)中返回。 對於 RAX 或 XMM0 中傳回的值，其中未使用之位元的狀態尚未定義。

使用者定義的類型可透過全域函式和靜態成員函式的值傳回。 要按 RAX 中的值返回使用者定義的類型,它必須具有 1、2、4、8、16、32 或 64 位的長度。 它還必須沒有使用者定義的構造函數、析構函數或複製賦值運算符;沒有私有或受保護的非靜態數據成員;沒有引用類型的非靜態數據成員;無基類;無虛擬函數;並且沒有也不符合這些要求的數據成員。 (這基本上是 C++03 POD 類型的定義。 由於定義在 C++11 標準中已更改,因此我們不建議`std::is_pod`使用此 測試。否則,調用方承擔分配記憶體和傳遞返回值的指標作為第一個參數的責任。 後續的引數將向右移一個引數。 在 RAX 中的被呼叫端必須傳回相同的指標。

這些範例展示有指定之宣告的函式如何傳遞參數和傳回值：

### <a name="example-of-return-value-1---64-bit-result"></a>傳回值 1 - 64 位元的範例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>傳回值 2 - 128 位元結果的範例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>傳回值 3 - 使用者類型結果 (指標) 的範例

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>傳回值 4 範例 - 按值計算的使用者類型結果

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>呼叫者/被叫者儲存的寄存器

寄存器 RAX、RCX、RDX、R8、R9、R10、R11、XMM0-5 以及 YMM0-15 和 ZMM0-15 的上部被視為易失性,必須在函數調用時被視為銷毀(除非通過分析(如整個程序優化)進行安全證明)。 在 AVX512VL 上,ZMM、YMM 和 XMM 寄存器 16-31 是不穩定的。

寄存器 RBX、RBP、RDI、RSI、RSP、R12、R13、R14、R15 和 XMM6-15 被視為非易失性寄存器,必須通過使用它們的函數進行保存和恢復。

## <a name="function-pointers"></a>函式指標

函數指標只是指向相應函數標籤的指標。 函數指標沒有目錄 (TOC) 要求。

## <a name="floating-point-support-for-older-code"></a>對舊代碼的浮點支援

MMX 和浮點堆疊寄存器 (MM0-MM7/ST0-ST7) 跨上下文開關保留。 這些寄存器沒有顯式調用約定。 在內核模式代碼中嚴禁使用這些寄存器。

## <a name="fpcsr"></a>FpCsr

寄存器狀態還包括 x87 FPU 控制字。 調用約定指示此寄存器是非易失性的。

x87 FPU 控制字寄存器在程式執行開始時設定為以下標準值:

| 註冊\[位* | 設定 |
|-|-|
| FPCSR\[0:6] | 例外遮罩所有 1(所有例外都已遮罩) |
| FPCSR\[7* | 保留 - 0 |
| FPCSR\[8:9] | 精密控制 - 10B(雙精度) |
| FPCSR\[10:11* | 進爾控制 - 0(捨入到最近) |
| FPCSR\[12* | 無限控制 - 0(未使用) |

修改 FPCSR 中任何欄位的被調用方必須先還原這些欄位,然後才能返回到其調用方。 此外,已修改這些欄位中的任何一個的調用方必須在調用被叫方之前將它們還原到其標準值,除非通過協定被叫方希望修改值。

關於控制標誌的非波動性的規則有兩個例外:

1. 在給定函數的記錄用途是修改非易失性 FpCsr 標誌的函數中。

1. 當證明違反這些規則會導致程序的行為與程序的行為相同時,例如,通過整個程式分析,這些程序的行為與程式相同。

## <a name="mxcsr"></a>MxCsr

寄存器狀態還包括 MxCsr。 調用約定將此寄存器劃分為易失性部分和非易失性部分。 易失性部分由 MXCSR\[0:5+ 中的六個狀態標誌組成,而寄存器的其餘部分 MXCSR\[6:15] 則被視為非易失性標誌。

在程式執行開始時,非易失性部分設定為以下標準值:

| 註冊\[位* | 設定 |
|-|-|
| MXCSR\[6* | 非正常值為零 - 0 |
| MXCSR\[7:12] | 例外遮罩所有 1(所有例外都已遮罩) |
| MXCSR\[13:14* | 進爾控制 - 0(捨入到最近) |
| MXCSR\[15* | 將已刷新到零 - 0 (關閉) |

修改 MXCSR 中任何非易失性欄位的被調用方必須先還原這些欄位,然後才能返回到其調用方。 此外,已修改這些欄位中的任何一個的調用方必須在調用被叫方之前將它們還原到其標準值,除非通過協定被叫方希望修改值。

關於控制標誌的非波動性的規則有兩個例外:

- 在給定函數的記錄用途是修改非易失性 MxCsr 標誌的函數中。

- 當證明違反這些規則會導致程序的行為與程序的行為相同時,例如,通過整個程式分析,這些程序的行為與程式相同。

除非函數的文檔中具體描述,否則無法對跨函數邊界的 MXCSR 易失性部分的狀態做出任何假設。

## <a name="setjmplongjmp"></a>塞特詹普/隆詹姆

當您包括 setjmpex.h 或 setjmp.h 時,所有對[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)的調用都會導致`__finally`展開,從而調用析構函數和調用。  這與 x86 不同,其中包含 setjmp.h`__finally`會導致不調用子句和析構函數。

保留`setjmp`當前堆疊指標、非易失寄存器和 MxCsr 寄存器的呼叫。  調用以`longjmp`返回到`setjmp`最新的 調用網站並重置堆疊指標、非易失寄存器和 MxCsr 寄存器,返回`setjmp`到最近 調用保留的狀態。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)
