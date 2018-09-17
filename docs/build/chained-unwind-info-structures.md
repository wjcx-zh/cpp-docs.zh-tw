---
title: 鏈結的回溯資訊結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6da09387595188026d855fb99a49b588e6f21aa3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715022"
---
# <a name="chained-unwind-info-structures"></a>鏈結的回溯資訊結構

如果已設定 UNW_FLAG_CHAININFO 旗標，則回溯資訊結構是次要，並共用例外狀況處理常式/鏈結-資訊的地址欄位包含主要的回溯資訊。 下列程式碼會擷取主要回溯的詳細資訊，但前提`unwindInfo`是結構，其 UNW_FLAG_CHAININFO 旗標設定。

```
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

鏈結的資訊可用於兩種情況。 首先，它可以用於非連續的程式碼區段。 藉由使用鏈結的資訊，您可以減少必要的回溯資訊，因為您沒有重複的回溯程式碼陣列，從主要的回溯資訊。

您也可以將變動性的暫存器儲存使用鏈結的資訊。 編譯器可能會延遲儲存一些動態暫存器，直到它超出函式項目初構。 您可以將此資訊記錄讓主要的回溯資訊所屬的群組程式碼之前，此函式，然後設定鏈結與為非零的初構，其中的鏈結資訊中的回溯程式碼反映的靜態暫存器儲存大小的資訊。 在此情況下，回溯程式碼是 UWOP_SAVE_NONVOL 的所有執行個體。 不支援使用推入儲存靜態暫存器，或使用其他固定的堆疊配置來修改 RSP 暫存器群組。

已設定的 UNW_FLAG_CHAININFO UNWIND_INFO 項目可以包含其 UNWIND_INFO 項目也會有設定 （多個包裝） UNW_FLAG_CHAININFO RUNTIME_FUNCTION 項目。 最後，鏈結的回溯資訊指標將會看見已清除; UNW_FLAG_CHAININFO UNWIND_INFO 項目這是主要的 UNWIND_INFO 項目，它會指向實際的程序進入點。

## <a name="see-also"></a>另請參閱

[回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)