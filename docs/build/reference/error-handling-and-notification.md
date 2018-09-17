---
title: 錯誤處理和告知 |Microsoft Docs
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
ms.openlocfilehash: 17df0dfd57bf24c7cd442c296409530e521b28de
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723199"
---
# <a name="error-handling-and-notification"></a>錯誤處理和告知

如需有關錯誤處理和通知的詳細資訊，請參閱 <<c0> [ 了解 Helper 函式](understanding-the-helper-function.md)。

如需有關攔截函式的詳細資訊，請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。

如果您的程式使用延遲載入 Dll，它必須處理錯誤，強行因為程式執行過程中發生的失敗會導致未處理例外狀況。 處理失敗是由兩個部分組成：

透過攔截程序的復原。
如果您的程式碼需要復原或提供替代的程式庫和/或常式失敗，攔截程序可以提供 helper 函式，可提供或補救這種情況。 攔截的例行工作必須傳回適當的值，以便處理可以繼續 （HINSTANCE 或 FARPROC） 或 0 表示應該擲回例外狀況。 它可能也會擲回它自己的例外狀況或**longjmp**超出勾點。 有通知攔截和錯誤攔截。

透過例外狀況的報告。
如果所有所需的處理錯誤中止程序，就不需要攔截，只要使用者程式碼可以處理例外狀況。

下列主題討論的錯誤處理和通知：

- [通知攔截](../../build/reference/notification-hooks.md)

- [失敗攔截](../../build/reference/failure-hooks.md)

- [例外狀況](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)