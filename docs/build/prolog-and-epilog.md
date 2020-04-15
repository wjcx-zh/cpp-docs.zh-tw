---
title: x64 初構和終解
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328437"
---
# <a name="x64-prolog-and-epilog"></a>x64 初構和終解

分配堆疊空間、調用其他函數、保存非易失性寄存器或使用異常處理的每個函數都必須具有一個 prolog,其位址限制在與相應的函數表條目關聯的展開數據中描述。 有關詳細資訊,請參閱[x64 例外處理](../build/exception-handling-x64.md)。 如有必要,prolog 會在其主位址中保存參數寄存器,在堆疊上推送非易失性寄存器,為局部變數和臨時數據分配堆疊的固定部分,並選擇建立幀指標。 關聯的展開數據必須描述 prolog 的操作,並且必須提供必要的資訊來撤銷 prolog 代碼的效果。

如果堆疊中的固定分配是多個頁面(即大於 4096 位元組),則堆疊分配可能跨越多個虛擬記憶體頁,因此,在分配分配之前必須檢查分配。 為此提供了一個特殊例程,該例程可以從 prolog 調用,並且不會銷毀任何參數寄存器。

保存非易失性寄存器的首選方法是在固定堆疊分配之前將它們移動到堆疊上。 如果在保存非易失性寄存器之前執行固定堆疊分配,則很可能需要 32 位位位位元處理保存的寄存器區域。 (據報導,寄存器的推送與移動一樣快,在可預見的將來,儘管推送之間存在隱含的依賴性,但仍保持此速度。可按任意順序保存非易失寄存器。 但是,在 Prolog 中首次使用非易失性寄存器必須是保存它。

## <a name="prolog-code"></a>Prolog 代碼

典型 prolog 的代碼可能是:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

此 prolog 將參數寄存器 RCX 儲存在其主位置,保存非易失性寄存器 R13-R15,分配堆疊幀的固定部分,並建立一個幀指標,將 128 字節點入固定分配區域。 使用偏移允許使用一位元組偏移處理更多的固定分配區域。

如果固定分配大小大於或等於一頁記憶體,則必須在修改 RSP 之前調用説明器函數。 此幫助程式`__chkstk`探測要分配的堆疊範圍,以確保堆疊得到正確擴展。 在這種情況下,前面的 prolog 示例將改為:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

`__chkstk`説明程式不會修改 R10、R11 和條件代碼以外的任何寄存器。 特別是,它將返回 RAX 不變,並保留所有未修改的非易失寄存器和參數傳遞寄存器。

## <a name="epilog-code"></a>Epilog 代碼

函數的每個出口都存在 Epilog 代碼。 雖然通常只有一個象號,但可以有許多的表觀。 Epilog 代碼將堆疊修剪到其固定分配大小(如有必要),取消分配固定堆疊分配,通過從堆疊中彈出保存的值來還原非易失性寄存器,然後返回。

epilog 代碼必須遵循一組嚴格的解放代碼規則,以便可靠地展開異常和中斷。 這些規則減少了所需的展開數據量,因為無需額外數據來描述每個描述。 相反,展開代碼可以通過向前掃描代碼流來標識表徵來確定正在執行。

如果函數中不使用幀指標,則 epilog 必須首先解調堆疊的固定部分,彈出非易失性寄存器,並將控件返回到調用函數。 例如，

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

如果在函數中使用幀指標,則必須在執行分義之前將堆疊修剪為其固定分配。 從技術上講,此操作不是該說明的一部分。 例如,以下表徵可用於撤銷以前使用的 prolog:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

實際上,當使用幀指標時,沒有充分理由分兩步調整 RSP,因此將改為使用以下表示名詞:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

這些表格是徵詞的唯一合法形式。 `add RSP,constant`它必須由`lea RSP,constant[FPReg]`或 ,後跟一系列零或更多 8 位元組寄存器`return`彈出`jmp`和 a 或 。 (在聲明中只允許`jmp`語句的子集。 子集是具有 ModRM`jmp`記憶體引用的語句類,其中 ModRM mod 欄位值為 00。 `jmp`禁止在與 ModRM mod 欄位值 01 或 10 一起使用聲明。 有關允許的 ModRM 參考的更多資訊,請參閱 AMD x86-64 架構程式師手冊第 3 卷:通用和系統說明中的表 A-15。無法顯示其他代碼。 特別是,無法在分詞中安排任何內容,包括載入返回值。

不使用幀指標時,該表徵必須用於`add RSP,constant`解分配堆疊的固定部分。 它可能不使用`lea RSP,constant[RSP]`。 存在此限制,因此展開代碼在搜索表皮時需要識別的模式較少。

遵循這些規則允許展開代碼確定當前正在執行的表名,並類比對分詞的其餘部分的執行,以允許重新創建調用函數的上下文。

## <a name="see-also"></a>另請參閱

[x64 軟體約定](x64-software-conventions.md)
