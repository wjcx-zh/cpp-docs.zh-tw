---
title: ARM64 例外狀況處理
description: 描述 ARM64 上 windows 所使用的例外狀況處理慣例和資料。
ms.date: 11/19/2018
ms.openlocfilehash: 1ed147a27cfeb545e2a5fe265df8113a5befac73
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72276841"
---
# <a name="arm64-exception-handling"></a>ARM64 例外狀況處理

Windows on ARM64 會針對非同步硬體產生的例外狀況和同步軟體產生的例外狀況，使用相同的結構化例外狀況處理機制。 語言專屬例外狀況處理常式使用語言協助程式函式，以 Windows 結構化例外狀況處理為基礎，進行建置。 本檔說明 Windows on ARM64 的例外狀況處理，以及由 Microsoft ARM 組合器和 MSVC 編譯器所產生之程式碼所使用的語言協助程式。

## <a name="goals-and-motivation"></a>目標和動機

例外狀況回溯資料慣例和此描述適用于：

1. 在所有情況下，提供足夠的描述以允許回溯，而不需要程式碼探查。

   - 分析程式碼需要將程式碼分頁。 這可避免在某些情況下回溯（追蹤、取樣、偵錯工具）。

   - 分析程式碼很複雜;編譯器必須謹慎地產生回溯器可以解碼的指令。

   - 如果回溯無法透過使用回溯代碼來完整描述，在某些情況下，它必須切換回指令解碼。 這會增加整體複雜度，而且最好是避免的。

1. 支援在初初初和 mid 中回溯。

   - 回溯用於 Windows 中，以進行超過例外狀況處理。 程式碼很重要，即使在初構或終解程式碼序列中間也可以正確回溯。

1. 佔用最少的空間。

   - 回溯代碼不得匯總以大幅增加二進位大小。

   - 由於回溯程式碼可能會在記憶體中被鎖定，因此較小的使用量會確保每個載入的二進位檔都有最小的負擔。

## <a name="assumptions"></a>假設

這些假設是在例外狀況處理描述中進行：

1. 初構和 epilogs 通常會彼此鏡像。 藉由利用此共同特性，描述回溯所需的中繼資料大小可以大幅降低。 在函式的主體中，不論初構的作業是否復原，或終的作業都是以正向的方式執行，都不會有任何影響。 這兩個作業會產生相同的結果。

1. 函式通常會整體相對較小。 空間的數個優化會依賴此事實來達到最有效率的資料封裝。

1. Epilogs 中沒有條件式程式碼。

1. 專用框架指標註冊：如果 sp 儲存在初構的另一個暫存器（x29）中，該暫存器在整個函式中維持不變。 這表示原始 sp 可以隨時復原。

1. 除非 sp 儲存在另一個暫存器中，否則堆疊指標的所有操作都會嚴格地在初構和終解中進行。

1. 堆疊框架版面配置的組織方式如下一節所述。

## <a name="arm64-stack-frame-layout"></a>ARM64 堆疊框架版面配置

![堆疊框架版面]配置(media/arm64-exception-handling-stack-frame.png "堆疊框架版面")配置

針對框架連結的函式，可以在本機變數區域中的任何位置儲存 fp 和 lr 配對，視優化考慮而定。 目標是要最大化可透過框架指標（x29）或堆疊指標（sp）的單一指令來達到的區域變數數目。 不過，針對 `alloca` 函式，它必須是連鎖的，而且 x29 必須指向堆疊的底部。 為了允許更好的暫存器成對定址模式涵蓋範圍，非靜態暫存器儲存區域會放在本機區域堆疊的頂端。 以下範例說明數個最有效率的初構序列。 為了清楚且更佳的快取區域，在所有標準初構中儲存被呼叫端儲存的暫存器的順序，都是「成長中」的順序。 底下的 `#framesz` 代表整個堆疊的大小（不包括 alloca 區域）。 `#localsz` 和 `#outsz` 表示區域大小（包括 @no__t 2x29、lr > 配對的儲存區域）和傳出參數大小。

1. 連鎖，#localsz \< = 512

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

1. 連鎖，#localsz > 512

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

1. Unchained，分葉函數（lr 未儲存）

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   所有區域變數都是根據 SP 來存取。 @no__t 0x29，lr > 指向上一個畫面。 針對框架大小 \< = 512，"sub sp，..."如果 regs 儲存的區域移至堆疊底部，可以將其優化。 缺點是它與上述的其他版面配置不一致，而且儲存的 regs 會納入 regs 的範圍，以及前置和後置索引的位移定址模式。

1. Unchained，非分葉函式（lr 會儲存在 Int 儲存的區域中）

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   或者，使用偶數儲存的 Int 暫存器，

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   僅儲存 x19：

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \*，reg 儲存區域配置不會折迭到 stp，因為預先編制索引的 reg-lr stp 無法以回溯代碼表示。

   所有區域變數都是根據 SP 來存取。 @no__t 0x29 > 指向上一個畫面格。

1. 連鎖，#framesz \< = 512，#outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   相較于上述的第一個初構範例，此處的優點是所有的暫存器儲存指示都已準備好在只有一個堆疊配置指令之後執行。 這表示不會對 sp 造成任何阻礙，因為它會阻止指令層級平行處理。

1. 連鎖，框架大小 > 512 （選擇性用於沒有 alloca 的函式）

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   基於優化目的，x29 可以放在當地區域中的任何位置，以提供更好的「reg 組」和預先/post-indexed 的位移定址模式的涵蓋範圍。 您可以根據 SP 來存取下列框架指標下方的區域變數。

1. 連鎖，框架大小 > 4K，有或不含 alloca （），

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

### <a name="pdata-records"></a>。 pdata 記錄

Pdata 記錄是固定長度專案的已排序陣列，描述 PE 二進位檔中的每個堆疊操作函數。 「堆疊操作」一詞很重要：不需要任何本機儲存區的分葉函數，而且不需要儲存/還原非變動暫存器，也不需要 pdata 記錄。 這些記錄應該明確地省略以節省空間。 其中一個函式的回溯可以直接從 LR 取得傳回位址，以向上移動到呼叫端。

ARM64 的每個 pdata 記錄長度為8個位元組。 每筆記錄的一般格式會將函式的32位 RVA 放在第一個單字中，後面接著第二個單字，其中包含 .xdata 區塊的指標，或描述標準函式回溯順序的封裝字組。

![。 pdata 記錄版面]配置(media/arm64-exception-handling-pdata-record.png ". pdata 記錄")配置

欄位如下所示：

- 函式**啟動 RVA**是函數開頭的32位 rva。

- **旗**標是2位欄位，表示如何解讀第二個 pdata 字的剩餘30位。 如果**旗**標為0，則其餘的位會形成**例外狀況資訊 RVA** （具有兩個最低位隱含0）。 如果**旗**標為非零，則其餘的位會形成**封裝**的回溯資料結構。

- **例外狀況資訊 RVA**是 .xdata 區段中所儲存之可變長度例外狀況資訊結構的位址。 此資料必須是對齊的 4 位元組。

- **封裝**的回溯資料是從函式回溯所需作業的壓縮描述，假設是標準格式。 在此情況下，不需要 .xdata 記錄。

### <a name="xdata-records"></a>。 .xdata 記錄

當封裝回溯格式不足以描述函式的回溯時，必須建立可變長度的 .xdata 記錄。 此記錄的位址儲存在 .pdata 記錄的第二個字組。 .Xdata 的格式是一組已壓縮的可變長度文字：

![。 .xdata 記錄版面]配置(media/arm64-exception-handling-xdata-record.png ". .xdata 記錄")配置

此資料分為四個區段：

1. 描述結構整體大小和提供關鍵函數資料的1或2個字組標頭。 只有當 [終**計數**] 和 [程式**代碼字**] 欄位都設定為0時，才會出現第二個單字。 標頭具有下列位欄位：

   a. **函數長度**是18位欄位。 它會指出函式的總長度（以位元組為單位），除以4。 如果函式大於1M，則必須使用多個 pdata 和. .xdata 記錄來描述函數。 如需詳細資訊，請參閱[大型函數](#large-functions)一節。

   b. [使用 **] 是 2**位欄位。 它會描述其餘 .xdata 的版本。 目前只會定義版本0，因此不允許1-3 的值。

   c. **X**是1位欄位。 它表示例外狀況資料的目前狀態（1）或缺勤（0）。

   d. **E**是1位欄位。 這表示描述單一終終的資訊會封裝成標頭（1），而不是稍後需要額外的範圍字組（0）。

   e. [終**計數**] 是有兩個意義的5位欄位，視**電子**位的狀態而定：

      1. 如果**E**為0，它會指定第2節中所述的終解範圍總數。 如果函式中存在超過31個範圍，則 [程式**代碼文字**] 欄位必須設定為0，以指出需要擴充字組。

      2. 如果**E**是1，則此欄位會指定第一個回溯程式碼的索引，以描述其中一個，而且只會進行終解。

   f. 程式**代碼字**是一個5位欄位，指定包含第3節中所有回溯程式碼所需的32位字組數目。 如果需要超過31個單字（也就是，如果有超過124個回溯程式碼位元組），則此欄位必須為0，以指出需要擴充字組。

   g. **擴充**的終數和擴充的程式**代碼字**組分別是16位和8位的欄位。 它們提供更多的空間來編碼異常大量的 epilogs，或異常大量的回溯程式碼字組。 只有當第一個標頭字組中的 [終**計數**] 和 [程式**代碼文字**] 欄位為0時，才會顯示包含這些欄位的副檔名字組。

1. 如果終**數**不是零，則會在標頭和選用的擴充標頭之後，將有關終解範圍的資訊清單（封裝一個到單字）。 它們是以增加的起始位移順序儲存。 每個範圍都包含下列位：

   a. 終解**開始位移**是一個18位欄位，其位移是以位元組為單位，除以4，相對於函式的開頭。

   b. **Res**是保留給未來擴充的4位欄位。 其值必須為 0。

   c. 終解**開始索引**是10位欄位（比擴充的程式**代碼字**多2個位）。 它會指出第一個描述此終解的回溯程式碼的位元組索引。

1. 在終的範圍清單之後，會產生包含回溯程式碼的位元組陣列，稍後的章節會有詳細說明。 此陣列在最近完整字組界面的結尾處填補。 回溯代碼會寫入至此陣列。 它們會從最接近函式主體的開始，並移至函式的邊緣。 每一個回溯程式碼的位元組都是以位元組由大到小的順序儲存，因此可以直接提取，從最重要的位元組開始，以識別作業和其餘程式碼的長度。

1. 最後，在回溯程式碼位元組之後，如果標頭中的**X**位設為1，則會提供例外狀況處理常式資訊。 它是由單一**例外狀況處理常式 RVA**所組成，它會提供例外狀況處理常式本身的位址。 其後緊接著例外狀況處理常式所需的可變長度資料量。

.Xdata 記錄的設計可讓您提取前8個位元組，並使用它們來計算記錄的完整大小，減去後面的可變大小例外狀況資料的長度。 下列程式碼片段會計算記錄大小：

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

雖然初構和每個終解在回溯程式碼中都有自己的索引，但資料表會在它們之間共用。 所有人都可以共用相同的程式碼，完全可行（而且並非完全常見）。 （如需範例，請參閱[範例](#examples)一節中的範例2）。編譯器撰寫者應該針對此案例進行優化，特別是因為可指定的最大索引為255，這會限制特定函數的回溯程式碼總數。

### <a name="unwind-codes"></a>回溯代碼

回溯程式碼的陣列是一組時序的集區，這些順序描述了如何復原初構的效果，並以作業需要復原的相同順序儲存。 回溯代碼可以視為小型指令集，並編碼為位元組的字串。 執行完成時，呼叫函式的傳回位址會位於 lr 暫存器中。 而且，所有的非 volatile 暫存器都會在呼叫函數時還原為其值。

如果例外狀況保證只會發生在函式主體內，而不是在初構或任何終解中，則只需要一個序列。 不過，Windows 回溯模型要求程式碼可以從部分執行的初構或終解中回溯。 為了符合這項需求，已仔細設計回溯代碼，使其能夠明確地將1:1 對應至初構和終解中的每個相關 opcode。 這種設計有幾項含意：

1. 藉由計算回溯程式碼的數目，可以計算初構和終解的長度。

1. 藉由計算結束範圍開始之後的指示數目，就可以略過對等的回溯程式碼數目。 然後，我們可以執行序列的其餘部分，以完成終完成的部分執行回溯。

1. 藉由計算初構結尾之前的指令數目，就可以略過相同數目的回溯程式碼。 然後，我們可以執行序列的其餘部分，只復原已完成執行的初構部分。

回溯代碼是根據下表進行編碼。 所有回溯程式碼都是單一/雙位元組，但配置大型堆疊的則除外。 完全有21個回溯程式碼。 每個回溯程式碼只會對應初構/終解中的一個指令，以允許回溯部分執行的初構和 epilogs。

|回溯程式碼|位和轉譯|
|-|-|
|`alloc_s`|000xxxxx：配置大小 \< 512 （2 ^ 5 * 16）的小型堆疊。|
|`save_r19r20_x`|    001zzzzz：將 \<x19、x20 > 組儲存在 `[sp-#Z*8]!`，預先索引的位移 > =-248 |
|`save_fplr`|        01zzzzzz：將 \<x29、lr > 組儲存在 `[sp+#Z*8]`，offset \< = 504。 |
|`save_fplr_x`|        10zzzzzz：儲存 \<x29、lr > 配對 `[sp-(#Z+1)*8]!`，預先索引的位移 > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx：配置大小 \< 16k （2 ^ 11 * 16）的大型堆疊。 |
|`save_regp`|        110010xx'xxzzzzzz：將 x （19 + #X）配對儲存 `[sp+#Z*8]`，位移 \< = 504 |
|`save_regp_x`|        110011xx'xxzzzzzz：在 `[sp-(#Z+1)*8]!`、預先索引的位移 > =-512 儲存配對 x （19 + #X） |
|`save_reg`|        110100xx'xxzzzzzz：將 reg x （19 + #X）儲存在 `[sp+#Z*8]`，offset \< = 504 |
|`save_reg_x`|        1101010x'xxxzzzzz：將 reg x （19 + #X）儲存在 `[sp-(#Z+1)*8]!`，預先索引的位移 > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz：儲存組 \<x （19 + 2 * #X），lr > 于 `[sp+#Z*8]`，位移 \< = 504 |
|`save_fregp`|        1101100x'xxzzzzzz：將 d （8 + #X）儲存在 `[sp+#Z*8]`，位移 \< = 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz： save d （8 + #X），在 `[sp-(#Z+1)*8]!`，預先索引的位移 > =-512 |
|`save_freg`|        1101110x'xxzzzzzz：將 reg d （8 + #X）儲存在 `[sp+#Z*8]`，offset \< = 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz：將 reg d （8 + #X）儲存在 `[sp-(#Z+1)*8]!`，預先索引的位移 > =-256 |
|`alloc_l`|         11100000 ' xxxxxxxx'xxxxxxxx'xxxxxxxx：配置大小 \< 的大型堆疊256M （2 ^ 24 * 16） |
|`set_fp`|        11100001：設定 x29： with： `mov x29,sp` |
|`add_fp`|        11100010 ' xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx：使用下列方式設定 x29： `add x29,sp,#x*8` |
|`nop`|            11100011：不需要回溯作業。 |
|`end`|            11100100：回溯程式碼結束。 意指在終解中的 ret。 |
|`end_c`|        11100101：目前連結範圍中的回溯程式碼結束。 |
|`save_next`|        11100110：儲存下一個非 volatile Int 或 FP 暫存器配對。 |
|`arithmetic(add)`|    11100111 ' 000zxxxx：將 cookie reg （z）新增至 lr （0 = x28，1 = sp）;`add lr, lr, reg(z)` |
|`arithmetic(sub)`|    11100111 ' 001zxxxx：來自 lr 的 sub cookie reg （z）（0 = x28，1 = sp）;`sub lr, lr, reg(z)` |
|`arithmetic(eor)`|    11100111 ' 010zxxxx： eor lr with cookie reg （z）（0 = x28，1 = sp）;`eor lr, lr, reg(z)` |
|`arithmetic(rol)`|    11100111 ' 0110xxxx：具有 cookie reg 的 lr 模擬 rol （x28）;xip0 = neg x28;`ror lr, xip0` |
|`arithmetic(ror)`|    11100111 ' 100zxxxx： ror lr with cookie reg （z）（0 = x28，1 = sp）;`ror lr, lr, reg(z)` |
| |            11100111： xxxz----：----保留 |
| |              11101xxx：只為 asm 常式產生的自訂堆疊案例保留 |
| |              11101000：MSFT_OP_TRAP_FRAME 的自訂堆疊 |
| |              11101001：MSFT_OP_MACHINE_FRAME 的自訂堆疊 |
| |              11101010：MSFT_OP_CONTEXT 的自訂堆疊 |
| |              11101100：MSFT_OP_CLEAR_UNWOUND_TO_CALL 的自訂堆疊 |
| |              1111xxxx：已保留 |

在涵蓋多個位元組的大型值指示中，會先儲存最重要的位。 這項設計可讓您藉由只查閱程式碼的第一個位元組，來找出回溯程式碼的總大小（以位元組為單位）。 由於每個回溯程式碼都會與初構或終解中的指令完全對應，因此您可以計算初構或終解的大小。 您可以從序列開頭到結尾處進行，並使用查閱資料表或類似的裝置來判斷對應的 opcode 的時間長度。

在初構中不允許使用後置索引位移定址。 所有位移範圍（#Z）都符合 STP/STR 定址的編碼（`save_r19r20_x` 除外），在這種情況下，248對所有儲存區域都已足夠（10個 Int 暫存器 + 8 FP 暫存器 + 8 個輸入暫存器）。

`save_next` 必須遵循 Int 或 FP volatile 暫存器配對的儲存： `save_regp`、`save_regp_x`、`save_fregp`、`save_fregp_x`、`save_r19r20_x` 或另一個 `save_next`。 它會在接下來的16個位元組插槽中，將下一個暫存器配對儲存在「成長」的順序中。 @No__t-0 指的是第一個 FP 暫存器配對，其遵循代表最後一個 Int 暫存器配對的 `save-next`。

由於一般傳回和跳躍指示的大小相同，因此不需要針對尾呼叫案例使用分隔的 @no__t 0 回溯程式碼。

`end_c` 是設計用來處理不連續的函式片段，以供優化之用。 表示目前範圍中回溯程式碼結尾的 `end_c`，後面必須接著以 real `end` 結束的另一系列回溯程式碼。 @No__t-0 和 `end` 之間的回溯代碼代表父區域（"虛設" 初構）中的初構作業。  如需更多詳細資料和範例，請參閱下一節。

### <a name="packed-unwind-data"></a>封裝的回溯資料

對於初構和 epilogs 遵循以下所述標準格式的函式，可以使用封裝的回溯資料。 它完全不需要 .xdata 記錄，而且能大幅降低提供回溯資料的成本。 標準初構和 epilogs 是設計來符合簡單函數的一般需求：一個不需要例外狀況處理常式，而是以標準循序執行其設定和清除作業。

具有封裝之回溯資料的 pdata 記錄格式看起來像這樣：

。具有已封裝之回溯資料的![pdata 記錄](media/arm64-exception-handling-packed-unwind-data.png "。 pdata 記錄具有已封裝的回溯資料")

欄位如下所示：

- 函式**啟動 RVA**是函數開頭的32位 rva。
- **旗**標是如上所述的2位欄位，具有下列意義：
  - 00 = 未使用封裝的回溯資料;剩餘的位指向 .xdata 記錄
  - 01 = 搭配單一初構使用的封裝回溯資料，並在範圍的開頭和結尾終止
  - 10 = 封裝的回溯資料，用於沒有任何初構和終解的程式碼。 適用于描述分隔的函數區段
  - 11 = 保留。
- **函數長度**是一個11位欄位，提供整個函式的長度（以位元組為單位），除以4。 如果函數大於8k，則必須改用完整的 .xdata 記錄。
- **畫面格大小**是9位欄位，指出配置給此函式的堆疊位元組數（除以16）。 配置大於（8k-16）個位元組之堆疊的函數必須使用完整的 .xdata 記錄。 其中包含本機變數區域、傳出參數區域、被呼叫者儲存的 Int 和 FP 區域，以及 home 參數區域，但會排除動態配置區域。
- **CR**是2位旗標，指出函式是否包含設定框架鏈和傳回連結的額外指示：
  - 00 = unchained 函式，@no__t 0x29，lr > 配對不會儲存在堆疊中。
  - 01 = unchained 函數，@no__t 0lr > 儲存在堆疊中
  - 10 = 保留;
  - 11 = 連結函式，在初構/終解中使用存放/負載配對指令 \<x29，lr >
- **H**是1位旗標，指出函式在函式的開頭是否會將它儲存在函式的最開頭，以註冊（x0-7）函數。 （0 = 不是 home 暫存器，1 = 家庭暫存器）。
- **RegI**是4位欄位，指出標準堆疊位置中儲存的非 volatile INT 暫存器（x19-x28）數目。
- **RegF**是3位欄位，指出標準堆疊位置中儲存的非 volatile FP 暫存器（d8-d15）數目。 （RegF = 0：未儲存 FP 暫存器;RegF > 0：會儲存 RegF + 1 FP 暫存器）。 封裝的回溯資料無法用於只儲存一個 FP 暫存器的函式。

屬於類別1、2（不含傳出參數區域）、3和4的標準初構會以封裝的回溯格式來表示。  標準函式的 epilogs 遵循類似的格式，但**H**不會有任何作用、省略了 `set_fp` 指令，而且每個步驟中的指令順序會在終止時反轉。 .Xdata 的演算法會遵循下列步驟，如下表所述：

步驟 0：預先計算每個區域的大小。

步驟 1:儲存 Int 被呼叫端-已儲存的暫存器。

步驟 2:此步驟適用于早期區段中的類型4。 lr 會儲存在 Int 區域的結尾。

步驟 3：儲存 FP 被呼叫端-已儲存的暫存器。

步驟 4：將輸入引數儲存在 home 參數區域中。

步驟 5：配置剩餘的堆疊，包括區域、@no__t 0x29、lr > 配對和傳出參數區域。 5a 對應至標準類型1。 5b 和5c 適用于標準類型2。 5d 和5e 適用于類型3和類型4。

步驟#|旗標值|指示數目|Opcode|回溯程式碼
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** < = 10|RegI/2 + **RegI** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|（RegF + 1）/2 +<br/>（RegF + 1）% 2）|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 & & #locsz<br/> < = 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &&<br/>512 < #locsz < = 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 & & #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* 如果**CR** = = 01，而**RegI**是奇數，則步驟1中的步驟2和最後一個 save_rep 會合並成一個 save_regp。

\* @ no__t-1，如果**RegI** == **CR** = = 0，而**RegF** ！ = 0，則浮點的第一個 stp 會執行前置遞減。

\* @ no__t-1 @ no__t-2 不會有對應至終的 `mov x29,sp` 的指示。 如果函數需要從 x29 還原 sp，則無法使用封裝的回溯資料。

### <a name="unwinding-partial-prologs-and-epilogs"></a>回溯部分初構和 epilogs

最常見的回溯情況是在函式主體中發生例外狀況或呼叫，而不是從初構和所有 epilogs。 在這種情況下，回溯很簡單：回溯器只會開始執行從索引0開始的回溯陣列中的程式碼，並繼續直到偵測到結束 opcode。

在執行初構或終解時，如果發生例外狀況或中斷，則更難以正確回溯。 在這些情況下，只會部分結構化堆疊框架。 問題在於判斷完成的動作，以正確地復原。

例如，採用這個初構和終解序列：

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

每個 opcode 的旁邊是描述這項作業的適當回溯程式碼。 您可以看到初構的一系列回溯程式碼如何為終解的回溯程式碼的確切鏡像影像（不計算終解的最後一個指令）。 這是常見的情況，因此我們一律會假設初構的回溯程式碼是從初構的執行順序以相反順序儲存。

因此，在初構和終初，我們都會留下一組常用的回溯程式碼：

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

終的情況很簡單，因為它是正常的順序。 從終開始（在函式中從 offset 0x100 開始），我們預期會執行完整回溯順序，因為尚未進行清除。 如果我們在中發現自己的一個指示（在終的位移2），我們可以略過第一個回溯程式碼，成功回溯。 我們可以將這種情況一般化，並假設 opcode 和回溯代碼之間的1:1 對應。 然後，若要從終的指令*n*開始回溯，我們應該略過前*n*個回溯代碼，然後從該處開始執行。

其實初構的類似邏輯也適用于初構，但相反。 如果我們從初構中的位移0開始回溯，我們想要執行任何操作。 如果我們從 offset 2 回溯（這是中的一個指令），那麼我們想要從結尾開始執行回溯序列一個回溯程式碼。 （請記住，代碼會以反向順序儲存）。此外，我們也可以一般化：如果我們從初構中的指令 n 開始回溯，則應該從代碼清單的結尾開始執行 n 回溯代碼。

不一定是初構和終解程式碼完全相符的情況。 這就是為什麼回溯陣列可能需要包含數個程式碼序列的原因。 若要判斷開始處理代碼的位移，請使用下列邏輯：

1. 如果是從函式主體內回溯，請在索引0開始執行回溯程式碼，並繼續進行，直到達到「結束」 opcode 為止。

1. 如果從終解內回溯，請使用以終範圍提供的終解特定起始索引做為起點。 計算有問題的電腦從終開始的多少位元組。 然後向前復原回溯程式碼，略過回溯程式碼，直到所有已執行的指令都列入考慮為止。 然後從該點開始執行。

1. 如果從初構內回溯，請使用索引0做為起點。 計算序列中初構程式碼的長度，然後計算有問題的電腦與初構結尾的位元組數目。 然後向前推進回溯程式碼，略過回溯程式碼，直到所有尚未執行的指令都列入考慮為止。 然後從該點開始執行。

這些規則表示初構的回溯程式碼必須一律為數組中的第一個。 此外，它們也是用來在從主體內回溯的一般情況下回溯的代碼。 任何終解特定的程式碼序列應該緊接在之後。

### <a name="function-fragments"></a>函數片段

基於程式碼優化的目的和其他原因，最好是將函式分割成分隔的片段（也稱為「區域」）。 分割時，每個產生的函式片段都需要它自己的個別 pdata （可能是 .xdata）記錄。

針對每個具有自己初構的分隔次要片段，預期在其初構中不會進行堆疊調整。 次要區域所需的所有堆疊空間都必須由其父區域（或稱為「主機區域」）預先配置。 這會在函式的原始初構中嚴格保持堆疊指標操作。

函式片段的一般情況是「程式碼分隔」，而該編譯器可能會將程式碼區域移出其主機函式。 有三種異常情況，可能是程式碼分離所造成。

#### <a name="example"></a>範例

- （區域1：開始）

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- （區域1：結束）

- （區域3：開始）

    ```asm
        ...
    ```

- （區域3：結束）

- （區域2：開始）

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- （區域2：結束）

1. 僅初構（區域1：所有 epilogs 都位於不同的區域）：

   僅必須描述初構。 這不能以 pdata 格式表示。 在 .xdata 的案例中，可以藉由設定終計數 = 0 來表示。 請參閱上述範例中的區域1。

   回溯代碼： `set_fp`，`save_regp 0,240`，`save_fplr_x_256`，`end`。

1. 僅限 Epilogs （區域2：初構位於主機區域）

   這是假設，當時間控制項跳入此區域時，就會執行所有初構程式碼。 部分回溯可能會在 epilogs 中發生，方式與一般函式相同。 此類型的區域無法以 pdata 表示。 在完整的 .xdata 記錄中，可以使用「虛設」初構來編碼，並以 @no__t 0 和 @no__t 1 回溯程式碼配對括住。  前置的 `end_c` 表示初構的大小為零。 將單一終解點的開始索引到 `set_fp`。

   區域2： `end_c`，`set_fp`，`save_regp 0,240`，`save_fplr_x_256`，`end` 的回溯程式碼。

1. 沒有初構或 epilogs （區域3：初構和所有 epilogs 都在其他片段中）：

   Pdata 格式可以透過設定旗標 = 10 來套用。 具有完整的 .xdata 記錄，終計數 = 1。 回溯程式碼等同于上述區域2的程式碼，但終解開始索引也會指向 `end_c`。 部分回溯永遠不會發生在此程式碼區域中。

另一個更複雜的函數片段案例是「壓縮包裝」。 編譯器可能會選擇延遲儲存一些被呼叫端儲存的暫存器，直到函式進入初構的外部。

- （區域1：開始）

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- （區域2：開始）

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- （區域2：結束）

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- （區域1：結束）

在區域1的初構中，會預先配置堆疊空間。 您可以看到區域2會有相同的回溯程式碼，即使它已移出其主機函式也一樣。

區域1： `set_fp`，`save_regp 0,240`，`save_fplr_x_256`，`end`，並以平常的方式將開始索引點與 `set_fp` 進行比對。

區域2： `save_regp 2, 224`，`end_c`，`set_fp`，`save_regp 0,240`，`save_fplr_x_256`，`end`。 終解開始索引點到第一個回溯程式碼 `save_regp 2, 224`。

### <a name="large-functions"></a>大型函式

片段可以用來描述大於 .xdata 標頭中位欄位所加上1M 限制的功能。 為了描述非常大的函式，它必須分解成小於1M 的片段。 每個片段都應該調整，讓它不會將終解分割成多個部分。

只有函式的第一個片段會包含初構。所有其他片段都會標示為沒有初構。 根據目前的 epilogs 數目，每個片段可能包含零個或多個 epilogs。 請記住，片段中的每個終解範圍都會指定相對於片段開頭的起始位移，而不是函式的開頭。

如果片段沒有初構且沒有終解，它仍需要它自己的 pdata （可能是 .xdata）記錄，以描述如何從函式主體內回溯。

## <a name="examples"></a>範例

### <a name="example-1-frame-chained-compact-form"></a>範例 1：框架-連鎖，compact-表單

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>範例 2：具有鏡像初構 & 終的框架連結、完整形式

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

終解開始索引 [0] 指向相同的初構回溯程式碼序列。

### <a name="example-3-variadic-unchained-function"></a>範例 3：Variadic unchained 函式

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

終解開始索引 [4] 指向初構回溯程式碼的中間（部分重複使用的回溯陣列）。

## <a name="see-also"></a>另請參閱

[ARM64 ABI 慣例的總覽](arm64-windows-abi-conventions.md)<br/>
[ARM 例外狀況處理](arm-exception-handling.md)
