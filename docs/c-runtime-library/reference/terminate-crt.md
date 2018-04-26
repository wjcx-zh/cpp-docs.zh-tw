---
title: terminate (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- terminate
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
- terminate
dev_langs:
- C++
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 302bb0096bd6b4d0b9e92c3508704f35f2c355c8
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="terminate-crt"></a>terminate (CRT)

呼叫[中止](abort.md)或您的函式指定使用**set_terminate**。

## <a name="syntax"></a>語法

```C
void terminate( void );
```

## <a name="remarks"></a>備註

**終止**函式會搭配 c + + 例外狀況處理，並在下列情況中，稱為：

- 擲回的 C++ 例外狀況找不到相符的 catch 處理常式。

- 解構函式在堆疊回溯期間擲回例外狀況。

- 堆疊在擲回例外狀況之後損毀。

**終止**呼叫[中止](abort.md)預設。 您可以透過撰寫自己的中止函式和呼叫來變更此預設**set_terminate**您為其引數的函式的名稱。 **終止**做為引數所指定的最後一個函式會呼叫**set_terminate**。 如需詳細資訊，請參閱[未處理的 C++ 例外狀況](../../cpp/unhandled-cpp-exceptions.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**terminate**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
