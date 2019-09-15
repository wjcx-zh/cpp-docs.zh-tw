---
title: set_terminate (CRT)
ms.date: 11/04/2016
api_name:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 860789a3f2fda5ef13cadffa2a00dba4fbd2090a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948359"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

安裝要由**terminate**呼叫的專屬終止常式。

## <a name="syntax"></a>語法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>參數

*termFunction*<br/>
所撰寫之終止函式的指標。

## <a name="return-value"></a>傳回值

傳回**set_terminate**所註冊之先前函式的指標，以便之後可以還原先前的函式。 如果尚未設定先前的函式，則會使用傳回值來還原預設行為。這個值可以是**Null**。

## <a name="remarks"></a>備註

**Set_terminate**函數會將*termFunction*安裝為**終止**所呼叫的函式。 **set_terminate**會與C++例外狀況處理搭配使用，而且可以在擲回例外狀況之前，在程式中的任何時間點呼叫。 依預設，**終止**呼叫會[中止](abort.md)。 您可以變更此預設值，方法是撰寫自己的終止函式，並使用您的函式名稱做為其引數來呼叫**set_terminate** 。 **terminate**會呼叫指定為**set_terminate**引數的最後一個函式。 執行任何所需的清除工作之後， *termFunction*應該會結束程式。 如果未結束（如果它傳回至其呼叫端），則會呼叫[abort](abort.md) 。

在多執行緒環境中，會分別維護每個執行緒的終止函式。 每個新執行緒都需要安裝它自己的終止函式。 因此，每個執行緒都會負責它自己的終止處理。

**Terminate_function**類型是在 EH 中定義。H 做為使用者定義終止函式的指標，此*termFunction*會傳回**void**。 您的自訂函式*termFunction*不會接受任何引數，而且不應該傳回至其呼叫端。 如果存在，則會呼叫[abort](abort.md) 。 可能不會從*termFunction*中擲回例外狀況。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**函式僅適用于偵錯工具以外。

所有動態連結的 Dll 或 Exe 都有單一的**set_terminate**處理常式;即使您呼叫**set_terminate** ，您的處理常式可能會被另一個取代，或者您可能會取代另一個 DLL 或 EXE 所設定的處理常式。

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
