---
title: 撰寫初構-終解程式碼的考慮
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: a598ddbdd1b5f91c97e32905202e264b444c05d0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988697"
---
# <a name="considerations-for-writing-prologepilog-code"></a>撰寫初構/終解程式碼的考量

**Microsoft 專屬**

在撰寫您自己的初構和終解程式碼序列之前，請務必瞭解堆疊框架的配置方式。瞭解如何使用 `__LOCAL_SIZE` 符號也很有用。

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a>堆疊框架版面配置

這個範例將示範可能出現在 32 位元函式中的標準初構程式碼：

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

`localbytes` 變數代表區域變數堆疊上所需的位元組數目，而 `<registers>` 變數是預留位置，代表要儲存在堆疊上的暫存器清單。 推入暫存器之後，您就可以在堆疊上放置任何適當的資料。 以下是對應的終解程式碼：

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

堆疊一律從高到低排列 (從高到低記憶體位址)。 基底指標 (`ebp`) 會指向 `ebp` 的推送值。 區域是從 `ebp-4` 開始。 若要存取區域變數，請從 `ebp` 減去適當的值計算 `ebp` 的位移。

##  <a name="_pluslang___local_size"></a>__LOCAL_SIZE

編譯器會提供符號 `__LOCAL_SIZE`，以便在函式初構程式碼的內嵌組合語言區塊中使用。 這個符號是用來在自訂初構程式碼中堆疊框架上為區域變數配置空間。

編譯器會判斷 `__LOCAL_SIZE`的值。 其值是所有使用者定義之區域變數和編譯器所產生之暫存變數的位元組總數。 `__LOCAL_SIZE` 只能用來做為立即運算元;它不能用在運算式中。 您不得變更或重新定義這個符號的值。 例如：

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

下列包含自訂初構和終解序列之 naked 函式的範例會使用初構序列中的 `__LOCAL_SIZE` 符號：

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[Naked 函式呼叫](../cpp/naked-function-calls.md)
