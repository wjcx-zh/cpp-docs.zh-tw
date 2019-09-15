---
title: _CrtSetReportHook2、_CrtSetReportHookW2
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook2
- _CrtSetReportHookW2
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
- CrtSetReportHookW2
- CrtSetReportHook2
- _CrtSetReportHookW2
- _CrtSetReportHook2
helpviewer_keywords:
- CrtSetReportHook2 function
- _CrtSetReportHook2 function
- _CrtSetReportHookW2 function
- CrtSetReportHookW2 function
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
ms.openlocfilehash: 37ec0cea3fb558a5926e6f9c707e0e5033a17222
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942224"
---
# <a name="_crtsetreporthook2-_crtsetreporthookw2"></a>_CrtSetReportHook2、_CrtSetReportHookW2

將用戶端定義的報告函式連結到 C 執行階段偵錯報告處理序，以進行安裝或解除安裝 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtSetReportHook2(
   int mode,
   _CRT_REPORT_HOOK pfnNewHook
);
int _CrtSetReportHookW2(
   int mode,
   _CRT_REPORT_HOOKW pfnNewHook
);
```

### <a name="parameters"></a>參數

*mode*<br/>
要採取的動作： **_CRT_RPTHOOK_INSTALL**或 **_CRT_RPTHOOK_REMOVE**。

*pfnNewHook*<br/>
要在此函式的窄字元或寬字元版本中安裝或移除的報表攔截。

## <a name="return-value"></a>傳回值

如果發生錯誤，則為-1，使用**EINVAL**或**ENOMEM**設定;否則，會在呼叫之後傳回*pfnNewHook*的參考計數。

## <a name="remarks"></a>備註

**_CrtSetReportHook2**和 **_CrtSetReportHookW2**可讓您對函式進行攔截或解除連結，而[_CrtSetReportHook](crtsetreporthook.md)僅可讓您攔截函式。

當攔截呼叫是在 DLL 中進行，而且可能載入多個 Dll，並設定自己的攔截函式時，應該使用 **_CrtSetReportHook2**或 **_CrtSetReportHookW2**而不是 **_CrtSetReportHook** 。 在此情況下，可依載入 DLL 時的不同順序來卸載 DLL，並可保留攔截函式以指向未卸載的 DLL。 如果已使用 **_CrtSetReportHook**新增攔截函式，任何偵錯工具輸出都會損毀進程。

如果沒有以 **_CrtSetReportHook2**或 **_CrtSetReportHookW2**新增的攔截函式，或所有使用 **_CrtSetReportHook2**和 _ 新增的攔截函式，則會呼叫以 **_CrtSetReportHook**新增的任何攔截函式**CrtSetReportHookW2**傳回**FALSE**。

此函式有寬字元版本可用。 報表攔截函式採用的字串類型 (寬或窄字元) 必須符合此函式所使用的版本。 針對此函式的寬字元版本搭配使用的報表攔截程序，使用下列函式原型：

```C
int YourReportHook( int reportType, wchar_t *message, int *returnValue );
```

針對窄字元報表攔截程序，使用下列原型：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

這些函式會驗證它們的參數。 如果*mode*或**pfnNewNook**無效，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回-1。

> [!NOTE]
> 如果您的應用程式是使用 **/clr**編譯的，而且在應用程式結束 main 之後呼叫報告函式，則 clr 會在報告函數呼叫任何 CRT 函數時擲回例外狀況（exception）。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtSetReportHook2**|\<crtdbg.h>|\<errno.h>|
|**_CrtSetReportHookW2**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_setreporthook2.c
#include <windows.h>
#include <stdio.h>
#include <crtdbg.h>
#include <assert.h>

int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)
{
   int nRet = FALSE;

   printf("CRT report hook 1.\n");
   printf("CRT report type is \"");
   switch (nReportType)
   {
      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         // nRet = TRUE;   // Always stop for this type of report
         break;
      }

      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is:\n\t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;

   return   nRet;
}

int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)
{
   int   nRet = FALSE;

   printf("CRT report hook 2.\n");
   printf("CRT report type is \"");
   switch   (nReportType)
   {
      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         nRet = TRUE;   // Always stop for this type of report
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is: \t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;
   // printf("CRT report code is %d.\n", *pnRet);
   return   nRet;
}

int   main(int argc, char* argv[])
{
   int   nRet = 0;

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);

   _ASSERT(0);

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);

   return   nRet;
}
```

### <a name="output"></a>Output

```Output
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
```

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
