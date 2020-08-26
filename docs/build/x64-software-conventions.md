---
title: x64 軟體慣例
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 7c47ec86e80b50bb2b313a2c84a3f375681e2870
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838824"
---
# <a name="x64-software-conventions"></a>x64 軟體慣例

本節說明 x64 的 c + + 呼叫慣例方法，這是 x86 架構的64位延伸模組。

## <a name="overview-of-x64-calling-conventions"></a>X64 呼叫慣例總覽

X86 與 x64 之間有兩個重要的差異：64位的定址功能，以及一組一般的 16 64 位暫存器，供一般使用。 由於有擴充的暫存器集，因此 x64 使用 [__fastcall](../cpp/fastcall.md) 呼叫慣例和 RISC 型例外狀況處理模型。 **`__fastcall`** 慣例會針對前四個引數使用暫存器，並使用堆疊框架傳遞額外的引數。 如需 x64 呼叫慣例的詳細資訊，包括註冊使用方式、堆疊參數、傳回值和堆疊回溯，請參閱 [x64 呼叫慣例](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>啟用 x64 的優化

下列編譯器選項可協助您優化 x64 的應用程式：

- [/favor (針對架構細節優化) ](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>類型和儲存體

本節說明 x64 架構之資料類型的列舉和儲存。

### <a name="scalar-types"></a>純量類型

雖然可以存取任何對齊的資料，但建議您將資料對齊其自然界限（或多個），以避免效能遺失。 列舉是常數整數，而且會被視為32位整數。 下表描述型別定義和建議的資料儲存空間，因為它與使用下列對齊值的對齊方式有關：

- 位元組-8 位

- Word-16 位

- 雙全半形-32 位

- 四位元組-64 位

- Octaword-128 位

|純量類型|C 資料類型|儲存體大小 (位元組) |建議的對齊|
|-|-|-|-|
|**`INT8`**|**`char`**|1|Byte|
|**`UINT8`**|**`unsigned char`**|1|Byte|
|**`INT16`**|**`short`**|2|Word|
|**`UINT16`**|**`unsigned short`**|2|Word|
|**`INT32`**|**`int`**, **`long`**|4|長|
|**`UINT32`**|**`unsigned int`**, **`unsigned long`**|4|長|
|**`INT64`**|**`__int64`**|8|字|
|**`UINT64`**|**`unsigned __int64`**|8|字|
|**`FP32`** (單一精確度) |**`float`**|4|長|
|**`FP64`** (雙精確度) |**`double`**|8|字|
|**`POINTER`**|__\*__|8|字|
|**`__m64`**|**`struct __m64`**|8|字|
|**`__m128`**|**`struct __m128`**|16|Octaword|

### <a name="aggregates-and-unions"></a>匯總和等位

其他類型（例如陣列、結構和等位）具有嚴格的對齊需求，以確保一致的匯總和聯集儲存和資料抓取。 以下是 array、structure 和 union 的定義：

- Array

   包含相鄰資料物件的已排序群組。 每個物件都稱為 *元素*。 陣列中的所有元素都有相同的大小和資料類型。

- 結構

   包含資料物件的已排序群組。 不同于陣列的元素，結構內的資料物件可以有不同的資料類型和大小。 結構中的每個資料物件都稱為 *成員*。

- Union

   物件，其中包含一組命名成員的任何一個。 命名集的成員可以是任何類型。 配置給聯集的儲存區等於該聯集最大成員所需的儲存空間，以及對齊所需的任何填補。

下表顯示等位和結構的純量成員強烈建議的對齊方式。

|純量類型|C 資料類型|需要的對齊|
|-|-|-|
|**`INT8`**|**`char`**|Byte|
|**`UINT8`**|**`unsigned char`**|Byte|
|**`INT16`**|**`short`**|Word|
|**`UINT16`**|**`unsigned short`**|Word|
|**`INT32`**|**`int`**, **`long`**|長|
|**`UINT32`**|**`unsigned int`**, **`unsigned long`**|長|
|**`INT64`**|**`__int64`**|字|
|**`UINT64`**|**`unsigned __int64`**|字|
|**`FP32`** (單一精確度) |**`float`**|長|
|**`FP64`** (雙精確度) |**`double`**|字|
|**`POINTER`**|<strong>\*</strong>|字|
|**`__m64`**|**`struct __m64`**|字|
|**`__m128`**|**`struct __m128`**|Octaword|

下列匯總對齊規則適用：

- 陣列的對齊方式與陣列中其中一個元素的對齊方式相同。

- 結構或等位開頭的對齊方式是任何個別成員的最大對齊。 結構或等位中的每個成員都必須依照上表中的定義來放置適當的對齊，視先前的成員而定，可能需要隱含的內部填補。

- 結構大小必須是其對齊的整數倍數，可能需要在最後一個成員之後填入。 由於結構和等位可以分組于陣列中，結構或等位的每個陣列元素都必須在先前決定的適當對齊下開始和結束。

- 只要維持先前的規則，就可以將資料對齊，使其大於對齊需求。

- 個別編譯器可能會基於大小的原因調整結構的封裝。 例如 [/Zp (結構成員對齊) ](../build/reference/zp-struct-member-alignment.md) 可讓您調整結構的封裝。

### <a name="examples-of-structure-alignment"></a>結構對齊範例

下列四個範例分別會宣告對齊的結構或等位，而對應的圖表說明記憶體中該結構或聯集的版面配置。 圖中的每個資料行都代表一個位元組的記憶體，而資料行中的數位表示該位元組的位移。 每個圖表的第二個數據列中的名稱會對應到宣告中的變數名稱。 網底資料行表示完成指定對齊所需的填補。

#### <a name="example-1"></a>範例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 轉換範例1結構版面配置](../build/media/vcamd_conv_ex_1_block.png "AMD 轉換範例1結構版面配置")

#### <a name="example-2"></a>範例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 轉換範例2結構版面配置](../build/media/vcamd_conv_ex_2_block.png "AMD 轉換範例2結構版面配置")

#### <a name="example-3"></a>範例 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![AMD 轉換範例2結構版面配置](../build/media/vcamd_conv_ex_3_block.png "AMD 轉換範例2結構版面配置")

#### <a name="example-4"></a>範例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 轉換範例4聯集 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 轉換範例4聯集 layouit")

### <a name="bitfields"></a>位元欄位

結構位欄位的限制為64位，而且可以是類型帶正負號的 int、不帶正負號的 int、int64 或未簽署的 int64。 跨越型別界限的位欄位將會略過位，以將等位對齊下一個型別對齊。 例如，整數位欄位可能不會跨越32位的 boundry。

### <a name="conflicts-with-the-x86-compiler"></a>與 x86 編譯器衝突

當您使用 x86 編譯器來編譯應用程式時，大於4個位元組的資料類型不會自動對齊堆疊。 因為 x86 編譯器的架構是4位元組對齊的堆疊，所以大於4個位元組的任何字元（例如64位整數）都無法自動對齊8位元組的位址。

使用未對齊的資料有兩個含意。

- 存取未對齊的位置可能需要較長的時間，而不是存取對齊位置所需要的位置。

- 未對齊的位置無法在連鎖作業中使用。

如果您需要更嚴格的對齊，請在變數宣告中使用 `__declspec(align(N))` 。 這會導致編譯器動態對齊堆疊以符合您的規格。 不過，在執行時間動態調整堆疊，可能會導致應用程式執行速度變慢。

## <a name="register-usage"></a>註冊使用量

X64 架構會提供16個一般用途的暫存器 (稍後稱為整數暫存器) ，以及16個可供浮點數使用的 XMM/YMM 暫存器。 動態暫存器是臨時暫存器，由呼叫者假設為跨呼叫終結。 需要靜態暫存器才能跨函式呼叫保留其值，且靜態暫存器必須由被呼叫者 (如果使用的話) 儲存。

### <a name="register-volatility-and-preservation"></a>註冊變動性與保留

下表描述如何跨函式呼叫使用每一個暫存器：

|註冊|狀態|用途|
|-|-|-|
|RAX|動態|傳回值暫存器|
|RCX|動態|第一個整數引數|
|RDX|動態|第二個整數引數|
|R8|動態|第三個整數引數|
|R9|動態|第四個整數引數|
|R10:R11|動態|必須由呼叫者視需要保留；在 syscall/sysret 指令中使用|
|R12:R15|靜態|必須由被呼叫者保留|
|RDI|靜態|必須由被呼叫者保留|
|RSI|靜態|必須由被呼叫者保留|
|RBX|靜態|必須由被呼叫者保留|
|RBP|靜態|必須用作框架指標；必須由被呼叫者保留|
|RSP|靜態|堆疊指標|
|XMM0, YMM0|動態|第一個 FP 引數;使用時的第一個向量類型引數 **`__vectorcall`**|
|XMM1, YMM1|動態|第二個 FP 引數;使用時的第二個向量類型引數 **`__vectorcall`**|
|XMM2, YMM2|動態|第三個 FP 引數;使用時的第三個向量類型引數 **`__vectorcall`**|
|XMM3, YMM3|動態|第四個 FP 引數;使用時的第四個向量類型引數 **`__vectorcall`**|
|XMM4, YMM4|動態|必須由呼叫者視需要保留;使用時的第五個向量類型引數 **`__vectorcall`**|
|XMM5, YMM5|動態|必須由呼叫者視需要保留;使用時的第六個向量類型引數 **`__vectorcall`**|
|XMM6:XMM15, YMM6:YMM15|靜態 (XMM)、動態 (YMM 的上半部分)|必須由被呼叫者保留。 YMM 暫存器必須由被呼叫者視需要保留。|

在函式結束時，以及對 C 執行時間程式庫呼叫和 Windows 系統呼叫的函式輸入，應該清除 CPU 旗標登錄中的方向旗標。

## <a name="stack-usage"></a>堆疊使用方式

如需有關 x64 上堆疊配置、對齊方式、函式類型和堆疊框架的詳細資訊，請參閱 [x64 堆疊使用](stack-usage.md)方式。

## <a name="prolog-and-epilog"></a>初構和終解

配置堆疊空間、呼叫其他函式、儲存非靜態暫存器或使用例外狀況處理的每個函式，都必須具有在與個別函式資料表專案相關聯的回溯資料中描述其位址限制的初構，並在每次結束時 epilogs 至函式。 如需 x64 上所需的初構和終解程式碼的詳細資訊，請參閱 x64 初構 [和](prolog-and-epilog.md)終解。

## <a name="x64-exception-handling"></a>x64 例外狀況處理

如需有關用來在 x64 上執行結構化例外狀況處理和 c + + 例外狀況處理行為的慣例和資料結構的詳細資訊，請參閱 [x64 例外狀況處理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>內建和內嵌的元件

X64 編譯器的其中一個限制是沒有內嵌組合語言支援。 這表示無法以 C 或 c + + 撰寫的函式，將必須撰寫為副程式或編譯器支援的內建函式。 某些函式在效能上是敏感的，有些則否。 與效能相關的函式應該實作為內建函式。

編譯器所支援的內建函式會在 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)中描述。

## <a name="image-format"></a>影像格式

X64 可執行映射格式為 PE32 +。  (Dll 和 Exe) 的可執行映射會限制為 2 gb 的大小上限，因此可使用32位取代的相對定址來定址靜態影像資料。 此資料包括匯入位址資料表、字串常數、靜態全域資料等等。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
