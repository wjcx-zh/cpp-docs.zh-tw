---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332095"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

安裝您自己的終止例程式,由**終止**呼叫 。

## <a name="syntax"></a>語法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>參數

*字語函數*<br/>
所撰寫之終止函式的指標。

## <a name="return-value"></a>傳回值

返回指向**set_terminate**註冊的前一個函數的指標,以便以後可以還原以前的函數。 如果未設置以前的函數,則返回值可用於還原默認行為;如果未設置以前的函數,則返回值可用於還原默認行為。這個值可以是**NULL**。

## <a name="remarks"></a>備註

**set_terminate**函數將*術語函數*作為**終止**呼叫的函數。 **set_terminate**用於C++異常處理,並且可能在引發異常之前在程式中的任意點調用。 預設情況下**取消**呼叫[中止](abort.md)。 您可以通過編寫自己的終止函數並將函數**的名稱稱為參數**set_terminate來更改此預設值。 **終止**呼叫作為參數給出的最後一個函數**set_terminate**。 執行任何所需的清理任務後,*術語函數*應退出程式。 如果它不退出(如果它傳回到其呼叫者),則呼叫[中止](abort.md)。

在多執行緒環境中，會分別維護每個執行緒的終止函式。 每個新執行緒都需要安裝它自己的終止函式。 因此，每個執行緒都會負責它自己的終止處理。

**terminate_function**類型在 EH 中定義。H 作為指向使用者定義的終止函數的指標,*術語函數*傳回**void**。 自定義函數*術語"函數*"不能採用任何參數,並且不應返回到其調用方。 如果是,則呼叫[中止](abort.md)。 不能從*術語函數*中引發異常。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **set_terminate**函數僅在調試器外部工作。

對於所有動態連結的 DLL 或 EXEs,都有一個**set_terminate**處理程式;即使您調用**set_terminate**您的處理程式可能被另一個替換,或者您可能正在取代由另一個 DLL 或 EXE 設置的處理程式。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
[終止](terminate-crt.md)<br/>
[意外](unexpected-crt.md)<br/>
