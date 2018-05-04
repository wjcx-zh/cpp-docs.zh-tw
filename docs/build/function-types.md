---
title: 函式類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322bd45abbfe217671fd39f0617987fde21445db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="function-types"></a>函式類型
基本上有兩種類型的函式。 畫面格函式呼叫需要堆疊框架的函式。 不需要堆疊框架的函式稱為分葉函式。  
  
 畫面格函式是函式，會配置堆疊空間、 呼叫其他函式，將儲存靜態暫存器，或使用例外狀況處理。 它也需要函式表格項目。 畫面格函式需要初構和終解。 畫面格函式可以動態配置堆疊空間，而且可以使用框架指標。 框架函式有完整的功能，在進行處置時呼叫標準。  
  
 如果框架函式不會呼叫其他函式，則不需要對齊堆疊 (> 一節中所參考[堆疊配置](../build/stack-allocation.md))。  
  
 分葉函式是不需要函式表格項目。 它無法變更任何靜態暫存器，包括 RSP，這表示無法呼叫任何函數或配置堆疊空間。 允許它不會損壞堆疊未對齊時，它會執行。  
  
## <a name="see-also"></a>另請參閱  
 [堆疊使用方式](../build/stack-usage.md)
