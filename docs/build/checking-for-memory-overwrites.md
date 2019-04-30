---
title: 檢查記憶體覆寫
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342246"
---
# <a name="checking-for-memory-overwrites"></a>檢查記憶體覆寫

如果您收到存取違規堆積操作函式的呼叫上時，很可能您的程式已損毀堆積。 這種情況的一般症狀會是：

```
Access Violation in _searchseg
```

[_Heapchk](../c-runtime-library/reference/heapchk.md)函式是適用於這兩個偵錯和發行組建 (Windows NT) 來驗證執行的階段程式庫堆積的完整性。 您可以使用`_heapchk`在相同的方式為`AfxCheckMemory`函式來找出堆積覆寫時，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函式發生問題時，您需要隔離此時堆積已損毀。

## <a name="see-also"></a>另請參閱

[解決發行組建的問題](fixing-release-build-problems.md)
