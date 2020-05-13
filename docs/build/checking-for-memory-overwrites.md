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

如果您對堆積操作函式的呼叫收到存取違規，可能是您的程式已損毀堆積。 這種情況的常見徵兆會是：

```
Access Violation in _searchseg
```

在 debug 和 release 組建（僅限 Windows NT）中都有提供[_heapchk](../c-runtime-library/reference/heapchk.md)函式，以驗證執行時間程式庫堆積的完整性。 您可以使用`_heapchk`與函式大致相同的方式`AfxCheckMemory`來隔離堆積覆寫，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函式失敗，您需要找出堆積損毀的時間點。

## <a name="see-also"></a>請參閱

[解決發行組建的問題](fixing-release-build-problems.md)
