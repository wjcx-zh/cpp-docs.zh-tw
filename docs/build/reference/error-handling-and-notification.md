---
title: 錯誤處理和告知 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2edec23da89766a45545566b0a689001d3ca75f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="error-handling-and-notification"></a>錯誤處理和告知
如需有關錯誤處理和通知的詳細資訊，請參閱[了解 Helper 函式](understanding-the-helper-function.md)。  
  
 如需有關攔截函式的詳細資訊，請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。  
  
 如果您的程式使用的延遲載入 Dll 時，它必須處理錯誤穩當地因為在程式執行時所發生的失敗會導致未處理例外狀況。 錯誤處理是由兩個部分組成：  
  
 透過勾點復原。  
 如果您的程式碼需要復原，或提供替代的程式庫和/或常式失敗，則攔截程序可以提供 helper 函式，可提供或補救這種情況。 傳回適當的值，以處理攔截常式需求可以繼續 （HINSTANCE 或 FARPROC） 或 0，表示應該擲回例外狀況。 它可能也會擲回它自己的例外狀況或**longjmp**超出勾點。 沒有通知攔截和錯誤攔截。  
  
 透過例外狀況的報告。  
 如果所需的處理錯誤中止程序，就不需要攔截，只要使用者程式碼可以處理此例外狀況。  
  
 錯誤處理和告知將討論下列主題：  
  
-   [通知攔截](../../build/reference/notification-hooks.md)  
  
-   [失敗攔截](../../build/reference/failure-hooks.md)  
  
-   [例外狀況](../../build/reference/exceptions-c-cpp.md)  
  
## <a name="see-also"></a>另請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)