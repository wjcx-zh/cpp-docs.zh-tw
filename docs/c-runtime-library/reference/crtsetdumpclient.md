---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: fd2b037ce10f708ab133f31a20636438b0d04b93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234259"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

安裝應用程式定義的函式，以傾印 **_CLIENT_BLOCK**類型的記憶體區塊（僅限 debug 版本）。

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

**_CrtSetDumpClient**函式可讓應用程式連結自己的函式，將儲存在 **_CLIENT_BLOCK**記憶體區塊中的物件傾印到 C 執行時間的 debug 記憶體傾印程式中。 如此一來，每次[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)或[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)的 debug 傾印函式傾印 **_CLIENT_BLOCK**記憶體區塊時，也會呼叫應用程式的傾印函式。 **_CrtSetDumpClient**提供應用程式一個簡單的方法來偵測記憶體流失，以及驗證或報告儲存在 **_CLIENT_BLOCK**區塊中的資料內容。 未定義[_DEBUG](../../c-runtime-library/debug.md)時，會在前置處理期間移除 **_CrtSetDumpClient**的呼叫。

**_CrtSetDumpClient**函數會安裝*dumpClient*中指定的新應用程式定義傾印函式，並傳回先前定義的傾印函數。 用戶端區塊傾印函式的範例如下所示：

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion*引數是記憶體區塊之使用者資料部分開頭的指標，而*區塊*會指定配置的記憶體區塊大小（以位元組為單位）。 用戶端區塊傾印函式必須傳回 **`void`** 。 傳遞至 **_CrtSetDumpClient**之用戶端傾印函式的指標是 **_CRT_DUMP_CLIENT**的類型，如 crtdbg.h 裡中所定義：

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

如需在 **_CLIENT_BLOCK**類型記憶體區塊上操作之函數的詳細資訊，請參閱[用戶端區塊攔截](/visualstudio/debugger/client-block-hook-functions)函式。 [_CrtReportBlockType](crtreportblocktype.md) 函式可用來傳回區塊類型和子類型的相關資訊。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[Debug 常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
