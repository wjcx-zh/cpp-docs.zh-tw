---
title: x64 軟體慣例
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313828"
---
# <a name="x64-software-conventions"></a>x64 軟體慣例

本章節描述C++呼叫慣例方法適用於 x64、 x86 64 位元延伸模組架構。

## <a name="overview-of-x64-calling-conventions"></a>X64 呼叫慣例的概觀

X86 和 x64 之間的兩個重要差異是 64 位元定址功能，以及一般的 16 個 64 位元暫存器設定一般用途。 提供擴充的暫存器組，使用 x64 [__fastcall](../cpp/fastcall.md)呼叫慣例和 risc 例外狀況處理模型。 `__fastcall`慣例會使用前四個引數的堆疊框架的暫存器傳遞其他引數。 針對 x64 呼叫慣例，包括暫存器使用量的詳細資訊堆疊參數，傳回值和堆疊回溯的情形，請參閱[x64 呼叫慣例](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>啟用適用於 x64 的最佳化

下列編譯器選項可協助您最佳化您的應用程式 （x64):

- [/favor (專為架構最佳化)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>型別和儲存體

本章節描述的列舉型別和儲存體的資料類型，適用於 x64 架構。

### <a name="scalar-types"></a>純量類型

雖然可以存取任何對齊的資料，但建議對齊自然界限或多個，以避免效能損失的資料。 列舉常數的整數，並會被視為 32 位元整數。 下表描述的型別定義和建議的儲存體的資料，因為它適用於使用下列的對齊值的對齊方式：

- 8 位元位元組

- Word-16 位元

- Doubleword-32 位元

- Quadword 為 64 位元

- Octaword-128 位元

|||||
|-|-|-|-|
|純量類型|C 資料類型|儲存體大小 （以位元組為單位）|建議的對齊方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|字組|
|**UINT16**|**unsigned short**|2|字組|
|**INT32**|**int**，**長**|4|Doubleword|
|**UINT32**|**不帶正負號的 int、 unsigned long**|4|Doubleword|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**unsigned __int64**|8|Quadword|
|**FP32 （單精確度）**|**float**|4|Doubleword|
|**FP64 （雙精確度）**|**double**|8|Quadword|
|**指標**|__\*__|8|Quadword|
|**__m64**|**結構 __m64**|8|Quadword|
|**__m128**|**結構 __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>彙總和等位

其他類型，例如陣列、 結構和等位，有更嚴格的對齊需求，以確保一致彙總和等位的儲存體和資料擷取。 以下是陣列、 結構和等位的定義：

- 陣列

   包含已排序的一整組相鄰的資料物件。 每個物件稱為*項目*。 在陣列中的所有元素都有相同的大小和資料類型。

- 結構

   包含已排序的一整組資料物件。 不同於陣列的元素，在結構中的資料物件可以有不同的資料類型和大小。 在結構中的每個資料物件稱為*成員*。

- 聯集

   物件，持有的一組具名成員的任何一個。 命名集的成員可以是任何類型。 配置給等位的儲存體等於所需的最大的成員，該聯集，再加上所需的對齊方式填補的儲存體。

下表顯示強烈建議純量的等位和結構成員對齊。

||||
|-|-|-|
|純量類型|C 資料類型|所需的對齊方式|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|字組|
|**UINT16**|**unsigned short**|字組|
|**INT32**|**int**，**長**|Doubleword|
|**UINT32**|**不帶正負號的 int、 unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 （單精確度）**|**float**|Doubleword|
|**FP64 （雙精確度）**|**double**|Quadword|
|**指標**|<strong>\*</strong>|Quadword|
|**__m64**|**結構 __m64**|Quadword|
|**__m128**|**結構 __m128**|Octaword|

適用下列的彙總的對齊方式規則：

- 陣列的對齊方式是其中一個陣列元素的對齊方式相同。

- 開頭的結構或等位的對齊方式會是任何個別成員的最大的對齊方式。 結構或等位中的每個成員必須放在正確的對齊方式，如同上表中，這可能需要隱含內部填補字元，根據先前的成員。

- 結構的大小必須是其對齊方式，可能需要在後的最後一個成員的填補整數倍數。 由於結構和等位可以歸類為陣列、 結構或等位的每個陣列元素必須在開始與結束先前決定正確的對齊方式。

- 可以對齊的方式，只要會保留上一個規則是大於對齊需求的資料。

- 個別的編譯器可能會調整大小基於結構的封裝。 比方說[/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)是用來調整結構的封裝。

### <a name="examples-of-structure-alignment"></a>結構對齊範例

下列四個範例每個宣告的對齊的結構或等位和對應的圖表說明該結構或等位在記憶體中的版面配置。 在圖中的每個資料行代表一個位元組的記憶體，以及資料行中的數字表示該位元組位移。 每一個圖形的第二個資料列中的名稱對應中宣告的變數的名稱。 網底的資料行表示填補，才能達到指定的對齊方式。

#### <a name="example-1"></a>範例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 轉換範例 1 結構配置](../build/media/vcamd_conv_ex_1_block.png "AMD 轉換範例 1 結構配置")

#### <a name="example-2"></a>範例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 轉換範例 2 結構配置](../build/media/vcamd_conv_ex_2_block.png "AMD 轉換範例 2 結構配置")

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

![AMD 轉換範例 2 結構配置](../build/media/vcamd_conv_ex_3_block.png "AMD 轉換範例 2 結構配置")

#### <a name="example-4"></a>範例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 轉換範例 4 的聯集 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 轉換範例 4 的聯集 layouit")

### <a name="bitfields"></a>位元欄位

結構的位元欄位限制為 64 位元，而且可以是類型的帶正負號 int、 不帶正負號的 int、 int64、 或不帶正負號的 int64。 跨越界限類型的位元欄位會略過對齊的下一步 類型的對齊方式的位元欄位的位元。 例如，整數的位元欄位可能不會跨 32 位元界限。

### <a name="conflicts-with-the-x86-compiler"></a>衝突與 x86 編譯器

資料類型都大於 4 個位元組會不會自動對齊堆疊上時使用 x86 編譯器來編譯應用程式。 因為 x86 編譯器是 4 位元組對齊的堆疊，任何大於 4 個位元組，比方說，64 位元整數，不會自動對齊 8 位元組位址的架構。

處理未對齊的資料有兩個含意。

- 可能需要較長的時間比所需存取對齊的位置存取未對齊的位置。

- 未對齊的位置不能在連鎖的作業。

如果您需要更多嚴格的對齊方式，使用`__declspec(align(N))`您變數宣告。 這可讓編譯器動態地對齊的堆疊，以符合您的規格。 不過，動態調整堆疊，在執行階段可能會導致您的應用程式的執行速度緩慢。

## <a name="register-usage"></a>暫存器使用方式

X64 架構提供 16 一般用途的暫存器 （以下稱為整數暫存器），以及 16 的 XMM/ymm 暫存註冊可供浮點數的使用。 動態暫存器是臨時暫存器，由呼叫者假設為跨呼叫終結。 需要靜態暫存器才能跨函式呼叫保留其值，且靜態暫存器必須由被呼叫者 (如果使用的話) 儲存。

### <a name="register-volatility-and-preservation"></a>變動性和保留暫存器

下表描述如何跨函式呼叫使用每一個暫存器：

||||
|-|-|-|
|登錄|狀態|使用|
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
|XMM0, YMM0|動態|第一個 FP 引數；使用 `__vectorcall` 時的第一個向量型別引數|
|XMM1, YMM1|動態|第二個 FP 引數；使用 `__vectorcall` 時的第二個向量類型引數|
|XMM2, YMM2|動態|第三個 FP 引數；使用 `__vectorcall` 時的第三個向量類型引數|
|XMM3, YMM3|動態|第四個 FP 引數；使用 `__vectorcall` 時的第四個向量類型引數|
|XMM4, YMM4|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第五個向量型別引數|
|XMM5, YMM5|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第六個向量型別引數|
|XMM6:XMM15, YMM6:YMM15|靜態 (XMM)、動態 (YMM 的上半部分)|必須由被呼叫端保留。 YMM 暫存器必須由被呼叫者視需要保留。|

函式結束和 C 執行階段程式庫呼叫和 Windows 系統呼叫的函式項目，方向旗標在 CPU 上旗標暫存器必須清除。

## <a name="stack-usage"></a>堆疊使用方式

如需堆疊配置、 對齊、 函式型別和 x64 上的堆疊框架的詳細資訊，請參閱[x64 堆疊使用方式](stack-usage.md)。

## <a name="prolog-and-epilog"></a>初構和終解

配置堆疊空間、 呼叫其他函式，將儲存靜態暫存器，或使用例外狀況處理每個函式必須有其位址的限制詳述於個別的函式表項目，並在終相關聯的回溯資料初構每個函式的結束。 有關所需的初構和終解程式碼，在 x64 上的，請參閱[x64 初構和終解](prolog-and-epilog.md)。

## <a name="x64-exception-handling"></a>x64 例外狀況處理

如需用來實作結構化例外狀況處理的慣例及資料結構和C++例外狀況處理行為，在 x64 上，請參閱[x64 例外狀況處理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>內建函式和內嵌組件

其中一個條件約束，適用於 x64 編譯器會為沒有內嵌組譯工具支援。 函式，這表示不能以 C 撰寫或C++將必須寫入為副程式或編譯器所支援的內建函式。 某些函式是效能敏感，而有些則不。 重視效能的函式應該實作為內建函式。

編譯器所支援的內建函式中所述[編譯器內建](../intrinsics/compiler-intrinsics.md)。

## <a name="image-format"></a>影像格式

X64 可執行映像格式為 PE32 +。 可執行映像 （Dll 和 Exe） 限於大小上限為 2 gb，因此可以用來解決靜態影像資料的 32 位元加上位移的相對位址。 此資料包含匯入位址表格，字串常數、 靜態的全域資料，以及等等。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
