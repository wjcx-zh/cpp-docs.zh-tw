---
title: set_terminate (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 017ea9d96cef9065ff82e7f3428e725b816c9319
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

會安裝由呼叫終止常式**終止**。

## <a name="syntax"></a>語法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>參數

*termFunction*<br/>
所撰寫之終止函式的指標。

## <a name="return-value"></a>傳回值

傳回先前註冊的函式的指標**set_terminate**以便日後還原先前的函數。 如果尚未設定先前函式，傳回值可能用於還原預設行為；這個值可以是 NULL。

## <a name="remarks"></a>備註

**Set_terminate**函式會安裝*termFunction*呼叫的函式為**終止**。 **set_terminate**會與 c + + 例外狀況處理和擲回例外狀況之前無法呼叫在程式中的任何時間點。 **終止**呼叫[中止](abort.md)預設。 您可以透過撰寫自己的中止函式和呼叫來變更此預設**set_terminate**您為其引數的函式的名稱。 **終止**做為引數所指定的最後一個函式會呼叫**set_terminate**。 執行任何所需的清除工作之後, *termFunction*應該結束程式。 如果它未結束 （如果它傳回至呼叫端），[中止](abort.md)呼叫。

在多執行緒環境中，會分別維護每個執行緒的終止函式。 每個新執行緒都需要安裝它自己的終止函式。 因此，每個執行緒都會負責它自己的終止處理。

**Terminate_function** EH 中定義類型。為使用者定義的終止函式的指標 H *termFunction*傳回**void**。 您的自訂函式*termFunction*可以接受任何引數，不應傳回其呼叫端。 若是如此，[中止](abort.md)呼叫。 例外狀況不會擲回從*termFunction*。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**函式僅適用於偵錯工具外部。

沒有單一**set_terminate**處理常式所有以動態方式連結的 Dll 或 Exe，即使您呼叫**set_terminate**您的處理常式可能會取代另一個，或您可能會取代另一個設定的處理常式DLL 或 EXE。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [terminate](terminate-crt.md) 的範例。

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
