---
title: 函式類型 |Microsoft Docs
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
ms.openlocfilehash: 6dfb36dc9e177fdb9ad196c0e2a8ad0f352d5f2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709562"
---
# <a name="function-types"></a>函式類型

基本上有兩種類型的函式。 需要的堆疊框架的函式會呼叫框架函式。 不需要堆疊框架的函式稱為分葉函式。

畫面格函式是配置堆疊空間，會呼叫其他函式、 將儲存靜態暫存器，或使用例外狀況處理函式。 您也必須以函式的資料表項目。 畫面格函式需要初構和終解。 畫面格函式可以動態地配置堆疊空間，而且可以利用框架指標。 框架函式具有完整的功能，呼叫標準，其可供使用。

如果框架函式不會呼叫另一個函式，則不需要對齊堆疊 (參考一節[堆疊配置](../build/stack-allocation.md))。

分葉函式是不需要函式表項目。 它無法變更任何靜態暫存器，包括 RSP，這表示它無法呼叫任何函數或配置堆疊空間。 它允許它執行時保留堆疊是未對齊。

## <a name="see-also"></a>另請參閱

[堆疊使用方式](../build/stack-usage.md)
