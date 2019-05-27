---
title: _open_osfhandle
ms.date: 05/21/2019
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 8527dade37f20b7341d5a26f5752ece668ab7fc9
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174797"
---
# <a name="openosfhandle"></a>_open_osfhandle

將 C 執行階段檔案描述項與現有的作業系統檔案控制代碼建立關聯。

## <a name="syntax"></a>語法

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>參數

*osfhandle*<br/>
作業系統檔案控制代碼。

*flags*<br/>
允許的作業類型。

## <a name="return-value"></a>傳回值

若成功，**_open_osfhandle** 會傳回 C 執行階段檔案描述項。 否則，它會傳回 -1。

## <a name="remarks"></a>備註

**_open_osfhandle** 函式會配置 C 執行階段檔案描述項，並將它與 *osfhandle* 指定的作業系統檔案控制代碼建立關聯。 若要避免編譯器警告，請將 *osfhandle* 引數從 **HANDLE** 轉換成 **intptr_t**。 *flag* 引數是整數運算式，由一或多個定義於 \<fcntl.h> 中的資訊清單常數所組成。 當使用兩個以上的資訊清單常數構成 *flags* 引數時，會使用位元 OR 運算子 (**&#124;**) 結合常數。

\<fcntl.h> 中定義了這些資訊清單常數：

|||
|-|-|
| **\_O\_APPEND** | 在每次寫入作業之前，將檔案指標置放到檔案的結尾。 |
| **\_O\_RDONLY** | 開啟檔案為僅供讀取。 |
| **\_O\_TEXT** | 以文字 (已轉譯) 模式開啟檔案。 |
| **\_O\_WTEXT** | 以 Unicode (已轉譯 UTF-16) 模式開啟檔案。 |

**_open_osfhandle** 呼叫會將 Win32 檔案控制代碼的擁有權轉送給檔案描述項。 或要使用 **_open_osfhandle** 關閉開啟的檔案，請呼叫 [\_close](close.md)。 呼叫 **_close** 也會關閉基礎 OS 檔案控制代碼。 請不要在原始控點上呼叫 **CloseHandle** Win32 函式。 若檔案描述項是由 **FILE &#42;** 資料流所擁有，則在該 **FILE &#42;** 資料流上呼叫 [fclose](fclose-fcloseall.md) 會同時關閉檔案描述項和基礎空點。 在此情況下，請不要在檔案描述項上呼叫 **_close**，或是在原始控點上呼叫 **CloseHandle**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
