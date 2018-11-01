---
title: set_terminate (CRT)
ms.date: 11/04/2016
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
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 7be81dec7fba80a273d635cbd30b96b09928bc66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493908"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

安裝要呼叫的專屬終止常式**終止**。

## <a name="syntax"></a>語法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>參數

*termFunction*<br/>
所撰寫之終止函式的指標。

## <a name="return-value"></a>傳回值

所註冊之先前函式傳回的指標**set_terminate**以便稍後可以還原先前函式。 如果尚未設定先前函式，傳回的值可能用於還原預設行為。此值可能**NULL**。

## <a name="remarks"></a>備註

**Set_terminate**函式會安裝*termFunction*所呼叫的函式**終止**。 **set_terminate**搭配 c + + 例外狀況處理和擲回例外狀況之前可能在您的程式中的任何時間點呼叫。 **終止**呼叫[中止](abort.md)預設。 您可以變更此預設值，方法是撰寫您自己的終止函式，並呼叫**set_terminate**您作為其引數的函式的名稱。 **終止**呼叫最後一個指定為引數的函式**set_terminate**。 執行任何所需的清除工作之後*termFunction*應該會結束程式。 如果它不會結束 （如果它傳回至呼叫端），[中止](abort.md)呼叫。

在多執行緒環境中，會分別維護每個執行緒的終止函式。 每個新執行緒都需要安裝它自己的終止函式。 因此，每個執行緒都會負責它自己的終止處理。

**Terminate_function** EH 中定義型別。為使用者定義終止函式的指標 H *termFunction*會傳回**void**。 您的自訂函式*termFunction*可以接受任何引數，而且不應該傳回至其呼叫端。 若是如此，請[中止](abort.md)呼叫。 例外狀況不會擲回內在*termFunction*。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**函式僅適用於偵錯工具之外。

沒有單一**set_terminate**處理常式的所有動態連結的 Dll 或 Exe; 即使您呼叫**set_terminate**可能由另一個，取代您的處理常式，或您可能會取代另一個設定的處理常式DLL 或 EXE。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
