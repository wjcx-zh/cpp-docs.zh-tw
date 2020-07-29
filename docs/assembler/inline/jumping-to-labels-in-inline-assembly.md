---
title: 跳至內嵌組譯碼中的標籤
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 0c411289745466bd6478cc82ab30e6a05be9cc25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191998"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>跳至內嵌組譯碼中的標籤

**Microsoft 特定的**

就像一般 C 或 c + + 標籤一樣，區塊中的標籤在 **`__asm`** 其定義所在的整個函式中都有範圍（而不只是在區塊中）。 元件指示和 **`goto`** 語句都可以跳到區塊內部或外部的標籤 **`__asm`** 。

區塊中定義的標籤 **`__asm`** 不區分大小寫; **`goto`** 語句和元件指示都可以參考這些標籤，而不考慮大小寫。 C 和 c + + 標籤只有在語句使用時才區分大小寫 **`goto`** 。 組件指令可以跳至 C 或 C++ 標籤，而不需考慮大小寫。

下列程式碼將顯示所有排列：

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

請勿使用 C 程式庫函式名稱做為區塊中的標籤 **`__asm`** 。 例如，下列情況可能會讓您想要使用 `exit` 做為標籤：

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

由於**exit**是 C 程式庫函式的名稱，因此這個程式碼可能會導致跳至**exit**函式，而不是所需的位置。

如同在 MASM 程式中，貨幣符號 (`$`) 會做為目前位置計數器。 它是目前所組合之指示的標籤。 在 **`__asm`** 區塊中，其主要用途是進行長條件跳躍：

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
