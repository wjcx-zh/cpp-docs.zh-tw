---
title: 錯誤攔截 |Microsoft 文件
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
ms.openlocfilehash: be598a77ca48eeee03360a3b598b0567abc6ee4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="failure-hooks"></a>錯誤攔截
錯誤攔截已啟用以相同方式[告知攔截](../../build/reference/notification-hooks.md)。 傳回適當的值，以處理攔截常式需求可以繼續 （HINSTANCE 或 FARPROC） 或 0，表示應該擲回例外狀況。  
  
 指的是使用者定義函式的指標變數是：  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo**結構包含的所有相關資料所需的精確報告的錯誤，包括從值`GetLastError`。  
  
 如果通知，則**dliFailLoadLib**，攔截函式可以傳回：  
  
-   0，如果它無法處理失敗。  
  
-   HMODULE，如果失敗攔截修正問題，並載入程式庫本身。  
  
 如果通知，則**dliFailGetProc**，攔截函式可以傳回：  
  
-   0，如果它無法處理失敗。  
  
-   有效的處理序位址 （匯入函式位址），如果錯誤攔截已成功取得位址。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理和通知](../../build/reference/error-handling-and-notification.md)