---
title: "struct UNWIND_CODE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# struct UNWIND_CODE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

回溯程式碼陣列是用來將影響靜態暫存器和 RSP 的作業序列 \(Sequence\) 記錄到初構 \(Prolog\) 中。  每個程式碼項目都具有下列格式：  
  
|||  
|-|-|  
|UBYTE|初構中的位移|  
|UBYTE: 4|回溯作業程式碼|  
|UBYTE: 4|作業資訊|  
  
 陣列會依初構中位移的遞減順序來排序。  
  
 **初構中的位移**  
 從執行此作業的指示結尾之初構開頭位移，加上 1 \(亦即下一個指示之開頭的位移\)。  
  
 **回溯作業程式碼**  
 注意：部分作業程式碼要求本機堆疊框架 \(Stack Frame\) 中的位移值必須是不帶正負號 \(Unsigned\) 的位移。  這個位移會從固定堆疊配置 \(Stack Allocation\) 的開頭 \(最低位址\) 開始。  如果 UNWIND\_INFO 的 \[框架暫存器\] 欄位為零，表示這個位移從 RSP 開始。  如果 \[框架暫存器\] 欄位為非零值 \(Nonzero\)，表示這是建立 FP 暫存器時 RSP 所在位置的位移。  這等於 FP 暫存器減去 FP 暫存器位移 \(16 \* UNWIND\_INFO 中的數值 \(Scaled\) 框架暫存器位移\)。  如果使用 FP 暫存器，則採用位移的任何回溯程式碼只能在 FP 暫存器已於初構中建立之後使用。  
  
 就 UWOP\_SAVE\_XMM128 和 UWOP\_SAVE\_XMM128\_FAR 以外的所有 opcode 而言，位移一定是 8 的倍數，因為所有相關的堆疊值都是儲存在 8 個位元組界限上 \(堆疊本身一律採用 16 個位元組的對齊方式\)。  如果是使用短位移 \(小於 512 K\) 的作業程式碼，這個程式碼的節點中最終的 USHORT 會存放除以 8 之後的位移。  如果是使用長位移 \(512 K \<\= 位移 \< 4 GB\) 的作業程式碼，這個程式碼的最終兩個 USHORT 節點則會以位元組由小到大的格式存放位移。  
  
 如果是 opcode UWOP\_SAVE\_XMM128 和 UWOP\_SAVE\_XMM128\_FAR，位移一定是 16 的倍數，因為所有的 128 位元 XMM 作業都必須發生在 16 個位元組對齊的記憶體內。  因此，UWOP\_SAVE\_XMM128 會採用 16 這個比例因數，允許小於 1 M 的位移。  
  
 回溯作業程式碼是下列其中一項：  
  
 UWOP\_PUSH\_NONVOL \(0\)1 節點  
  
 推入靜態整數暫存器，從 RSP 每次遞減 8。  作業資訊是暫存器的號碼。  請注意，由於終解 \(Epilog\) 的條件約束 \(Constraint\)，UWOP\_PUSH\_NONVOL 回溯程式碼必須先出現在初構，最後出現在回溯程式碼陣列。  這種相對的順序適用於 UWOP\_PUSH\_MACHFRAME 以外的其他所有回溯程式碼。  
  
 UWOP\_ALLOC\_LARGE \(1\)2 或 3 節點  
  
 在堆疊上配置大尺寸的區域。  有兩個方式：  如果作業資訊等於 0，就會將除以 8 之後的配置大小記錄到下一個位置 \(Slot\)，以允許配置的上限為 512 K – 8。  如果作業資訊等於 1，便會將配置的未縮放 \(Unscaled\) 大小以位元組由小到大的格式記錄到後面兩個位置，以允許配置的上限為 4 GB – 8。  
  
 UWOP\_ALLOC\_SMALL \(2\)1 節點  
  
 在堆疊上配置小尺寸的區域。  配置的大小為作業資訊欄位 \* 8 \+ 8，允許從 8 到 128 個位元組的配置大小。  
  
 堆疊配置的回溯程式碼應該一律採用最短的可能編碼方式：  
  
|||  
|-|-|  
|**配置大小**|**回溯程式碼**|  
|8 到 128 個位元組|UWOP\_ALLOC\_SMALL|  
|136 到 512 K\-8 個位元組|UWOP\_ALLOC\_LARGE, operation info \= 0|  
|512 K 到 4 G–8 個位元組|UWOP\_ALLOC\_LARGE, operation info \= 1|  
  
 UWOP\_SET\_FPREG \(3\)1 節點  
  
 藉由將暫存器設定成目前 RSP 的一些位移，以建立框架指標暫存器。  位移等於 UNWIND\_INFO 中 \[框架暫存器\] 位移 \(縮放\) 欄位 \* 16，允許從 0 到 240 範圍的位移。  使用位移能夠建立指向固定堆疊配置中央的框架指標，並藉由允許更多的存取使用簡短的指示形式，有助於提高程式碼的密度。  請注意，作業資訊欄位為保留欄位，不能使用。  
  
 UWOP\_SAVE\_NONVOL \(4\)2 節點  
  
 使用 MOV \(而非 PUSH\) 將靜態整數暫存器儲存到堆疊上。  這主要用在壓縮包裝 \(Shrink\-Wrapping\)，其中靜態暫存器會儲存到堆疊中先前所配置的位置。  作業資訊是暫存器的號碼。  以 8 為倍數縮放的堆疊位移會記錄在下一個回溯作業程式碼位置上，如前面注意事項所述。  
  
 UWOP\_SAVE\_NONVOL\_FAR \(5\)3 節點  
  
 使用 MOV \(而非 PUSH\)，將靜態整數暫存器以長位移儲存到堆疊上。  這主要用在壓縮包裝 \(Shrink\-Wrapping\)，其中靜態暫存器會儲存到堆疊中先前所配置的位置。  作業資訊是暫存器的號碼。  未縮放的堆疊位移會記錄在後面兩個回溯作業程式碼位置上，如前面注意事項所述。  
  
 UWOP\_SAVE\_XMM128 \(8\)2 節點  
  
 將靜態 XMM 暫存器的全部 128 個位元儲存到堆疊上。  作業資訊是暫存器的號碼。  以 16 為倍數縮放的堆疊位移會記錄到下一個位置。  
  
 UWOP\_SAVE\_XMM128\_FAR \(9\)3 節點  
  
 將靜態 XMM 暫存器的全部 128 個位元以長位移儲存到堆疊上。  作業資訊是暫存器的號碼。  未縮放的堆疊會記錄到後面兩個位置上。  
  
 UWOP\_PUSH\_MACHFRAME \(10\)1 節點  
  
 推入機器框架。  這是用來記錄硬體中斷或例外狀況的影響。  有兩個方式：  如果作業資訊等於 0，表示下列項目已推入堆疊：  
  
|||  
|-|-|  
|RSP\+32|SS|  
|RSP\+24|舊的 RSP|  
|RSP\+16|EFLAGS|  
|RSP\+8|CS|  
|RSP|RIP|  
  
 如果作業資訊等於 1，表示改為推入下列項目：  
  
|||  
|-|-|  
|RSP\+40|SS|  
|RSP\+32|舊的 RSP|  
|RSP\+24|EFLAGS|  
|RSP\+16|CS|  
|RSP\+8|RIP|  
|RSP|錯誤碼|  
  
 這個回溯程式碼將會固定出現在空的初構中，它永遠都不會真的執行，而是會出現在中斷常式的真實進入點 \(Entry Point\)，只為了提供一個位置以模擬推入機器框架的動作而存在。  UWOP\_PUSH\_MACHFRAME 會記錄該項模擬，指出在概念上機器已經完成下列作業：  
  
 從 *Temp* 堆疊頂端移除 RIP 傳回位址  
  
 推入 SS  
  
 推入舊的 RSP  
  
 推入 EFLAGS  
  
 推入 CS  
  
 推入 *Temp*  
  
 推入錯誤碼 \(如果作業資訊等於 1\)  
  
 模擬的 UWOP\_PUSH\_MACHFRAME 作業會將 RSP 每次遞減 40 \(作業資訊等於 0\) 或 48 \(作業資訊等於 1\)。  
  
 **作業資訊**  
 這 4 個位元的意義會依作業程式碼而有所不同。  若要替一般用途 \(整數\) 暫存器編碼，請使用下列對應：  
  
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
|8 至 15|R8 to R15|  
  
## 請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)