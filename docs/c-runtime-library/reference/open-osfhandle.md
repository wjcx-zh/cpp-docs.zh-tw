---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: d0f86c2588eed506bc9b8408e01bccdb6d1aad9d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844063"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

將 C 執行時間檔案描述項與現有的作業系統檔案控制代碼建立關聯。

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

**_Open_osfhandle**函數會配置 C 執行時間檔案描述項。 它會將此檔案描述項與 *>osfhandle*所指定的作業系統檔案控制代碼建立關聯。 若要避免編譯器警告，請將 *osfhandle* 引數從 **HANDLE** 轉換成 **intptr_t**。 *旗標*引數是從中定義的一或多個資訊清單常數所組成的整數運算式 \<fcntl.h> 。 您可以使用位 OR 運算子 ( **&#124;** ) 結合兩個或多個資訊清單常數來形成 *旗標* 引數。

這些資訊清單常數定義于 \<fcntl.h> ：

| 持續性 | 描述 |
|--|--|
| **\_O \_ 附加** | 在每次寫入作業之前，將檔案指標置放到檔案的結尾。 |
| **\_O \_ RDONLY** | 開啟檔案為僅供讀取。 |
| **\_O \_ 文字** | 以文字 (已轉譯) 模式開啟檔案。 |
| **\_O \_ WTEXT** | 以 Unicode (已轉譯 UTF-16) 模式開啟檔案。 |

**_open_osfhandle** 呼叫會將 Win32 檔案控制代碼的擁有權轉送給檔案描述項。 或要使用 **_open_osfhandle** 關閉開啟的檔案，請呼叫 [\_close](close.md)。 呼叫 **_close** 也會關閉基礎 OS 檔案控制代碼。 請不要在原始控點上呼叫 **CloseHandle** Win32 函式。 如果檔案描述項是由檔案 **&#42;** 資料流程所擁有，則呼叫 [fclose](fclose-fcloseall.md) 會關閉檔案描述項和基礎控制碼。 在此情況下，請不要在檔案描述項上呼叫 **_close**，或是在原始控點上呼叫 **CloseHandle**。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
