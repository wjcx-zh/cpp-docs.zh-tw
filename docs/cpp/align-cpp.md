---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 0a1212f1c78f49029f82be5a2f5d82ea1788b6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227656"
---
# <a name="align-c"></a>align (C++)

在 Visual Studio 2015 和更新版本中，請使用 c + + 11 標準 **`alignas`** 規範來控制對齊。 如需詳細資訊，請參閱[對齊](../cpp/alignment-cpp-declarations.md)。

**Microsoft 特定的**

使用 `__declspec(align(#))` 可精確控制使用者定義資料的對齊 (例如，靜態配置或函式中的自動資料)。

## <a name="syntax"></a>語法

> **__declspec （align （** *#* **））** *declarator*宣告子

## <a name="remarks"></a>備註

撰寫使用最新處理器指令的應用程式會帶來一些新的限制和問題。 許多新的指示需要與16位元組界限對齊的資料。 此外，藉由將經常使用的資料與處理器的快取行大小進行對齊，您可以改善快取效能。 例如，如果您定義的結構的大小小於32個位元組，您可能會想要32位元組對齊，以確保能夠有效率地快取該結構類型的物件。

\#這是對齊值。 有效項目是從 1 至 8192 (位元組) 的 2 乘冪整數，例如 2、4、8、16、32 或 64。 `declarator`這是您要宣告為對齊的資料。

如需如何傳回類型值（ `size_t` 這是類型的對齊需求）的詳細資訊，請參閱 [`alignof`](../cpp/alignof-operator.md) 。 如需如何在以64位處理器為目標時宣告未對齊指標的詳細資訊，請參閱 [`__unaligned`](../cpp/unaligned.md) 。

`__declspec(align(#))`當您定義 **`struct`** 、 **`union`** 或 **`class`** 時，或在宣告變數時，可以使用。

在複製或資料轉換作業期間，編譯器不保證或會嘗試保留資料的對齊屬性。 例如， [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) 可以將使用宣告的結構複製 `__declspec(align(#))` 到任何位置。 一般配置器（例如， [`malloc`](../c-runtime-library/reference/malloc.md) 、c + + [`operator new`](new-operator-cpp.md) 和 Win32 配置器）通常會傳回對 `__declspec(align(#))` 結構或結構陣列而言不夠的記憶體。 若要保證複製或資料轉換作業的目的地正確對齊，請使用 [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) 。 或者，撰寫您自己的配置器。

您無法指定函數參數的對齊方式。 當您以堆疊上的值來傳遞具有對齊屬性的資料時，其對齊方式會由呼叫慣例控制。 如果資料對齊在呼叫的函式中很重要，請將參數複製到正確對齊的記憶體中，才使用該參數。

`__declspec(align(#))`若沒有，編譯器通常會根據目標處理器和資料大小，將資料對齊自然界限，在32位處理器上最多4位元組的界限，64位處理器上的8位元組界限。 類別或結構中的資料會以其自然對齊和目前封裝設定（來自 `#pragma pack` 或編譯器選項）的最小程度，在類別或結構中對齊 `/Zp` 。

這個範例會示範 `__declspec(align(#))` 的使用方式。

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

這個類型現在具有 32 位元組對齊屬性。 這表示所有的靜態和自動實例都是在32位元組的界限上啟動。 以這個類型做為成員宣告的其他結構類型會保留這個類型的對齊屬性，也就是說，任何以 `Str1` 元素做為專案的結構都具有至少32的對齊屬性。

在這裡， `sizeof(struct Str1)` 等於32。 這表示如果建立物件的陣列 `Str1` ，而且陣列的基底為32位元組對齊，則陣列的每個成員也會對齊32位元組。 若要在動態記憶體中建立基底正確對齊的陣列，請使用 [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) 。 或者，撰寫您自己的配置器。

**`sizeof`** 任何結構的值都是最後一個成員的位移，加上該成員的大小，進位到最大成員對齊值的最接近倍數，或整個結構對齊值（以較大者為准）。

編譯器會為結構對齊使用這些規則：

- 除非以 `__declspec(align(#))` 覆寫，否則純量結構成員的對齊是其大小與目前封裝的最小值。

- 除非以 `__declspec(align(#))` 覆寫，否則結構的對齊是其成員的個別對齊最大值。

- 結構成員位於其父結構開頭的位移，這是其對齊的最小倍數大於或等於前一個成員結尾的位移。

- 結構的大小是其對齊的最小倍數 (大於或等於其最後一個成員結尾的位移)。

`__declspec(align(#))` 只能增加對齊限制。

如需詳細資訊，請參閱

- [`align`典型](#vclrfalignexamples)

- [使用定義新類型`__declspec(align(#))`](#vclrf_declspecaligntypedef)

- [對齊執行緒區域儲存區中的資料](#vclrfthreadlocalstorageallocation)

- [如何處理 `align` 資料封裝](#vclrfhowalignworkswithdatapacking)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)（x64 專用）

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>對齊範例

下列範例說明 `__declspec(align(#))` 如何影響資料結構的大小和對齊。 這個範例會假設下列定義：

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

在這個範例中，`S1` 結構使用 `__declspec(align(32))` 定義。 針對變數定義使用的所有 `S1`，或其他類型宣告中，都是對齊 32 位元組。 `sizeof(struct S1)` 會傳回 32，而且 `S1` 在保留四個整數所需的 16 個位元組後面會有 16 個填補位元組。 每個 **`int`** 成員需要4位元組對齊，但是結構本身的對齊會宣告為32。 然後，整體的對齊方式為32。

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

在下列範例中，`sizeof(struct S2)` 會傳回 16，也就是成員大小的總和，因為這剛好是最大對齊需求的倍數 (8 倍)。

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

在下列範例中，`sizeof(struct S3)` 會傳回 64。

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

在這個範例中，請注意 `a` 有其自然類型的對齊，在此情況下，為 4 個位元組。 不過，`S1` 必須對齊 32 位元組。 會跟隨28個位元組的填補 `a` ，因此 `s1` 從位移32開始。 `S4`接著會繼承的對齊需求 `S1` ，因為它是結構中最大的對齊需求。 `sizeof(struct S4)` 會傳回 64。

```cpp
struct S4 {
   int a;
   // 28 bytes padding
   struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

下列三個變數宣告也會使用 `__declspec(align(#))`。 在每個案例中，變數必須對齊 32 位元組。 在陣列中，陣列的基底位址（而不是每個陣列成員）會對齊32位元組。 **`sizeof`** 當您使用時，每個陣列成員的值不會受到影響 `__declspec(align(#))` 。

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

若要對齊陣列的每個成員，應使用如下的程式碼：

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

在這個範例中，請注意對齊結構本身和對齊第一個元素都有相同的效果：

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` 和 `S7` 具有相同的對齊、配置和大小特性。

在下列範例中，a、b、c 和 d 的對齊開始位址分別為 4、1、4 和 1。

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

如果已在堆積上配置記憶體，則對齊會取決於所呼叫的配置函式。  例如，如果您使用 `malloc`，則結果會取決於運算元大小。 如果*arg* >= 8，則傳回的記憶體會對齊8位元組。 如果*arg* < 8，則傳回的記憶體的對齊會是小於*arg*之2的第一個乘冪。 例如，如果您使用 `malloc(7)` ，則對齊是4個位元組。

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>使用定義新類型`__declspec(align(#))`

您可以定義具有對齊特性的類型。

例如，您可以透過下列 **`struct`** 方式定義具有對齊值的：

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

現在 `aType` 和 `bType` 都是相同的大小（8個位元組），但類型的變數 `bType` 會對齊32位元組。

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>對齊線程區域儲存區中的資料

使用 `__declspec(thread)` 屬性建立並放入影像之 TLS 區段的靜態執行緒區域儲存區 (TLS) 可用於對齊，就像一般靜態資料一樣。 為了建立 TLS 資料，作業系統會配置記憶體的 TLS 區段大小，並接受 TLS 區段對齊屬性。

此範例示範各種將對齊的資料放入執行緒區域儲存區中的方式。

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>如何處理 `align` 資料封裝

`/Zp`編譯器選項和 `pack` pragma 會影響結構和等位成員的資料封裝。 這個範例會示範 `/Zp` 和如何 `__declspec(align(#))` 共同作業：

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

下表列出每個成員在不同 `/Zp` （或）值下的位移 `#pragma pack` ，顯示這兩個互動的方式。

|變數|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

如需詳細資訊，請參閱[ `/Zp` （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)。

因此，物件的位移是根據前一個物件的位移與目前封裝設定，但如果物件具有 `__declspec(align(#))` 屬性，情況就不是這樣，此時對齊是根據前一個物件的位移與物件的 `__declspec(align(#))` 值。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[`__declspec`](../cpp/declspec.md)<br/>
[ARM ABI 慣例總覽](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 軟體慣例](../build/x64-software-conventions.md)
