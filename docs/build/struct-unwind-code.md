---
title: 結構和 UNWIND_CODE |Microsoft 文件
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
ms.openlocfilehash: 068acacf88e9ac968b34c26bf76657fd33adf4f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="struct-unwindcode"></a>struct UNWIND_CODE
回溯程式碼陣列用來記錄會影響靜態暫存器和 RSP 初構中的一系列的作業。 每個程式碼項目具有下列格式：  
  
|||  
|-|-|  
|UBYTE|初構中的位移|  
|UBYTE: 4|回溯作業程式碼|  
|UBYTE: 4|作業資訊|  
  
 陣列的初構中的位移遞減順序來排序。  
  
 **初構中的位移**  
 從執行這項作業，加上 1 （亦即，位移的下一個指令開始） 的指示結尾的初構開頭的位移。  
  
 **回溯作業程式碼**  
 注意： 特定作業的程式碼需要本機堆疊框架中的值不帶正負號的位移。 此位移為 from 固定的堆疊配置的開頭 （最低位址）。 如果框架暫存器中的欄位 UNWIND_INFO 為零，此位移為 from RSP。 如果框架暫存器的欄位不是零，這是從 RSP 所在 fp 建立時的位移。 此值等於 fp 減 FP reg 位移 (16 * 縮放的框架 UNWIND_INFO 中註冊位移)。 如果使用 fp，然後採用位移任何回溯程式碼只能用於初構中建立的 fp 之後。  
  
 如 UWOP_SAVE_XMM128 和 UWOP_SAVE_XMM128_FAR 以外的所有 opcode，位移一定會 8 的倍數，因為感興趣的所有堆疊的值會都儲存在 8 位元組界限 （堆疊本身為 alwayson 對齊 16 位元組）。 如需簡短的位移 (不超過 512 K) 的作業碼，最終的 USHORT 節點，此程式碼中保存的位移除以 8。 針對長時間的位移的作業程式碼 (512 K < = 位移 < 4 GB)，這段程式碼的最後兩個 USHORT 節點保留位移 （以位元組由小到大格式）。  
  
 作業碼 UWOP_SAVE_XMM128 和 UWOP_SAVE_XMM128_FAR 位移因為一律為 16 的倍數 128 位元 XMM 的所有作業必須都發生在 16 個位元組對齊的記憶體上。 因此，16 縮放比例就會用於 UWOP_SAVE_XMM128，允許的小於 1 M 位移。  
  
 回溯作業程式碼是下列其中一項：  
  
 UWOP_PUSH_NONVOL (0) 1 節點  
  
 推送靜態整數暫存器，遞減 RSP 8。 作業資訊是暫存器的數目。 請注意，終上的條件約束，因為 UWOP_PUSH_NONVOL 回溯程式碼必須先出現在初構中相對的最後一個回溯程式碼陣列中。 此相對順序套用至 UWOP_PUSH_MACHFRAME 以外的所有其他回溯程式碼。  
  
 UWOP_ALLOC_LARGE (1) 2 或 3 的節點  
  
 配置在堆疊上的大型區域。 有兩種形式。 如果作業資訊等於 0，則除以配置的大小 8 會記錄到下一個位置，允許最多 512 K-8 配置。 如果作業資訊等於 1，則允許配置的位元組由小到大格式的下面兩個插槽中記錄的配置未縮放的大小上限為 4 GB-8。  
  
 UWOP_ALLOC_SMALL (2) 1 節點  
  
 配置在堆疊上的小型區域。 配置的大小是作業資訊欄位 * 8 + 8，允許 8 到 128 個位元組的配置。  
  
 堆疊配置的回溯程式碼應該一律使用最短的可能編碼方式：  
  
|||  
|-|-|  
|**配置大小**|**回溯程式碼**|  
|8 到 128 個位元組|UWOP_ALLOC_SMALL|  
|136 到 512-8 個位元組|UWOP_ALLOC_LARGE，作業資訊 = 0|  
|512 K 到 4 G-8 個位元組|UWOP_ALLOC_LARGE，作業資訊 = 1|  
  
 UWOP_SET_FPREG (3) 1 節點  
  
 建立的暫存器設為目前 RSP 某些位移的框架指標暫存器。 位移是等於 UNWIND_INFO 註冊框架位移 （已縮放） 欄位 * 16，允許從 0 到 240 的位移。 使用位移允許建立框架指標，指向中間的固定的堆疊配置，藉由使用更多使用簡短的指示表單的存取協助程式碼的密度。 請注意作業資訊欄位已保留，而且不應使用。  
  
 UWOP_SAVE_NONVOL (4) 的 2 個節點  
  
 將靜態整數暫存器儲存使用 MOV 而不推入堆疊上。 這主要用於此處，靜態暫存器儲存在先前配置的位置堆疊的位置。 作業資訊是暫存器的數目。 調整所-8 堆疊位移會記錄在下一個回溯作業程式碼位置，如上述注意事項中所述。  
  
 UWOP_SAVE_NONVOL_FAR (5) 3 個節點  
  
 將靜態整數暫存器儲存以長位移，而不發送使用 MOV 堆疊上。 這主要用於此處，靜態暫存器儲存在先前配置的位置堆疊的位置。 作業資訊是暫存器的數目。 無縮放的堆疊會記錄在接下來兩個回溯作業程式碼位置，如上述注意事項中所述。  
  
 UWOP_SAVE_XMM128 (8) 的 2 個節點  
  
 將所有的 128 位元的靜態 xmm 暫存器儲存在堆疊上。 作業資訊是暫存器的數目。 調整 x 16 堆疊位移會記錄在下一個位置。  
  
 UWOP_SAVE_XMM128_FAR (9) 3 個節點  
  
 將所有的 128 位元的靜態 xmm 暫存器儲存以長位移堆疊上。 作業資訊是暫存器的數目。 無縮放的堆疊位移會記錄在下面兩個位置。  
  
 UWOP_PUSH_MACHFRAME (10) 1 節點  
  
 推送機器框架。  這用來記錄硬體插斷或例外狀況的影響。 有兩種形式。 如果作業資訊會等於 0，下列項目已推入堆疊：  
  
|||  
|-|-|  
|RSP + 32|SS|  
|RSP + 24|舊 RSP|  
|RSP + 16|EFLAGS|  
|RSP + 8|CS|  
|RSP|擷取|  
  
 如果作業資訊等於 1，表示改為推入下列項目：  
  
|||  
|-|-|  
|RSP + 40|SS|  
|RSP + 32|舊 RSP|  
|RSP + 24|EFLAGS|  
|RSP + 16|CS|  
|RSP + 8|擷取|  
|RSP|錯誤碼|  
  
 這個回溯程式碼一律會出現在空的初構，永遠不會實際執行，但改為顯示之前的插斷常式，實際的進入點和只用來提供一個位置以模擬推入機器框架存在。 UWOP_PUSH_MACHFRAME 會記錄該模擬，這表示電腦已經在概念上完成下列：  
  
 RIP 傳回位址從頂端到堆疊中取出*Temp*  
  
 推入 SS  
  
 推入舊 RSP  
  
 推入 EFLAGS  
  
 推入 CS  
  
 推播*Temp*  
  
 推入錯誤碼 （如果 op 資訊等於 1）  
  
 模擬的 UWOP_PUSH_MACHFRAME 作業遞減 RSP 由 40 （作業資訊會等於 0） 或 48 （op 資訊等於 1）。  
  
 **作業資訊**  
 這些 4 個位元的意義取決於作業程式碼。 若要編碼的一般用途 （整數） 暫存器，請使用下列對應：  
  
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
|8 到 15|若要 R15 R8|  
  
## <a name="see-also"></a>另請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)