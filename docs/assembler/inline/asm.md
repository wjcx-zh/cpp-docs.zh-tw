---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 14a40bef5b2edba76fc130604414c45eee589bcd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192999"
---
# `__asm`

**Microsoft 特定的**

關鍵字會叫 **`__asm`** 用內嵌組合語言，而且可以出現在 C 或 c + + 語句合法的任何位置。 它不可以單獨出現。 後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。 此處的「區塊」一詞 **`__asm`** 指的是任何指令或指示群組，不論是否以大括弧括住。

> [!NOTE]
> 標準 c + + 關鍵字的 Visual C++ 支援 **`asm`** 僅限於編譯器不會在關鍵字上產生錯誤的事實。 不過， **`asm`** 區塊不會產生任何有意義的程式碼。 使用， **`__asm`** 而不是 **`asm`** 。

## <a name="grammar"></a>文法

*asm-封鎖*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***assembly-指令* **`;`**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***元件-指令清單* **`}`****`;`** <sub>opt</sub>

*元件-指令清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **`;`**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **`;`***元件-指令清單* **`;`**<sub>opt</sub>

## <a name="remarks"></a>備註

如果使用時不含大括弧， **`__asm`** 關鍵字表示行的其餘部分是元件語言語句。 如果搭配大括號使用，表示在大括號之間的每一行都是組合語言的陳述式。 為了與舊版相容， **`_asm`** 是的同義字 **`__asm`** 。

因為 **`__asm`** 關鍵字是語句分隔符號，所以您可以將元件指令放在同一行上。

在 Visual Studio 2005 之前，指示

```cpp
__asm int 3
```

以 **/clr**編譯時，不會產生原生程式碼;編譯器會將指令轉譯為 CLR 中斷指令。

`__asm int 3` 現在會產生函式的機器碼。 如果您想要讓函式在您的程式碼中造成中斷點，而且如果您想要將該函式編譯成 MSIL，請使用[__debugbreak](../../intrinsics/debugbreak.md)。

為了與舊版相容， **`_asm`** **`__asm`** 除非指定了編譯器選項[/za \( 停用語言擴充](../../build/reference/za-ze-disable-language-extensions.md)功能，否則會是同義字。

## <a name="example"></a>範例

下列程式碼片段是 **`__asm`** 以大括弧括住的簡單區塊：

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

或者，您可以 **`__asm`** 在每個元件指令前面放入：

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

因為 **`__asm`** 關鍵字是語句分隔符號，所以您也可以將元件指令放在同一行：

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

這三個範例都會產生相同的程式碼，但第一個樣式（ **`__asm`** 以大括弧括住區塊）有一些優點。 大括弧會清楚地分隔 C 或 c + + 程式碼中的組解碼，並避免不必要的 **`__asm`** 關鍵字重複。 大括號也可避免語意模糊。 如果您想要將 C 或 c + + 語句放在與區塊相同的行上 **`__asm`** ，您必須以大括弧括住區塊。 沒有括號，編譯器就無法分辨組譯碼停止和 C 或 C++ 陳述式開始的位置。 最後，因為在括號中的文字與一般的 MASM 文字格式相同，您可以輕鬆地從現有的 MASM 原始程式檔剪貼文字。

不同于 C 和 c + + 中的大括弧，封閉區塊的大括弧 **`__asm`** 不會影響變數範圍。 您也可以嵌套 **`__asm`** 區塊; 嵌套不會影響變數範圍。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[關鍵字](../../cpp/keywords-cpp.md)<br/>
[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
