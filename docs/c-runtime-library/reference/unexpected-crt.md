---
title: unexpected (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- unexpected
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
- unexpected
dev_langs:
- C++
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd8dc51c41ebf938f59493cbd62fac3e0a491601
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408103"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

呼叫**終止**或使用指定的函式**set_unexpected**。

## <a name="syntax"></a>語法

```C
void unexpected( void );
```

## <a name="remarks"></a>備註

**意外**不適用於目前的實作的 c + + 例外狀況處理常式。 **未預期**呼叫**終止**預設。 您可以變更此預設行為，透過撰寫自訂終止函式和呼叫**set_unexpected**您為其引數的函式的名稱。 **未預期**做為引數所指定的最後一個函式會呼叫**set_unexpected**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
