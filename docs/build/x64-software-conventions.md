---
title: x64 軟體慣例
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417191"
---
# <a name="x64-software-conventions"></a>x64 軟體慣例

本節說明 x64 （64位延伸至 x86 架構）的 c + + 呼叫慣例方法。

## <a name="overview-of-x64-calling-conventions"></a>X64 呼叫慣例的總覽

X86 和 x64 之間的兩個重要差異是64位定址功能，以及一組一般使用的 16 64 位暫存器。 假設有擴充的暫存器集，x64 會使用[__fastcall](../cpp/fastcall.md)呼叫慣例和 RISC 型例外狀況處理模型。 `__fastcall`慣例會使用前四個引數的暫存器和堆疊框架來傳遞額外的引數。 如需 x64 呼叫慣例的詳細資訊，包括暫存器使用方式、堆疊參數、傳回值和堆疊回溯，請參閱[x64 呼叫慣例](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>啟用 x64 的優化

下列編譯器選項可協助您優化 x64 應用程式：

- [/favor (專為架構最佳化)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>類型和儲存體

本節描述 x64 架構之資料類型的列舉和儲存。

### <a name="scalar-types"></a>純量類型

雖然您可以使用任何對齊方式來存取資料，但建議您將資料對齊其自然界限或一些倍數，以避免效能降低。 列舉是常數整數，並會被視為32位整數。 下表描述資料的類型定義和建議的儲存體，因為它與對齊使用下列對齊值有關：

- 位元組-8 位

- Word-16 位

- 雙字-32 位

- 四字-64 位

- Octaword-128 位

|||||
|-|-|-|-|
|純量類型|C 資料類型|儲存體大小（以位元組為單位）|建議的對齊方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**unsigned short**|2|Word|
|**INT32**|**int**、 **long**|4|序位|
|**UINT32**|**不帶正負號的整數，不帶正負號的 long**|4|序位|
|**INT64**|**__int64**|8|序位|
|**UINT64**|**unsigned __int64**|8|序位|
|**FP32 （單精確度）**|**float**|4|序位|
|**FP64 （雙精確度）**|**double**|8|序位|
|**滑鼠**|__\*__|8|序位|
|**__m64**|**結構 __m64**|8|序位|
|**__m128**|**結構 __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>匯總和等位

其他類型（例如陣列、結構和等位）會有更嚴格的對齊需求，以確保一致的匯總和聯集儲存和資料抓取。 以下是陣列、結構和聯集的定義：

- Array

   包含相鄰資料物件的已排序群組。 每個物件都稱為*元素*。 陣列中的所有元素都具有相同的大小和資料類型。

- 結構

   包含資料物件的已排序群組。 不同于陣列的元素，結構中的資料物件可以有不同的資料類型和大小。 結構中的每個資料物件都稱為*成員*。

- Union

   物件，其中包含一組命名成員的任何一個。 命名集的成員可以是任何類型。 配置給聯集的儲存區等於該聯集最大成員所需的儲存空間，加上對齊所需的任何填補。

下表顯示等位和結構之純量成員的強烈建議對齊方式。

||||
|-|-|-|
|純量類型|C 資料類型|必要的對齊|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**unsigned short**|Word|
|**INT32**|**int**、 **long**|序位|
|**UINT32**|**不帶正負號的整數，不帶正負號的 long**|序位|
|**INT64**|**__int64**|序位|
|**UINT64**|**unsigned __int64**|序位|
|**FP32 （單精確度）**|**float**|序位|
|**FP64 （雙精確度）**|**double**|序位|
|**滑鼠**|<strong>\*</strong>|序位|
|**__m64**|**結構 __m64**|序位|
|**__m128**|**結構 __m128**|Octaword|

下列匯總對齊規則適用：

- 陣列的對齊方式與陣列其中一個元素的對齊方式相同。

- 結構或等位開頭的對齊是任何個別成員的最大對齊。 結構或等位中的每個成員都必須依照上表中的定義來放置適當的對齊，視前一個成員而定，這可能需要隱含的內部填補。

- 結構大小必須是其對齊的整數倍數，這可能需要在最後一個成員之後填補。 由於結構和等位可以在陣列中分組，因此結構或聯集的每個陣列元素都必須以先前判斷的適當對齊方式開始和結束。

- 只要保留先前的規則，就可以將資料對齊，使其大於對齊需求。

- 個別編譯器可能會因為大小的緣故而調整結構的封裝。 例如[/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)可讓您調整結構的封裝。

### <a name="examples-of-structure-alignment"></a>結構對齊範例

下列四個範例都會宣告對齊的結構或等位，而對應的圖表則說明該結構或 union 在記憶體中的配置。 圖中的每個資料行都代表記憶體的一個位元組，而資料行中的數位表示該位元組的位移。 每個圖表第二個數據列中的名稱會對應至宣告中的變數名稱。 陰影資料行表示達到指定對齊所需的填補。

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

結構位欄位的限制為64位，且可以屬於類型帶正負號的 int、不帶正負號的 int、int64 或不帶正負號的 int64。 跨類型界限的位欄位會略過 bits，將位字元對齊下一個類型對齊。 例如，整數位欄位可能不會跨越32位 boundry。

### <a name="conflicts-with-the-x86-compiler"></a>與 x86 編譯器衝突

當您使用 x86 編譯器來編譯應用程式時，大於4個位元組的資料類型不會在堆疊上自動對齊。 由於 x86 編譯器的架構是4位元組對齊堆疊，因此大於4個位元組的任何專案（例如，64位整數）無法自動對齊8個位元組的位址。

使用未對齊的資料有兩個含意。

- 存取對齊位置所需的未對齊位置可能需要較長的時間。

- 連鎖作業中無法使用未對齊的位置。

如果您需要更嚴格的對齊方式`__declspec(align(N))` ，請在您的變數宣告上使用。 這會導致編譯器以動態方式對齊堆疊，以符合您的規格。 不過，在執行時間動態調整堆疊可能會導致應用程式執行速度變慢。

## <a name="register-usage"></a>註冊使用方式

X64 架構提供16個一般用途的暫存器（這裡稱為整數暫存器），以及16個可供浮點使用的 XMM/YMM 暫存器。 動態暫存器是臨時暫存器，由呼叫者假設為跨呼叫終結。 需要靜態暫存器才能跨函式呼叫保留其值，且靜態暫存器必須由被呼叫者 (如果使用的話) 儲存。

### <a name="register-volatility-and-preservation"></a>註冊變動性和保留

下表描述如何跨函式呼叫使用每一個暫存器：

||||
|-|-|-|
|註冊|狀態|使用|
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

在函式 exit 上，以及在函式進入 C 執行時間程式庫呼叫和 Windows 系統呼叫的情況下，應清除 CPU 旗標暫存器中的方向旗標。

## <a name="stack-usage"></a>堆疊使用方式

如需堆疊配置、對齊、函式類型和 x64 上之堆疊框架的詳細資訊，請參閱[x64 堆疊使用](stack-usage.md)方式。

## <a name="prolog-and-epilog"></a>初構和終解

配置堆疊空間、呼叫其他函式、儲存非靜態暫存器或使用例外狀況處理的每個函式，都必須有一個初構，其位址限制會在與個別函式資料表專案相關聯的回溯資料中描述，並在每次結束時 epilogs 至函式。 如需 x64 上必要的初構和終解程式碼的詳細資訊，請參閱 x64 初構[和](prolog-and-epilog.md)終解。

## <a name="x64-exception-handling"></a>x64 例外狀況處理

如需在 x64 上用來執行結構化例外狀況處理和 c + + 例外狀況處理行為的慣例和資料結構的詳細資訊，請參閱[x64 例外狀況處理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>內建函式和內嵌組解碼

X64 編譯器的其中一個條件約束是沒有內嵌組合語言支援。 這表示無法以 C 或 c + + 撰寫的函式將必須撰寫為副程式或編譯器所支援的內建函式。 某些函式會區分效能，而其他函式則不會。 效能相關的函式應該實作為內建函式。

編譯器所支援的內建函式會在[編譯器內建函式](../intrinsics/compiler-intrinsics.md)中說明。

## <a name="image-format"></a>影像格式

X64 可執行檔影像格式為 PE32 +。 可執行映射（Dll 和 Exe）的大小上限為 2 gb，因此可使用32位置換的相對定址來處理靜態影像資料。 此資料包括匯入位址資料表、字串常數、靜態全域資料等等。

## <a name="see-also"></a>請參閱

[呼叫慣例](../cpp/calling-conventions.md)
