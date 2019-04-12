---
title: ARM64 例外狀況處理
ms.date: 11/19/2018
ms.openlocfilehash: 55476119499a3216f6801877dba692b2a0d1d9ee
ms.sourcegitcommit: 88631cecbe3e3fa752eae3ad05b7f9d9f9437b4d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59534119"
---
# <a name="arm64-exception-handling"></a>ARM64 例外狀況處理

Windows 上 ARM64 會使用相同的結構化例外狀況，以處理非同步硬體產生的例外狀況和同步軟體產生的例外狀況的機制。 語言專屬例外狀況處理常式使用語言協助程式函式，以 Windows 結構化例外狀況處理為基礎，進行建置。 本文件說明在 Windows 上 ARM64 和 Microsoft ARM 組譯工具和 MSVC 編譯器所產生的程式碼所使用的語言協助程式中處理的例外狀況。

## <a name="goals-and-motivation"></a>目標和動機

例外狀況回溯資料慣例，以及此描述，被要：

1. 提供足夠的描述，以允許回溯不需要在所有情況下探查的程式碼。

   - 分析程式碼需要分頁中的程式碼。 這可避免回溯，因為在某些情況下，它會很實用 （追蹤、 取樣、 偵錯）。

   - 分析程式碼太複雜;編譯器必須小心只會產生回溯器可以解碼的指示。

   - 如果回溯不能透過使用回溯程式碼完整說明，然後在某些情況下它必須切換回指令解碼。 這會增加整體的複雜度，並在理想情況下會避免。

1. 在中間的初構中回溯和中間的終解的支援。

   - 回溯用於 Windows 的多個例外狀況處理，因此很重要，我們能夠執行正確回溯甚至當中間初構和終解程式碼序列。

1. 需要最少量的空間。

   - 回溯程式碼必須不彙總到二進位的大小會大幅增加。

   - 由於回溯程式碼可能會在記憶體中鎖定，較小的使用量可確保針對每個載入的二進位檔的最少額外負荷。

## <a name="assumptions"></a>假設

在例外狀況處理描述中所做的假設如下：

1. 初構和終傾向於鏡像可能是其他。 藉由利用這個共同的特性，可以大幅減少描述回溯所需的中繼資料的大小。 在函式的主體內，不論是否在初構作業復原，終解作業將會在 正向的方式。 這兩個作業會產生相同的結果。

1. 函式通常對整體來說會較小。 空間的數個最佳化依賴此以達到最有效率的封裝的資料。

1. 終沒有條件式程式碼。

1. 專用的框架指標暫存器：如果預存程序儲存在初構中，註冊其他暫存器 (x29) 維持不變在函式，如此原始 sp 可能隨時復原。

1. 除非 sp 儲存在其他暫存器時，堆疊指標的所有操作都嚴格都發生在初構和終解。

1. 堆疊框架配置被組織的下一節中所述。

## <a name="arm64-stack-frame-layout"></a>ARM64 堆疊框架配置

![堆疊框架配置](media/arm64-exception-handling-stack-frame.png "堆疊框架配置")

框架鏈結函式，fp 和 lr 組可以儲存在變數根據最佳化考量的區域中的任何位置。 目標是要最大化單一框架指標 (x29) 或堆疊指標 (sp) 為基礎的單一指令可以觸達的區域變數的數目。 不過針對`alloca`函式一定會鏈結和 x29 必須指向堆疊的底部。 若要允許更好的暫存器配對-位址-模式涵蓋範圍，靜態暫存器儲存區域都位於區域堆疊的頂端。 以下是範例，說明幾個最有效率的初構序列。 為了清楚起見，較佳的快取位置將被呼叫端儲存的暫存器儲存在所有的標準初構中的順序為"成長設定 」 的順序。 `#framesz` 下面代表 （不含 alloca 區域） 的整個堆疊的大小。 `#localsz` 和`#outsz`指出本機區域大小 (包括儲存區域\<x29，lr > 組) 和分別傳出參數的大小。

1. 鏈結，#localsz \<= 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. 鏈結，#localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. 會見到，分葉函式 (lr 未儲存)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   根據 TECHED-SERVICES 存取所有的區域變數 \<x29，lr > 指向上一個畫面格。 畫面格大小\<= 512，"sp，sub...」 如果移到堆疊底部的 regs 儲存區域，則可以繼續最佳化。 缺點，是範圍的不一致，其他版面配置，並儲存的 regs 掌握組 regs 和前置和後置索引位移的定址模式。

1. 會見到非分葉函式 （lr 儲存區內儲存的 Int）

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   或者，您也可以使用偶數儲存整數暫存器，

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   只有 x19 儲存：

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* 儲存區配置 reg 不會摺成 spanning tree protocol，因為預先索引的 reg lr spanning tree protocol 不可以有回溯程式碼。

   根據 TECHED-SERVICES 存取所有的區域變數 \<x29 > 指向上一個畫面格。

1. 鏈結，#framesz \<= 512，#outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   比較上述 #1 初構，優點，是指示儲存所有暫存器已準備好之後只有一個堆疊配置指示執行。 因此，在預存程序，可防止指令層級平行處理原則沒有任何反的相依性。

1. 鏈結，畫面格大小 > 512 （選擇性沒有 alloca 函式）

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   基於最佳化目的，就可以將放 x29 提供較佳的涵蓋範圍 」 reg 組 」，以及前/後-indexed 位移定址模式的區域中的任何位置。 框架指標下方的 [區域變數] 可以根據 TECHED-SERVICES 存取

1. 鏈結，畫面格大小 > 4 K，不論 alloca()，

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>ARM64 例外狀況處理資訊

### <a name="pdata-records"></a>.pdata 記錄

.Pdata 記錄是固定長度項目會描述 PE 二進位檔中的每一個堆疊操作函式的已排序的陣列。 請小心注意片語 「 堆疊操作 」: 它不需要任何本機儲存體，並不需要儲存/還原靜態暫存器的分葉函式不需要.pdata 記錄;這些應該明確地省略以節省空間。 其中一個這些函式的回溯只可以從 LR 向上移至呼叫端收到的傳回位址。

適用於 ARM64 的每一個.pdata 記錄是 8 個位元組的長度。 每個函式的 32 位元 RVA 開始的第一個字，後面接著第二個與中的記錄位置的一般格式包含可變長度.xdata 區塊指標或描述標準函式回溯序列之封裝字組。

![.pdata 記錄版面配置](media/arm64-exception-handling-pdata-record.png ".pdata 記錄版面配置")

欄位如下所示：

- **函式開始 RVA**是函式開頭的 32 位元 RVA。

- **旗標**是 2 位元欄位，指出如何解譯其餘 30 個位元的第二個.pdata 字組。 如果**旗標**為 0，則其餘位元會構成**例外狀況資訊 RVA** (具有較低的兩個位元隱含為 0)。 如果**旗標**是不是零，則其餘位元會構成**封裝回溯資料**結構。

- **例外狀況資訊 RVA**是.xdata 區段中所儲存的可變長度例外狀況資訊結構的位址。 此資料必須是對齊的 4 位元組。

- **封裝回溯資料**是從函式，假設為標準格式回溯所需的作業的精簡的描述。 在此情況下，不需要 .xdata 記錄。

### <a name="xdata-records"></a>.xdata 記錄

當封裝回溯格式不足以描述函式的回溯時，必須建立可變長度的 .xdata 記錄。 此記錄的位址儲存在 .pdata 記錄的第二個字組。 .xdata 的格式是可變長度的一組封裝字組：

![.xdata 記錄版面配置](media/arm64-exception-handling-xdata-record.png ".xdata 記錄版面配置")

這項資料會分成四個區段：

1. 1 或 2 字組標頭描述結構的整體大小，並提供關鍵函式資料。 第二個 word 才有，如果兩個**終解計數**並**程式碼字組**欄位會設定為 0。 這些是標頭中的位元欄位：

   a. **函式長度**是 18 位元欄位，指出以位元組為單位，除以 4 函式的總長度。 如果函式值大於 1 百萬個項目，然後 pdata 和 xdata 的多個記錄必須用來描述函式。 請參閱[大型函式](#large-functions)一節以取得更多詳細資料。

   b. **Vers**是 2 位元欄位，描述其餘 xdata 的版本。 撰寫本文時，只有版本 0 已定義，並因此不允許的 1 到 3 的值。

   c.  **X**是 1 位元欄位，表示的目前狀態 (1) 與否 (0) 的例外狀況資料。

   d. **E**是一個位元欄位會指出資訊描述單一終解時，會封裝到標頭 (1) 上，而不需要其他範圍字組更新版本 (0)。

   e. **終解計數**是 5 位元欄位，有兩種意義，視狀態而定**E**元：

      1. 如果**E**設為 0： 它會指定第 2 節中所述的終解範圍總數的計數。 如果超過 31 個範圍存在於函式，則**程式碼字組**欄位必須設為 0 指出需要擴充字組。

      2. 如果**E**設為 1，則此欄位會指定描述和只終解之第一個回溯程式碼索引。

   f. **程式碼字組**是 5 位元欄位，指定包含所有第 3 節中的回溯程式碼所需的 32 位元字組的數目。 如果 31 個以上的字組所需 （亦即，多個 124 回溯程式碼位元組），則此欄位必須設為 0 指出需要擴充字組。

   g. **擴充的終解計數**並**擴充程式碼字組**分別為 16 位元和 8 位元欄位、 提供更多空間的編碼方式為異常大數目的終或為異常大數目的回溯程式碼字組。 包含這些欄位的擴充字組才有，如果兩個**終解計數**並**程式碼字組**的第一個標頭文字中的欄位會設定為 0。

1. 標頭和選用延伸的標頭，如果上述步驟之後**終解計數**不是零，是一份終解領域的相關資訊封裝至一個字組，其中一個，以及遞增的開始位移順序儲存。 每個範圍包含下列的位元：

   a. **終解開始位移**是 18 位元欄位，描述以位元組為單位，除以 4，終解相對於函式的開頭的位移

   b. **Res**是 4 位元欄位，保留供未來擴充。 其值必須為 0。

   c.  **終解開始的索引**為 10 位元 (比 2 更多的位元**擴充程式碼字組**) 欄位，指出第一個位元組索引回溯描述此終解程式碼。

1. 之後的終解範圍清單包含回溯程式碼，在稍後的章節將詳細說明的位元組陣列。 此陣列在最近完整字組界面的結尾處填補。 回溯程式碼會寫入至這個陣列中開始的一個最接近的函式，採用函式的邊緣的主體。 每個回溯程式碼的位元組會儲存在位元組由大到小順序讓它們可以提取，直接從最大顯著性位元組開始，其可識別作業和其餘程式碼的長度。

1. 最後，在回溯程式碼位元組中，如果**X**標頭中的位元已設為 1，出現例外狀況處理常式資訊。 這包含單一**例外狀況處理常式 RVA**提供位址的例外狀況處理常式本身，後面緊接跟著的可變長度資料量所需的例外狀況處理常式。

上述的.xdata 記錄的設計可讓您可擷取前 8 個位元組，並從該計算 （減去遵循的可變大小例外狀況資料的長度） 記錄的完整大小。 下列程式碼片段會計算記錄大小：

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

請注意雖然初構和終解中每個有自己的索引，回溯程式碼，它們之間會共用表格，而且很有可能 （且不是完全不常見），它們全都可以共用相同的代碼 （請參閱範例 2 中的範例區段 below below)。 編譯器撰寫者應該最佳化此情況下，特別是因為您可以指定最大索引為 255，以減少特定函式的回溯程式碼的總數。

### <a name="unwind-codes"></a>回溯程式碼

回溯程式碼陣列是說明如何完全恢復作業要復原的順序的初構序列的集區。 回溯程式碼可以視為迷你指令集，編碼為位元組的字串。 執行完成時，要呼叫的函式的傳回位址位於 lr 暫存器和所有非靜態暫存器在呼叫函式時，會還原為其值。

如果已保證例外狀況只會進行函式主體內 （且不可與初構或任何終解），則可能需要要求單一序列。 不過，Windows 回溯模型需要，我們可以從回溯部分執行的初構和終解內。 為了滿足此需求，回溯程式碼有經過仔細設計，使它們會明確地 1 對 1 對應至在初構和終解每個相關作業碼。 這有下列幾個含意：

1. 透過計算回溯程式碼的數目，就可以計算的初構和終解長度。

1. 計算過去的終解範圍開頭的指令數目，就可以跳過相同數目的回溯程式碼，並執行所要完成之部分執行的序列的其餘部分回溯終解程式已執行。

1. 透過計算的初構結尾之前的指令數目，就可以跳過相同數目的回溯程式碼，並執行復原只有這些組件的初構已完成執行順序的其餘部分。

回溯程式碼會根據下表進行編碼。 所有回溯程式碼是單一/雙位元組，除了會配置大量的堆疊。 完全有 21 的回溯程式碼。 每個回溯程式碼對應一個指令，在初構/終解以容許回溯部分執行的初構和終。

|回溯程式碼|位元和轉譯|
|-|-|
|`alloc_s`|000xxxxx： 配置大小的小型堆疊\<512 (2 ^5 * 16)。|
|`save_r19r20_x`|    001zzzzz： 儲存\<x19、 x20 > 組，在 [sp #Z * 8] ！，索引預先位移 > =-248 |
|`save_fplr`|        01zzzzzz： 儲存\<x29，lr > 配對在 [sp + #Z * 8]，位移\<= 504。 |
|`save_fplr_x`|        10zzzzzz： 儲存\<x29，lr > 配對在 [sp-（#Z + 1） * 8] ！，索引預先位移 > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx： 配置大小的大型堆疊\<16k (2 ^11 * 16)。 |
|`save_regp`|        110010xx'xxzzzzzz： 儲存 x(19+#X) 組，在 [sp + #Z * 8]，位移\<= 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: save pair x(19+#X) at [sp-(#Z+1)*8]!, pre-indexed offset >= -512 |
|`save_reg`|        110100xx'xxzzzzzz： 儲存在登錄 x(19+#X) [預存程序 + #Z * 8]，位移\<= 504 |
|`save_reg_x`|        1101010x'xxxzzzzz: save reg x(19+#X) at [sp-(#Z+1)*8]!, pre-indexed offset >= -256 |
|`save_lrpair`|         1101011x'xxzzzzzz: save pair \<x(19+2 *#X),lr> at [sp+#Z*8], offset \<= 504 |
|`save_fregp`|        1101100 x'xxzzzzzz： 儲存在組 d(8+#X) [預存程序 + #Z * 8]，位移\<= 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: save pair d(8+#X), at [sp-(#Z+1)*8]!, pre-indexed offset >= -512 |
|`save_freg`|        1101110 x'xxzzzzzz： 儲存在登錄 d(8+#X) [預存程序 + #Z * 8]，位移\<= 504 |
|`save_freg_x`|        11011110'xxxzzzzz: save reg d(8+#X) at [sp-(#Z+1)*8]!, pre-indexed offset >= -256 |
|`alloc_l`|         11100000' xxxxxxxx 'xxxxxxxx' xxxxxxxx： 配置大小的大型堆疊\<256m (2 ^24 * 16) |
|`set_fp`|        11100001： 設定 x29： 與： mov x29，預存程序 |
|`add_fp`|        11100010' xxxxxxxx： 設定使用 x29: sp，新增 x29，#x * 8 |
|`nop`|            11100011： 沒有回溯會需要作業。 |
|`end`|            11100100： 結尾回溯程式碼。 表示 ret 終解中。 |
|`end_c`|        11100101： 鏈結是目前範圍中的回溯程式碼的結尾。 |
|`save_next`|        11100110： 儲存下一個非暫時性 Int 或 FP 暫存器組。 |
|`arithmetic(add)`|    11100111'000zxxxx: add cookie reg(z) to lr (0=x28, 1=sp); add lr, lr, reg(z) |
|`arithmetic(sub)`|    11100111'001zxxxx: sub cookie reg(z) from lr (0=x28, 1=sp); sub lr, lr, reg(z) |
|`arithmetic(eor)`|    11100111'010zxxxx: eor lr with cookie reg(z) (0=x28, 1=sp); eor lr, lr, reg(z) |
|`arithmetic(rol)`|    11100111' 0110xxxx： 模擬選角色的使用 cookie reg (x28); lrxip0 = neg x28;ror lr xip0 |
|`arithmetic(ror)`|    11100111'100zxxxx: ror lr with cookie reg(z) (0=x28, 1=sp); ror lr, lr, reg(z) |
| |            11100111: xxxz----: ---- reserved |
| |              11101xxx： 保留供自訂的堆疊以下案例只產生 asm 常式 |
| |              11101001:自訂 MSFT_OP_TRAP_FRAME 堆疊 |
| |              11101010:自訂 MSFT_OP_MACHINE_FRAME 堆疊 |
| |              11101011:自訂 MSFT_OP_CONTEXT 堆疊 |
| |              1111xxxx： 保留 |

具有涵蓋多個位元組的大數值的指示，會先儲存的最大顯著性的位元。 上述的回溯程式碼被設計能使得只要查閱此程式碼的第一個位元組，就可以知道以位元組為單位的回溯程式碼的總大小。 假設每個回溯程式碼完全對應到在初構/終解中的指示，來計算大小的初構和終解中，所有必須完成是引導從序列開頭到結尾，以判斷使用的查閱資料表或類似的裝置時間長度 cor是回應的 opcode。

請注意，後置編製索引位移定址不允許在初構中。 所有的位移的範圍 (#Z) 可讓您符合編碼 spanning tree Protocol/STR 定址除了`save_r19r20_x`在哪一個 248 即已足夠輸入所有的儲存區域 （10 的整數暫存器 + 8 FP 暫存器 + 8 輸入的暫存器）。

`save_next` 必須遵循儲存 int 或 FP volatile 註冊組： `save_regp`， `save_regp_x`， `save_fregp`， `save_fregp_x`， `save_r19r20_x`，或另一個`save_next`。 它會儲存到下一個 16 位元位置處的下一步 暫存器組"成長 」 的順序。 `save-next` 遵循`save_next`表示最後一個 Int 暫存器配對指的是第一個 FP 暫存器組。

一般的大小會傳回，並且跳指示相同，因為沒有必要的分隔`end`回溯 tail 呼叫案例的程式碼。

`end_c` 被設計來處理進行最佳化的非連續的函式片段。 A`end_c`表示目前的範圍中的回溯程式碼結尾後面必須接著另一個系列的回溯程式碼以 實際結束`end`。 回溯程式碼之間`end_c`和`end`代表初構中的作業父區域 （「 虛設 」 初構）。  更多詳細資訊和範例節所述。

### <a name="packed-unwind-data"></a>封裝回溯資料

函式的標準格式如下所述，其初構和終遵循封裝回溯資料可用，完全不需要.xdata 記錄，並大幅降低成本提供回溯資料。 標準初構和終專為滿足簡單的函式，不需要例外狀況處理常式，而且會以標準順序執行其設定和拆除作業的一般需求。

封裝的.pdata 記錄格式的回溯資料看起來像這樣：

![.pdata 記錄與封裝回溯資料](media/arm64-exception-handling-packed-unwind-data.png ".pdata 記錄與封裝回溯資料")

欄位如下所示：

- **函式開始 RVA**是函式開頭的 32 位元 RVA。
- **旗標**是 2 位元欄位，如上述，具有下列意義：
  - 00 = 封裝回溯資料未使用;其餘的位元指向.xdata 記錄
  - 01 = 封裝回溯資料使用，如下所述，使用單一的初構和終解的開頭和結尾範圍
  - 10 = 封裝回溯資料使用如下所述的程式碼，而不需要任何初構和終解;這是用於描述分隔的函數區段。
  - 11 = 保留;
- **函式長度**是 11 位元欄位，提供整個函式，以位元組為單位，除以 4 的長度。 如果函式大於 8k，必須改為使用完整.xdata 記錄。
- **框架大小**是 9 位元欄位，表示配置給這個函式，除以 16 的堆疊的位元組數目。 配置大於 (8k-16) 個位元組的堆疊的函式必須使用完整.xdata 記錄。 這包括本機變數的區域，傳出參數區域、 被呼叫端儲存 Int 和 FP 區域，以及主參數 區域中，但不包括動態配置區域。
- **CR**是 2 位元旗標，指出函數是否包含額外的指示，以設定框架鏈結，傳回的連結：
  - 00 = 會見到的函式， \<x29，lr > 組不會儲存在堆疊。
  - 01 = 會見到的函式， \<lr > 會儲存在堆疊
  - 10 = 保留;
  - 11 = 鏈結的函式，將存放區/載入組指示會在初構/終解\<x29，lr >
- **H**是 1 位元旗標，指出是否函式參數寫入堆疊整數參數註冊 (x0 x7)，藉以儲存這些函式的最開頭。 (0 = 不將寄存器，1 = 將寄存器)。
- **RegI**是 4 位元欄位，表示非揮發性 INT 暫存器 (x19 x28) 儲存在標準的堆疊位置數目。
- **RegF**是 3 位元欄位，表示非揮發性 FP 暫存器 (d8-d15) 儲存在標準的堆疊位置數目。 (RegF = 0： 沒有 fp 暫存器儲存;RegF > 0:RegF + 1 FP 暫存器會儲存）。 封裝回溯資料無法用於儲存只有一個 fp 暫存器的函式。

屬於類別 1、 2 （不含連出的 [參數] 區域）、 3 和 4 在上一節中的標準初構可以封裝的回溯格式來表示。  終如標準函式，請遵循類似的表單，除非**H**沒有任何作用，`set_fp`省略指令，而且在終解相反的順序的步驟，以及在每個步驟的指示。 封裝的 xdata 的演算法會遵循下列步驟下, 表所述：

步驟 0:執行預先計算的每個區域的大小。

步驟 1：儲存 Int 被呼叫端儲存的暫存器。

步驟 2：這個步驟是類型 4 最早的章節中的特定項目。 lr 會儲存在 Int 區域結尾處。

步驟 3：儲存 FP 被呼叫端儲存的暫存器。

步驟 4：將輸入引數儲存在家用參數區域。

步驟 5：配置剩餘的講座，包括本機區域中， \<x29，lr > 配對和傳出的參數區域。 5a 對應至標準的類型 1。 5b 和 5c 適用於標準的類型 2。 5d 和 5e 適用於這兩個型別為 3，類型 4。

步驟 #|旗標值|# 個指示|Opcode|回溯程式碼
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** <= 10|RegI / 2 + **RegI** %2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** <=7|(RegF + 1）/2 +<br/>(RegF + 1) %2）。|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 && #locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &&<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** == 11 && #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* 如果**CR** = = 01 並**RegI**是奇數，步驟 2 和步驟 1 中的最後一個 save_rep 會合併成一個 save_regp。

\*\* 如果**RegI** == **CR** = = 0，並**RegF** ！ = 0，第一個 spanning tree protocol，如浮點前置遞減。

\*\*\* 對應至任何指令`mov x29,sp`位於終解。 封裝回溯資料無法使用，如果函式需要的預存程序從 x29 的還原作業。

### <a name="unwinding-partial-prologs-and-epilogs"></a>回溯部分的初構和終

最常見的回溯情況是其中一個函式，從初構和終所有的主體中發生的例外狀況或呼叫的位置。 在此情況下，回溯很簡單： 回溯器只會開始執行回溯陣列從索引 0 開始並繼續直到偵測到結尾作業碼中的程式碼。

它很難正確回溯例外狀況或中斷發生時執行初構和終解的案例。 在這些情況下，只有部分建構的堆疊框架，而訣竅是判斷完全為何以正確地復原它。

比方說，採用這個初構和終解序列：

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

每一個作業碼旁邊是描述這項作業的適當回溯程式碼。 要注意的第一件事是一系列的初構的回溯程式碼完全相同的鏡像映像的終解 （不計入終解最後一個指示） 的回溯程式碼。 這是常見的情況下，並因此回溯初構程式碼一律假定為以相反順序儲存，從初構的執行順序。

因此，對於初構和終解，但還是有一組常用的回溯程式碼：

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

與終解案例 （更多直接了當，即依正常順序），從位移 0 開始終解 （用來啟動位移 0x100 函式中） 內，我們會預期要執行完整回溯序列中，為 「 不會清除尚未完成。 如果我們發現自己在一個指令 （位移 2 終解中），我們可以成功回溯略過第一個回溯程式碼。 一般化這種情況下，假設作業碼之間的 1 對 1 對應回溯程式碼，我們可以狀態，是否我們從終解中的指示 n 開始回溯，我們應該略過第一次 n 回溯程式碼，並開始從該處執行。

事實上，類似的邏輯適用於初構中，但順序相反。 如果我們從初構中的位移 0 開始回溯，我們會想要執行任何動作。 如果我們回溯從位移 2，這是一個指令，然後我們會想要開始執行回溯序列一個回溯程式碼從端 （請記住，程式碼會以反向順序儲存）。 並這裡太我們可以將它一般化，如果我們從初構中的指示 n 開始回溯，我們應該就會執行 n 的回溯程式碼從代碼清單的結尾。

現在，它不一定完全相符的初構和終解程式碼的情況。 基於這個理由，可能需要對回溯陣列包含數個序列的程式碼。 若要判定開始處理程式碼的位置的位移，請使用下列邏輯：

1. 如果從內開始回溯的函式的主體只是開始執行索引 0 處的回溯程式碼，並繼續直到達到 「 結束 」 opcode。

1. 如果在終解中，從開始回溯，使用隨附做為起點的終解範圍終解專屬開始索引。 計算從終解開頭多少個位元組有問題的電腦。 然後向前向前回溯程式碼，直到所有已經執行的指示說明，請略過回溯程式碼。 然後，執行在該位置開始。

1. 如果在初構中，從開始回溯，使用索引 0 做為您的起點。 計算序列中的初構程式碼的長度，然後計算多少個位元組有問題的電腦是從初構的結尾。 然後向前向前回溯程式碼，直到所有尚未執行的指示說明，請略過回溯程式碼。 然後，執行在該位置開始。

如此一來這些規則，初構的回溯程式碼必須一律為陣列中的第一個，而且它們也來進行回溯的一般案例的主體內從回溯程式碼。 任何特定終解程式碼序列應該遵循的後面。

### <a name="function-fragments"></a>函式片段

程式碼最佳化目的和其他原因，它可能會偏好將函式分割成 （也稱為區域） 分隔的片段項目。 每個產生的函式片段時這麼做，需要它自己的個別.pdata （和可能是.xdata） 記錄。

分隔有它自己的初構的第二個片段，它會預期無堆疊調整是在其初構中。 所有堆疊空間所需的次要區域必須預先配置其上層區域 （或稱為的主機區域）。 這完全是在函式的原始初構中保持堆疊指標操作。

函式片段的一般情況是 「 程式碼分離 」，而編譯器可能會移動其主應用程式函式的程式碼區域。 有三個罕見的情況下可能產生的程式碼分離。

#### <a name="example"></a>範例：

- (區域 1： 開始)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (區域 1： 結束)
- (區域 3： 開始)

    ```asm
        ...
    ```

- (區域 3： 結束)
- (區域 2： 開始)

    ```asm
    ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (區域 2： 結束)

1. 只有在初構 (區域 1： 位於不同區域中所有終):

   初構，必須加以描述。 這無法由精簡.pdata 格式表示。 在完整.xdata 案例中，這可以表示 splittunneling 終解計數 = 0。 在上述範例中的區域 1，請參閱。

   回溯程式碼： `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。

1. 只有終 (區域 2： 初構位於主應用程式的區域)

   它會假設，跳到此區域的時間控制項，所有初構程式碼已執行。 部分回溯可能會發生在終為正常函式的相同方式。 無法由精簡.pdata 表示這種類型的區域。 在完整的 xdata 記錄中，它可以編碼與 「 虛設 」 的初構，括住`end_c`和`end`回溯程式碼組。  前置`end_c`指出的初構大小為零。 終解啟動單一終解點做為索引`set_fp`。

   回溯程式碼區域 2: `end_c`， `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。

1. 沒有初構或終 (區域 3： 初構和終所有已在其他片段):

   可以透過設定旗標套用精簡.pdata 格式 = 10。 使用完整.xdata 記錄，終解計數 = 1。 回溯程式碼區域 2 上述相同但終解開始索引也會指向`end_c`。 此區域中的程式碼時，將永遠不會發生部分回溯。

函式片段的另一個更複雜的案例是 「 縮小文繞圖 」 的而編譯器可能會選擇要延遲儲存某些被呼叫端儲存的暫存器，直到外部函式項目初構。

- (區域 1： 開始)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (區域 2： 開始)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (區域 2： 結束)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (區域 1： 結束)

在區域 1 的初構中的堆疊空間會預先配置。 請注意，區域 2 會有相同的回溯程式碼即使在移出其主應用程式函式。

區域 1: `set_fp`， `save_regp 0,240`， `save_fplr_x_256`，`end`終解啟動索引指向`set_fp`像往常一樣。

區域 2: `save_regp 2, 224`， `end_c`， `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。 第一次回溯程式碼指向終解開始索引`save_regp 2, 224`。

### <a name="large-functions"></a>大型函式

片段可以用來說明超過 1 百萬次加諸的限制由.xdata 標頭中的位元欄位的函式。 若要描述非常大的函式，就像這樣，它只需要分割成片段小於 1 百萬個。 應該調整每個片段，使它不會不會終解分割成多個片段。

此函式的第一個片段將會包含初構;所有其他片段都標記為不初構中。 根據存在的終數目，每個片段可能包含零個或多個終。 請記住，每個終解範圍片段中的指定其相對於片段，而不是函式的開頭開始的起始位移。

如果片段沒有初構和終解中沒有，它仍然需要它自己的.pdata （和可能是.xdata） 記錄，以說明如何從函式主體內回溯。

## <a name="examples"></a>範例

### <a name="example-1-frame-chained-compact-form"></a>範例 1：框架鏈結的精簡格式

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>範例 2：框架鏈結完整形式與鏡像初構和終解

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

請注意 EpilogStart 索引 [0]，指向相同的初構回溯程式碼序列。

### <a name="example-3-variadic-unchained-function"></a>範例 3：Variadic 會見到函式

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

注意:初構回溯程式碼 （部分重複使用回溯陣列） 的中間點 EpilogStart 索引 [4]。

## <a name="see-also"></a>另請參閱

[ARM64 ABI 慣例概觀](arm64-windows-abi-conventions.md)<br/>
[ARM 例外狀況處理](arm-exception-handling.md)
