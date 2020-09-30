---
title: 參數驗證
description: Microsoft C 執行時間程式庫中的參數驗證描述。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 60ded7fc5a4388b2c4bf87ab5a388caab5fc47c2
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589818"
---
# <a name="parameter-validation"></a>參數驗證

大部分增強安全性的 CRT 函式以及許多這些函式都不會驗證其參數，例如檢查指標是否為 **Null**、整數屬於有效範圍，或列舉值有效。 如果找到不正確參數，則會呼叫不正確參數處理常式。

## <a name="invalid-parameter-handler-routine"></a>無效的參數處理常式

當 C 執行時間程式庫函式偵測到不正確參數時，它會捕獲有關錯誤的部分資訊，然後呼叫包裝無效參數處理常式分派函式的宏。 這會是 [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md)、 [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)或 [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md)之一。 呼叫哪個分派函式取決於您的程式碼分別是偵錯工具組建、零售組建，還是不會將錯誤視為可復原。

在 debug 組建中，不正確參數宏通常會在呼叫分派函式之前，引發失敗的判斷提示和偵錯工具中斷點。 當執行程式碼時，判斷提示可能會根據作業系統和執行時間程式庫版本，在具有「中止」、「重試」和「繼續」或類似選項的對話方塊中回報給使用者。 這些選項可讓使用者立即終止程式、附加偵錯工具，或讓現有的程式碼繼續執行，以呼叫分派函數。

不正確參數處理常式分派函數會呼叫目前指派的無效參數處理常式。 根據預設，不正確參數 `_invoke_watson` 會呼叫，這會導致應用程式關閉並產生迷你傾印。 如果作業系統啟用，對話方塊會詢問使用者是否要將損毀傾印傳送給 Microsoft 進行分析。

您可以使用 [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 或 [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 函數將不正確參數處理常式設定為您自己的函式，來變更此行為。 如果您指定的函式不終止應用程式，控制權就會回到接收了無效參數的函式。 在 CRT 中，這些函數通常會停止函式執行、設定 `errno` 為錯誤碼，並傳回錯誤碼。 在許多情況下， `errno` 值和傳回值都是 `EINVAL` ，用來表示不正確參數。 在某些情況下，會傳回更具體的錯誤碼，例如不正確檔案指標的 `EBADF` 傳入為參數。 

如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="see-also"></a>另請參閱

[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)\
[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
