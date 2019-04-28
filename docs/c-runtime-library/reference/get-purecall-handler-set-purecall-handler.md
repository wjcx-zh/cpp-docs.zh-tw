---
title: _get_purecall_handler、_set_purecall_handler
ms.date: 11/04/2016
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 0009b4bc1c7bf70bd84b9a82ecdc8643789e8164
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287396"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler、_set_purecall_handler

取得或設定純虛擬函式呼叫的錯誤處理常式。

## <a name="syntax"></a>語法

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>參數

*function*<br/>
呼叫純虛擬函式時要呼叫的函式。 A **_purecall_handler**函式必須有 void 的傳回型別。

## <a name="return-value"></a>傳回值

先前 **_purecall_handler**。 傳回**nullptr**如果有任何先前的處理常式。

## <a name="remarks"></a>備註

**_Get_purecall_handler**並 **_set_purecall_handler**函式是 Microsoft 專有和僅適用於C++的程式碼。

呼叫純虛擬函式會產生錯誤，因為它有沒有實作。 根據預設，呼叫純虛擬函式時，編譯器會產生程式碼來叫用錯誤處理常式函式，該函式會終止程式。 您可以為純虛擬函式呼叫安裝您自己的錯誤處理函式，以攔截它們，用於偵錯或報告目的。 若要使用您自己的錯誤處理常式，建立具有的函式 **_purecall_handler**簽章，然後使用 **_set_purecall_handler**使它成為目前的處理常式。

因為只有一個 **_purecall_handler**每個處理序，當您呼叫 **_set_purecall_handler**它立即影響所有執行緒。 任何執行緒的上一個呼叫端會設定處理常式。

若要還原預設行為，請呼叫 **_set_purecall_handler**利用**nullptr**引數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler**|\<cstdlib> 或 \<stdlib.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
