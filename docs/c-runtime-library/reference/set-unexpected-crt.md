---
title: set_unexpected (CRT)
ms.date: 11/04/2016
api_name:
- set_unexpected
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
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: f05eab14a53c8abc119a8014d5ac99dc076a9c25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226160"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

安裝要由 **unexpected** 呼叫的專屬中止函式。

## <a name="syntax"></a>語法

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>參數

*unexpFunction*<br/>
您所撰寫的函式指標，用來取代非**預期**的函式。

## <a name="return-value"></a>傳回值

傳回 **_set_unexpected**所註冊之先前終止函式的指標，以便之後可以還原先前的函式。 如果尚未設定先前的函式，則會使用傳回值來還原預設行為。這個值可以是**Null**。

## <a name="remarks"></a>備註

**Set_unexpected**函式會將*unexpFunction*安裝為非**預期**所呼叫的函式。 非**預期**的無法在目前的 c + + 例外狀況處理執行中使用。 **Unexpected_function**類型是在 EH 中定義。H 做為使用者定義非預期函式的指標， *unexpFunction*會傳回 unexpFunction **`void`** 。 您的自訂*unexpFunction*函式不應回到其呼叫端。

```cpp
typedef void ( *unexpected_function )( );
```

根據預設，非**預期**的呼叫會**終止**。 您可以藉由撰寫自己的終止函式，並使用您的函式名稱做為其引數呼叫**set_unexpected** ，來變更此預設行為。 非**預期**的會呼叫當做引數提供給**set_unexpected**的最後一個函數。

不同于**set_terminate**的呼叫所安裝的自訂終止函式，例外狀況可以從*unexpFunction*中擲回。

在多執行緒環境中，會分別維護每個執行緒的未預期函式。 每個新執行緒都需要安裝它自己的未預期函式。 因此，每個執行緒都會負責它自己的未預期處理。

在目前 Microsoft c + + 例外狀況處理的執行中，非**預期**的呼叫預設會**終止**，而且不會由例外狀況處理執行時間程式庫呼叫。 呼叫非**預期**的，而不是**終止**的特殊優點。

所有動態連結的 Dll 或 Exe 都有一個**set_unexpected**處理常式;即使您呼叫**set_unexpected**您的處理常式可能會被另一個取代，或者您要取代另一個 DLL 或 EXE 所設定的處理常式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[終止](terminate-crt.md)<br/>
[意料](unexpected-crt.md)<br/>
