---
title: set_unexpected (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- set_unexpected
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
- set_unexpected
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7af5cce0b17747beb8c136f75489025d741f864a
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

安裝要由 **unexpected** 呼叫的專屬中止函式。

## <a name="syntax"></a>語法

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>參數

*unexpFunction*<br/>
若要取代您撰寫的函式指標**意外**函式。

## <a name="return-value"></a>傳回值

傳回指向先前的中止函式的註冊 **_set_unexpected**以便日後還原先前的函數。 如果尚未設定任何先前的函數，傳回的值可能用來還原預設行為。這個值可能是**NULL**。

## <a name="remarks"></a>備註

**Set_unexpected**函式會安裝*unexpFunction*呼叫的函式為**意外**。 **未預期**不是在目前的 c + + 例外狀況處理實作。 **Unexpected_function** EH 中定義類型。為使用者定義的非預期函式，指標 H *unexpFunction*傳回**void**。 您的自訂*unexpFunction*函式不應傳回其呼叫端。

```cpp
typedef void ( *unexpected_function )( );
```

根據預設，**意外**呼叫**終止**。 您可以變更此預設行為，透過撰寫自己的中止函式和呼叫**set_unexpected**您為其引數的函式的名稱。 **未預期**做為引數所指定的最後一個函式會呼叫**set_unexpected**。

不同於自訂終止函式的呼叫所安裝**set_terminate**，可以擲回例外狀況，從*unexpFunction*。

在多執行緒環境中，會分別維護每個執行緒的未預期函式。 每個新執行緒都需要安裝它自己的未預期函式。 因此，每個執行緒都會負責它自己的未預期處理。

在目前的 Microsoft 實作的 c + + 例外狀況處理，**意外**呼叫**終止**依預設，絕不會呼叫例外狀況處理執行階段程式庫。 沒有任何特定的優勢，於呼叫**意外**而**終止**。

沒有單一**set_unexpected**處理常式所有以動態方式連結的 Dll 或 Exe，即使您呼叫**set_unexpected**可能由另一個取代您的處理常式，或您要取代所設定的處理常式另一個 DLL 或 EXE。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
