---
title: _CrtSetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342987"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

安裝的應用程式定義的函式傾印 **_CLIENT_BLOCK**類型記憶體區塊 （僅限偵錯版本）。

## <a name="syntax"></a>語法

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>參數

*dumpClient*<br/>
要連結到 C 執行階段偵錯記憶體傾印處理序之新的用戶端定義記憶體傾印函式。

## <a name="return-value"></a>傳回值

傳回先前定義的用戶端區塊傾印函式。

## <a name="remarks"></a>備註

**_CrtSetDumpClient**函式可讓應用程式將自己的函式，來傾印物件儲存在連結 **_CLIENT_BLOCK**到 C 執行階段的記憶體區塊偵錯記憶體傾印處理序。 如此一來，每當偵錯傾印函式這類[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)或是[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)傾印 **_CLIENT_BLOCK**記憶體區塊，應用程式傾印函式也會呼叫。 **_CrtSetDumpClient**提供一個簡單的方法中的應用程式，偵測記憶體流失和驗證或報告中所儲存資料的內容 **_CLIENT_BLOCK**區塊。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtSetDumpClient**會在前置處理期間移除。

**_CrtSetDumpClient**函式會安裝新的應用程式定義傾印函式中指定*dumpClient*並傳回先前定義的傾印函式。 用戶端區塊傾印函式的範例如下所示：

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion*引數是記憶體區塊的使用者資料部分開頭的指標並*blockSize*指定配置的記憶體大小區塊以位元組為單位。 用戶端區塊傾印函式必須傳回**void**。 要傳遞至用戶端傾印函式的指標 **_CrtSetDumpClient**別的 **_CRT_DUMP_CLIENT**，定義在 crtdbg.h 裡：

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

如需有關運作的函式 **_CLIENT_BLOCK**類型記憶體區塊，請參閱[用戶端區塊攔截函式](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](crtreportblocktype.md) 函式可用來傳回區塊類型和子類型的相關資訊。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
