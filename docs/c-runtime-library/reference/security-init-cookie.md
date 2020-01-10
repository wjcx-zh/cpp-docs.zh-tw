---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948723"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

初始化全域安全性 Cookie。

## <a name="syntax"></a>語法

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>備註

全域安全性 Cookie 用於在以 [/GS (緩衝區安全性檢查)](../../build/reference/gs-buffer-security-check.md) 編譯的程式碼以及在使用例外狀況處理的程式碼中，提供緩衝區滿溢保護。 在進入滿溢保護的函式時，此 Cookie 會放在堆疊上，然後結束時，在堆疊上的值會與全域 Cookie 進行比較。 它們之間的任何差異表示已發生緩衝區滿溢，並導致程式立即終止。

通常， **__security_init_cookie**會在初始化時由 CRT 呼叫。 如果您略過 CRT 初始化（例如，如果您使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)指定進入點），則必須自行呼叫 **__security_init_cookie** 。 如果未呼叫 **__security_init_cookie** ，全域安全性 cookie 會設定為預設值，而緩衝區溢位保護會遭到入侵。 由於攻擊者可以利用此預設 cookie 值來破壞緩衝區溢位檢查，因此建議您在定義自己的進入點時，一律呼叫 **__security_init_cookie** 。

**__Security_init_cookie**的呼叫必須在輸入任何溢位保護的函式之前進行;否則，將會偵測到假的緩衝區溢位。 如需詳細資訊，請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。

## <a name="example"></a>範例

請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的範例。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie**是標準 C 執行時間程式庫的 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[Microsoft 安全性回應中心](https://www.microsoft.com/msrc?rtc=1)
