---
title: 檢查記憶體覆寫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718638"
---
# <a name="checking-for-memory-overwrites"></a>檢查記憶體覆寫

如果您收到存取違規堆積操作函式的呼叫上時，很可能您的程式已損毀堆積。 這種情況的一般症狀會是：

```
Access Violation in _searchseg
```

[_Heapchk](../../c-runtime-library/reference/heapchk.md)函式是適用於這兩個偵錯和發行組建 (Windows NT) 來驗證執行的階段程式庫堆積的完整性。 您可以使用`_heapchk`在相同的方式為`AfxCheckMemory`函式來找出堆積覆寫時，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函式發生問題時，您需要隔離此時堆積已損毀。

## <a name="see-also"></a>另請參閱

[解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)