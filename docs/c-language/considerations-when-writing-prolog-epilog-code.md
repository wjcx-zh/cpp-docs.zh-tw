---
title: 撰寫初構-終解程式碼時的考量
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e7bfeccf41b9e4dace49e9ab209a94598c492b41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515527"
---
# <a name="considerations-when-writing-prologepilog-code"></a>撰寫初構/終解程式碼時的考量

**Microsoft 專屬**

在您撰寫自己的初構和終解程式碼序列之前，務必先了解堆疊框架的配置方式。另外，了解如何使用 **__LOCAL_SIZE** 預先定義常數也會很實用。

##  <a name="_clang_c_stack_frame_layout"></a> C 堆疊框架配置

這個範例將示範可能出現在 32 位元函式中的標準初構程式碼：

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

`localbytes` 變數代表區域變數堆疊上所需的位元組數目，而 `registers` 變數是預留位置，代表要儲存在堆疊上的暫存器清單。 推入暫存器之後，您就可以在堆疊上放置任何適當的資料。 以下是對應的終解程式碼：

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

堆疊一律從高到低排列 (從高到低記憶體位址)。 基底指標 (`ebp`) 會指向 `ebp` 的推送值。 區域變數區域是從 `ebp-2` 開始。 若要存取區域變數，請從 `ebp` 減去適當的值計算 `ebp` 的位移。

##  <a name="_clang_the___local_size_constant"></a> __LOCAL_SIZE 常數

編譯器會提供常數 **__LOCAL_SIZE**，用於函式初構程式碼的內嵌組合語言區塊中。 這個常數是用來配置區域變數在自訂初構程式碼中堆疊框架上的空間。

編譯器會判斷 **__LOCAL_SIZE** 的值。 這個值是所有使用者定義區域變數和編譯器所產生暫存變數的位元組總數。 **__LOCAL_SIZE** 只能作為即時運算元，不能在運算式中使用。 您不可變更或重新定義這個常數的值。 例如: 

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

下列 naked 函式範例包含自訂初構和終解序列，會在初構序列中使用 **__LOCAL_SIZE**：

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[Naked 函式](../c-language/naked-functions.md)