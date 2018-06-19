---
title: 鏈結的回溯資訊結構 |Microsoft 文件
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
ms.openlocfilehash: 87469a381c038462549d20b105b791ddb17b1656
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366948"
---
# <a name="chained-unwind-info-structures"></a>鏈結的回溯資訊結構
如果設定 UNW_FLAG_CHAININFO 旗標，則回溯資訊結構是一個次要且共用的例外狀況處理常式/鏈結-資訊位址欄位會包含主要的回溯資訊。 下列程式碼擷取主要回溯的詳細資訊，但前提`unwindInfo`是具有 UNW_FLAG_CHAININFO 結構的旗標組。  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 鏈結的資訊是在兩個情況下很有用。 首先，它可以用於非連續的程式碼區段。 藉由使用鏈結的資訊，您可以縮小的所需的回溯資訊，因為沒有重複的回溯程式碼陣列，從主要的回溯資訊。  
  
 您也可以將變動性的暫存器儲存使用鏈結的資訊。 編譯器可能會延遲儲存某些動態暫存器，直到它超出函式項目初構。 您可以記錄這讓主要回溯分組程式碼之前，函式的部分資訊，然後設定鏈結為非零的初構，其中鏈結資訊的回溯程式碼反映的靜態暫存器儲存大小資訊。 在此情況下，回溯程式碼是 UWOP_SAVE_NONVOL 所有執行個體。 不支援所使用推入儲存靜態暫存器，或使用額外的固定的堆疊配置來修改 RSP 暫存器群組。  
  
 已設定的 UNW_FLAG_CHAININFO UNWIND_INFO 項目可以包含其 UNWIND_INFO 項目也有設定 （多個壓縮） UNW_FLAG_CHAININFO RUNTIME_FUNCTION 項目。 最後，鏈結的回溯資訊指標將到達 UNWIND_INFO 項目有 UNW_FLAG_CHAININFO 清除。這是主要 UNWIND_INFO 項目，指向實際的程序進入點。  
  
## <a name="see-also"></a>另請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)