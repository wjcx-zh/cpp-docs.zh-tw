---
title: 結構和 UNWIND_CODE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1da6f078741c598099e71da9164f54b56da3f355
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726644"
---
# <a name="struct-unwindcode"></a>struct UNWIND_CODE

回溯程式碼陣列用來記錄會影響到 RSP 與靜態暫存器的初構中的一系列的作業。 每個程式碼項目具有下列格式：

|||
|-|-|
|UBYTE|初構中的位移|
|UBYTE: 4|回溯作業程式碼|
|UBYTE: 4|作業資訊|

陣列是由初構中的位移的遞減順序排序。

## <a name="offset-in-prolog"></a>初構中的位移

從執行這項作業，再加上 1 （也就是下一個指令開始的位移） 的指示結尾的初構開頭的位移。

## <a name="unwind-operation-code"></a>回溯作業程式碼

注意： 某些作業程式碼需要的不帶正負號的位移，在本機的堆疊框架中的值。 這個位移會是固定的堆疊配置開始 （最低位址）。 如果框架註冊中的欄位 UNWIND_INFO 為零，此位移為 from RSP。 如果框架註冊 欄位為非零值，這會是從 RSP 所在 fp 建立時的位移。 此值等於 fp 減 FP reg 位移值 (16\*縮放的框架註冊 UNWIND_INFO 中的位移)。 如果使用 fp，然後採用位移任何回溯程式碼只能用於 fp 建立初構中之後。

針對以外的所有作業碼`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`的位移一律是 8 的倍數，因為所有堆疊 （堆疊本身是一律對齊 16 位元組） 的 8 位元組界限上儲存感興趣的值。 如需簡短的位移 (不超過 512 K) 的作業碼，最終的 USHORT 的節點，此程式碼中會保留除以 8 的位移。 針對需要較長的位移的作業程式碼 (512 K < = 位移 < 4 GB)，最後兩個 USHORT 節點，此程式碼會容納位移 （以位元組由小到大格式）。

針對 opcode`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`，位移會一律是 16 的倍數，因為所有的 128 位元 XMM 作業必須發生在 16 位元組對齊的記憶體上。 因此，16 縮放比例就會用於`UWOP_SAVE_XMM128`，允許小於 1 百萬個的位移。

回溯作業程式碼是下列其中一項：

`UWOP_PUSH_NONVOL` (0) 1 個節點

推送靜態整數暫存器，遞減 RSP 8。 作業資訊是暫存器的數目。 請注意，由於上終，限制`UWOP_PUSH_NONVOL`回溯程式碼必須出現在初構中的第一次，而同樣地，最後一個回溯程式碼陣列中。 此相對順序適用於所有其他回溯程式碼，除了`UWOP_PUSH_MACHFRAME`。

`UWOP_ALLOC_LARGE` （1) 2 或 3 個節點

配置堆疊上的大型區域。 有兩種形式。 如果作業資訊會等於 0，則除以配置的大小 8 會記錄到下一個位置，讓配置的上限為 512 K-8。 如果作業資訊會等於 1，則允許配置的位元組由小到大格式的下面兩個插槽中記錄的配置未縮放的大小達 4 GB-8。

`UWOP_ALLOC_SMALL` (2) 1 個節點

配置堆疊上的小型區域。 配置的大小是作業的 [資訊] 欄位\*8 + 8，允許從 8 到 128 個位元組的配置。

堆疊配置的回溯程式碼應該一律使用最短的可能編碼方式：

|**配置大小**|**回溯程式碼**|
|-|-|
|8 到 128 個位元組|`UWOP_ALLOC_SMALL`|
|第 136 到 512-8 個位元組|`UWOP_ALLOC_LARGE`作業資訊 = 0|
|512 K 到 4 G-8 個位元組|`UWOP_ALLOC_LARGE`作業資訊 = 1|

`UWOP_SET_FPREG` （3) 1 個節點

建立框架指標暫存器的目前 RSP 一些位移，以設定暫存器。 位移等於框架註冊位移 （縮放） 欄位中 UNWIND_INFO \* 16，允許從 0 到 240 的位移。 使用位移允許建立框架指標，指向 固定的堆疊配置，有助於藉由使用更多的存取，使用簡短的指令形式的程式碼的密度的中間。 請注意 [作業資訊] 欄位已保留，而且不應該使用。

`UWOP_SAVE_NONVOL` （4） 2 個節點

將靜態整數暫存器儲存使用 MOV，而不推入堆疊上。 這主要用於包裝，靜態暫存器儲存到先前配置的位置中的堆疊的位置。 作業資訊是暫存器的數目。 調整由-8 堆疊位移會記錄在下一個回溯作業程式碼位置，如以上所述。

`UWOP_SAVE_NONVOL_FAR` （5） 3 個節點

將靜態整數暫存器儲存長時間的位移，而不推播使用 MOV 與在堆疊上。 這主要用於包裝，靜態暫存器儲存到先前配置的位置中的堆疊的位置。 作業資訊是暫存器的數目。 無縮放的堆疊會記錄在接下來兩個回溯作業程式碼位置，如以上所述。

`UWOP_SAVE_XMM128` （8） 2 個節點

將所有的 128 位元靜態 xmm 暫存器儲存在堆疊上。 作業資訊是暫存器的數目。 縮放 x 16 堆疊位移會記錄在下一個位置。

`UWOP_SAVE_XMM128_FAR` （9） 3 個節點

將所有的 128 位元靜態 xmm 暫存器儲存以長位移堆疊上。 作業資訊是暫存器的數目。 未縮放的堆疊會記錄在下面兩個位置。

`UWOP_PUSH_MACHFRAME` （10) 1 個節點

推播機器框架。  這用來記錄硬體插斷或例外狀況的影響。 有兩種形式。 如果作業資訊會等於 0，下列項目已推入堆疊：

|||
|-|-|
|RSP + 32|SS|
|RSP + 24|舊 RSP|
|RSP + 16|EFLAGS|
|RSP + 8|CS|
|RSP|擷取|

如果作業資訊會等於 1，則改為已推送下列：

|||
|-|-|
|RSP + 40|SS|
|RSP + 32|舊 RSP|
|RSP + 24|EFLAGS|
|RSP + 16|CS|
|RSP + 8|擷取|
|RSP|錯誤碼|

此回溯程式碼一律會出現在空的初構，永遠不會實際執行，但改為出現之前的插斷常式，實際的進入點和存在只是為了提供一個位置來模擬電腦畫面格的推播。 `UWOP_PUSH_MACHFRAME` 會記錄該模擬，表示電腦已在概念上完成下列內容：

1. 快顯至堆疊的頂端 RIP 傳回位址*Temp*

2. 推播 SS

3. 推入舊 RSP

4. 推播 EFLAGS

5. 推播 CS

6. 推播*Temp*

7. 推入錯誤碼 （如果 op 資訊等於 1）

模擬`UWOP_PUSH_MACHFRAME`40 的作業遞減 RSP （作業資訊會等於 0） 或 48 （作業資訊會等於 1）。

## <a name="operation-info"></a>作業資訊

這 4 個位元的意義取決於作業程式碼。 若要編碼的一般用途 (integer) 暫存器，請使用下列的對應：

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 到 15|R15 的 R8|

## <a name="see-also"></a>另請參閱

[回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)