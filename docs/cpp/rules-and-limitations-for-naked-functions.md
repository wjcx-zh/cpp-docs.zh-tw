---
title: Naked 函式的規則和限制
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: 3dd089e13323e1811cf9d7c7717612313f2cef7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225848"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Naked 函式的規則和限制

**Microsoft 特定的**

下列規則和限制適用於 naked 函式：

- **`return`** 不允許使用語句。

- 不允許結構化例外狀況處理和 C++ 例外狀況處理建構，因為它們必須跨堆疊框架回溯。

- 基於相同理由，亦不得使用任何形式的 `setjmp`。

- 禁止使用 `_alloca` 函式。

- 為確保初構序列之前不會出現區域變數的初始化程式碼，函式範圍不可使用初始化的區域變數。 尤其不允許在函式範圍宣告 C++ 物件。 不過，巢狀範圍中可以有初始化資料。

- 不建議使用框架指標最佳化 (/Oy 編譯器選項)，但 naked 函式會自動隱藏此最佳化。

- 您不能在函式語彙範圍宣告 C++ 類別物件。 不過，您可以在巢狀區塊中宣告物件。

- **`naked`** 使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)進行編譯時，會忽略關鍵字。

- 針對[__fastcall](../cpp/fastcall.md) naked 函式，只要 C/c + + 程式碼中的其中一個暫存器引數有參考，初構程式碼就應該將該暫存器的值儲存在該變數的堆疊位置中。 例如：

```cpp
// nkdfastcl.cpp
// compile with: /c
// processor: x86
__declspec(naked) int __fastcall  power(int i, int j) {
   // calculates i^j, assumes that j >= 0

   // prolog
   __asm {
      push ebp
      mov ebp, esp
      sub esp, __LOCAL_SIZE
     // store ECX and EDX into stack locations allocated for i and j
     mov i, ecx
     mov j, edx
   }

   {
      int k = 1;   // return value
      while (j-- > 0)
         k *= i;
      __asm {
         mov eax, k
      };
   }

   // epilog
   __asm {
      mov esp, ebp
      pop ebp
      ret
   }
}
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[Naked 函式呼叫](../cpp/naked-function-calls.md)
