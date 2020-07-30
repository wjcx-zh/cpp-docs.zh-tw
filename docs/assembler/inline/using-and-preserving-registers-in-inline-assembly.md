---
title: 在內嵌組譯碼中使用和保留暫存器
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 99ca0093bb27e859854dfd1ca64addea923e5a5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191504"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>在內嵌組譯碼中使用和保留暫存器

**Microsoft 特定的**

一般來說，在區塊開始時，您不應該假設暫存器會有指定的值 **`__asm`** 。 暫存器值不保證會保留在不同的 **`__asm`** 區塊中。 如果您結束內嵌程式碼區塊並開始另一個區塊，您就不能依賴第二個區塊中的暫存器從第一個區塊保有其值。 **`__asm`** 區塊會繼承正常控制流程所產生的任何暫存器值。

如果您使用 **`__fastcall`** 呼叫慣例，編譯器會在暫存器中傳遞函數引數，而不是在堆疊上。 這可能會在具有區塊的函式中產生問題，因為函式 **`__asm`** 無法分辨哪個參數在哪個暫存器中。 如果函式剛好在 EAX 中接收參數並立即將其他參數儲存在 EAX 中，則會失去原始參數。 此外，您必須在使用宣告的任何函式中保留 ECX 暫存器 **`__fastcall`** 。

若要避免這類暫存器衝突，請勿針對包含區塊的函式使用 **`__fastcall`** 慣例 **`__asm`** 。 如果您 **`__fastcall`** 使用/Gr 編譯器選項來全域指定慣例，請使用或宣告包含區塊的每個函數 **`__asm`** **`__cdecl`** **`__stdcall`** 。 （ **`__cdecl`** 屬性會指示編譯器使用該函式的 C 呼叫慣例）。如果您不是使用/Gr 進行編譯，請避免使用屬性宣告函式 **`__fastcall`** 。

當 **`__asm`** 您使用在 c/c + + 函式中撰寫元件語言時，您不需要保留 EAX、EBX、ECX、EDX、ESI 或 EDI 暫存器。 例如，在 POWER2 中。C 範例：[使用內嵌](../../assembler/inline/writing-functions-with-inline-assembly.md)組解碼撰寫函式時，函式 `power2` 不會保留 EAX 暫存器中的值。 不過，使用這些暫存器會影響程式碼品質，因為註冊配置器無法使用它們來儲存 **`__asm`** 區塊之間的值。 此外，您可以在內嵌組譯碼中使用 EBX、ESI 或 EDI 來強制編譯器在函式序言和結尾中儲存及還原這些暫存器。

您應該保留用於區塊範圍的其他暫存器（例如 DS、SS、SP、BP 和 flags 暫存器） **`__asm`** 。 除非您有需要變更的理由 (例如切換堆疊)，否則您應該保留 ESP 和 EBP 暫存器。 另請參閱[優化內嵌](../../assembler/inline/optimizing-inline-assembly.md)組解碼。

部分 SSE 類型需要有八個位元組的堆疊對齊，強制編譯器發出動態堆疊對齊程式碼。 為了在對齊後能夠存取區域變數和函式參數二者，編譯器會保留兩個框架指標。  如果編譯器執行框架指標省略（FPO），則會使用 EBP 和 ESP。  如果編譯器未執行 FPO，則會使用 EBX 和 EBP。 為確保程式碼能夠正確執行，如果函式為了能夠修改框架指標而需要動態堆疊對齊，請勿修改 asm 程式碼中的 EBX。 您可以將八位元組的對齊類型移到函式以外，或者避免使用 EBX。

> [!NOTE]
> 如果內嵌組譯碼使用 STD 或 CLD 指令變更方向旗標，您必須將旗標還原為其原始值。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
