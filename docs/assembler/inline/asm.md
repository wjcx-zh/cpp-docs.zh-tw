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
ms.openlocfilehash: de28e4c0fad6b89a62b4479c5c32f0b8606cf3af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169627"
---
# <a name="__asm"></a>__asm

**Microsoft 專屬**

`__asm` 關鍵字會叫用內嵌組合語言，而且可以出現在 C 或 C++ 陳述式有效的任何地方。 它不可以單獨出現。 後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。 這裡的「`__asm` 區塊」一詞是指任何指令或指令群組，不論是否放在大括號中。

> [!NOTE]
> Visual C++ 對 Standard C++ `asm` 關鍵字的支援受到「編譯器不會發生關鍵字的錯誤」的這個事實所限制。 不過，`asm` 區塊不會產生任何有意義的程式碼。 使用 `__asm` 取代 `asm`。

## <a name="grammar"></a>文法

*asm-封鎖*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm** *assembly-指示* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *assembly-指令清單* **}** **;** <sub>opt</sub>

*元件-指令清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指示* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **;** *元件指令清單* **;** <sub>opt</sub>

## <a name="remarks"></a>備註

如果不含大括號使用，`__asm` 關鍵字表示該行的其餘部分是組合語言的陳述式。 如果搭配大括號使用，表示在大括號之間的每一行都是組合語言的陳述式。 為了與舊版相容，`_asm` 是 `__asm` 的同義字。

由於 `__asm` 關鍵字是陳述式分隔符號，您可以在同一行上放置組譯碼指令。

在 Visual Studio 2005 之前，指示

```cpp
__asm int 3
```

以 **/clr**編譯時，不會產生原生程式碼;編譯器會將指令轉譯為 CLR 中斷指令。

`__asm int 3` 現在會產生函式的機器碼。 如果您想要讓函式在您的程式碼中造成中斷點，而且如果您想要將該函式編譯成 MSIL，請使用[__debugbreak](../../intrinsics/debugbreak.md)。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../../build/reference/za-ze-disable-language-extensions.md) ，否則 **_asm**是 **__asm**的同義字。

## <a name="example"></a>範例

下列程式碼片段是放在大括號中的簡單 `__asm` 區塊：

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

或者，您可以將 `__asm` 放在每個組譯碼指令前面：

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

由於 `__asm` 關鍵字是陳述式分隔符號，您也可以將組件指令放在同一行：

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

這三個範例會產生相同的程式碼，不過，第一個樣式 (將 `__asm` 區塊放在括號中) 會比較具有優勢。 大括號會明顯分隔組合語言程式碼與 C 或 C++ 程式碼，並避免 `__asm` 關鍵字不必要的重複。 大括號也可避免語意模糊。 如果您想要在 `__asm` 區塊的同一行放置 C 或 C++ 陳述式，則必須以大括號括住區塊。 沒有括號，編譯器就無法分辨組譯碼停止和 C 或 C++ 陳述式開始的位置。 最後，因為在括號中的文字與一般的 MASM 文字格式相同，您可以輕鬆地從現有的 MASM 原始程式檔剪貼文字。

與 C 和 C++ 中的大括號不同，將 `__asm` 區塊括住的大括號不會影響變數範圍。 您也可以使用巢狀 `__asm` 區塊；巢狀並不會影響變數範圍。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[關鍵字](../../cpp/keywords-cpp.md)<br/>
[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>
