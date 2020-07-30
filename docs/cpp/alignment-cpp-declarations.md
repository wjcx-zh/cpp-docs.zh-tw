---
title: 對齊
description: 現代化 c + + 中指定資料對齊的方式。
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 7f6bef061fee41389bad644d9ac5244f5644da76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227643"
---
# <a name="alignment"></a>對齊

C++ 的其中一項低階功能可指定記憶體中物件的精確對齊方式，以充份利用特定的硬體架構。 根據預設，編譯器會將類別和結構成員對齊其大小值： **`bool`** 在 **`char`** 1 個位元組的界限上、在2個位元組的界限上、、、和4個位元組的界限上，以及 **`short`** **`int`** **`long`** **`float`** **`long long`** 、 **`double`** 、和 **`long double`** 8 位元組界限。

在大部分的情況下，您永遠不需要擔心對齊，因為預設的對齊方式已經是最佳的。 不過，在某些情況下，您可以藉由指定資料結構的自訂對齊，來達到顯著的效能改進或節省記憶體。 在 Visual Studio 2015 之前，您可以使用 Microsoft 特有的關鍵字 **`__alignof`** ，並 **`__declspec(align)`** 指定大於預設值的對齊方式。 從 Visual Studio 2015 開始，您應該使用 c + + 11 標準關鍵字 **`alignof`** ，以及 **`alignas`** 最大的程式碼可攜性。 新關鍵字的行為與 Microsoft 專屬的擴充功能相同。 這些延伸模組的檔也適用于新的關鍵字。 如需詳細資訊，請參閱[ `alignof` 運算子](../cpp/alignof-operator.md)和[align](../cpp/align-cpp.md)。 C + + 標準不會指定在界限小於目標平臺的編譯器預設值時，進行對齊的封裝行為，因此您仍然需要 [`#pragma pack`](../preprocessor/pack.md) 在該情況下使用 Microsoft。

針對具有自訂對齊的資料結構，使用[aligned_storage 類別](../standard-library/aligned-storage-class.md)來進行記憶體配置。 [Aligned_union 類別](../standard-library/aligned-union-class.md)是用來指定具有非一般程式或析構函式之等位的對齊方式。

## <a name="alignment-and-memory-addresses"></a>對齊和記憶體位址

對齊是記憶體位址的屬性，以數字位址取 2 乘冪的模數來表示。 例如，位址0x0001103F 模數4是3。 該位址會被視為對齊 4n + 3，其中4表示所選的2乘冪。 位址的對齊方式取決於所選的2乘冪。 相同位址取 8 的模數為 7。 如果位址的對齊方式為 Xn+0，則稱為對齊 X。

Cpu 會執行指示，以處理儲存在記憶體中的資料。 資料會以其在記憶體中的位址來識別。 單一 datum 也有大小。 如果它的位址對齊其大小，我們就會呼叫以*自然對齊*的基準。 否則會將其稱為未*對齊*。 例如，如果用來識別它的位址具有8位元組對齊，則會自然對齊8位元組的浮點基準。

## <a name="compiler-handling-of-data-alignment"></a>資料對齊的編譯器處理

編譯器嘗試以防止資料對齊的方式進行資料分配。

針對簡單的資料類型，編譯器指派的位址會是以位元組為單位之資料類型大小的倍數。 例如，編譯器會將位址指派給類型的變數 **`long`** ，這是4的倍數，將位址的底部2位設定為零。

編譯器也會以自然對齊結構的每個元素的方式來填補結構。 請考慮 `struct x_` 下列程式碼範例中的結構：

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

編譯器會填補這個結構，以便強制執行自然對齊。

下列程式碼範例顯示編譯器如何將填補的結構放在記憶體中：

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

這兩個宣告都會傳回 `sizeof(struct x_)` 12 個位元組。

第二個宣告包含兩個填補項目：

1. `char _pad0[3]`將成員對齊 `int b` 4 位元組界限。

1. `char _pad1[1]`將結構的陣列元素對齊 `struct _x bar[3];` 四個位元組的界限。

填補 `bar[3]` 會以允許自然存取的方式來對齊的元素。

下列程式碼範例顯示 `bar[3]` 陣列版面配置：

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>`alignof` 和 `alignas`

**`alignas`** 類型規範是可移植的 c + + 標準方法，可指定自訂變數和使用者定義類型的對齊方式。 **`alignof`** 運算子同樣是可移植的標準方式，以取得指定類型或變數的對齊方式。

## <a name="example"></a>範例

您可以 **`alignas`** 在類別、結構或等位上，或個別成員上使用。 當遇到多個指定名稱時 **`alignas`** ，編譯器會選擇最嚴格的一個（具有最大值的規範）。

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>另請參閱

[資料結構對齊](https://en.wikipedia.org/wiki/Data_structure_alignment)
