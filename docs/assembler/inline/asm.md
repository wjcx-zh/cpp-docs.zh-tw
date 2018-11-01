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
ms.openlocfilehash: 6b94bf73e66550d0245ef1f55c17d6676e3b4356
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591278"
---
# <a name="asm"></a>__asm

**Microsoft 專屬**

`__asm` 關鍵字會叫用內嵌組合語言，而且可以出現在 C 或 C++ 陳述式有效的任何地方。 它不可以單獨出現。 後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。 這裡的「`__asm` 區塊」一詞是指任何指令或指令群組，不論是否放在大括號中。

> [!NOTE]
> Visual C++ 對 Standard C++ `asm` 關鍵字的支援受到「編譯器不會發生關鍵字的錯誤」的這個事實所限制。 不過，`asm` 區塊不會產生任何有意義的程式碼。 使用 `__asm` 取代 `asm`。

## <a name="grammar"></a>文法

*asm 區塊*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *組譯碼指令* **;**<sub>選擇</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *組件指示清單* **}** **;**<sub>選擇</sub>

*組件指示清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*組譯碼指令* **;**<sub>選擇</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*組譯碼指令* **;***組件指示清單* **;**<sub>選擇</sub>

## <a name="remarks"></a>備註

如果不含大括號使用，`__asm` 關鍵字表示該行的其餘部分是組合語言的陳述式。 如果搭配大括號使用，表示在大括號之間的每一行都是組合語言的陳述式。 為了與舊版相容，`_asm` 是 `__asm` 的同義字。

由於 `__asm` 關鍵字是陳述式分隔符號，您可以在同一行上放置組譯碼指令。

在 Visual C++ 2005 之前，指令

```cpp
__asm int 3
```

不會造成編譯時產生的原生程式碼 **/clr**; 編譯器會轉譯為 CLR 中斷指令的指示。

`__asm int 3` 現在會產生函式的機器碼。 如果您想要產生程式碼中的中斷點，如果您想要編譯為 MSIL，該函數使用的函式[__debugbreak](../../intrinsics/debugbreak.md)。

為了與舊版中，相容性 **_asm**同義 **__asm**除非編譯器選項[/Za\(停用語言擴充功能)](../../build/reference/za-ze-disable-language-extensions.md)指定。

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[關鍵字](../../cpp/keywords-cpp.md)<br/>
[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>