---
title: __security_init_cookie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 699a75da7829feb39142a777a34a14fcd85be653
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821117"
---
# <a name="securityinitcookie"></a>__security_init_cookie

初始化全域安全性 Cookie。

## <a name="syntax"></a>語法

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>備註

全域安全性 Cookie 用於在以 [/GS (緩衝區安全性檢查)](../../build/reference/gs-buffer-security-check.md) 編譯的程式碼以及在使用例外狀況處理的程式碼中，提供緩衝區滿溢保護。 在進入滿溢保護的函式時，此 Cookie 會放在堆疊上，然後結束時，在堆疊上的值會與全域 Cookie 進行比較。 它們之間的任何差異表示已發生緩衝區滿溢，並導致程式立即終止。

通常 **__security_init_cookie**初始化時，會將由 CRT 呼叫。 如果您略過 CRT 初始化 — 比方說，如果您使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)以指定進入點，您必須呼叫 **__security_init_cookie**自己。 如果 **__security_init_cookie**不呼叫時，將全域安全性 cookie 設定為預設值，而且緩衝區滿溢保護會遭到入侵。 因為攻擊者可以利用此預設 cookie 值擊敗緩衝區滿溢檢查，我們建議您一律呼叫 **__security_init_cookie**當您定義您自己的進入點。

在呼叫 **__security_init_cookie**必須設定為任何滿溢保護之前先輸入函式; 否則將會偵測到假性的緩衝區滿溢。 如需詳細資訊，請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。

## <a name="example"></a>範例

請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的範例。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie**是標準的 C 執行階段程式庫的 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[Microsoft 安全性回應中心](https://www.microsoft.com/msrc?rtc=1)
