---
title: 失敗攔截 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c69759034dbb7233970bd89616a062a369cc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721275"
---
# <a name="failure-hooks"></a>錯誤攔截

失敗攔截程序已啟用以相同的方式[通知攔截](../../build/reference/notification-hooks.md)。 攔截的例行工作必須傳回適當的值，以便處理可以繼續 （HINSTANCE 或 FARPROC） 或 0 表示應該擲回例外狀況。

指標變數會參考使用者定義函式是：

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo**結構包含的所有相關資料所需的準確報告錯誤，包括從值`GetLastError`。

如果通知已**dliFailLoadLib**，攔截函式可以傳回：

- 0，如果它無法處理失敗。

- HMODULE，如果失敗攔截修正問題，並載入程式庫本身。

如果通知已**dliFailGetProc**，攔截函式可以傳回：

- 0，如果它無法處理失敗。

- 有效的處理序位址 （匯入函式位址），如果錯誤攔截成功取得本身的位址。

## <a name="see-also"></a>另請參閱

[錯誤處理和通知](../../build/reference/error-handling-and-notification.md)