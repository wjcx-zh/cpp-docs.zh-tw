---
title: 例外狀況 (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: cf38af464f08e143ed9073befe30f6aeb8b913b6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915469"
---
# <a name="exceptions-cc"></a>例外狀況 (C/C++)

當發生失敗時, 可能會引發兩個例外狀況代碼:

- **LoadLibrary**失敗

- 若為**GetProcAddress**失敗

以下是例外狀況資訊:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

擲回的例外狀況代碼是標準的 VcppException (ERROR_SEVERITY_ERROR、ERROR_MOD_NOT_FOUND) 和 VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND) 值。 例外狀況會將指標傳遞至 LPDWORD 值中的**DelayLoadInfo**結構, 而**GetExceptionInformation**會在[EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record)結構的 ExceptionInformation [0] 欄位中加以抓取。

此外, 如果在 grAttrs 欄位中設定了不正確的位, 就會擲回例外狀況 ERROR_INVALID_PARAMETER。 這個例外狀況適用于所有意圖和用途, 嚴重。

如需詳細資訊, 請參閱[結構和常數定義](structure-and-constant-definitions.md)。

## <a name="see-also"></a>另請參閱

[錯誤處理和通知](error-handling-and-notification.md)
