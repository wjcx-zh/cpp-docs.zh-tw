---
title: _open_osfhandle | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3783420389dc008e39c818c39406f0b2af8af5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569832"
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

如果成功的話， **_open_osfhandle**傳回 C 執行階段檔案描述項。 否則，它會傳回-1。

## <a name="remarks"></a>備註

**_Open_osfhandle**函式配置的 C 執行階段檔案描述元，並將其與所指定的作業系統檔案控制代碼相關聯*osfhandle*。 若要避免編譯器警告，請轉換*osfhandle*引數從**處理**至**intptr_t**。 *旗標*引數是整數運算式形成的其中一個或多個資訊清單常數定義於\<.h >。 當兩個或多個資訊清單常數用於表單*旗標*引數，會使用位元 OR 運算子結合常數 ( **&#124;** )。

中未定義這些資訊清單常數\<.h >:

|||
|-|-|
**\_O\_附加**|在每次寫入作業之前，將檔案指標置放到檔案的結尾。
**\_O\_RDONLY**|開啟檔案為僅供讀取。
**\_O\_TEXT**|以文字 (已轉譯) 模式開啟檔案。
**\_O\_WTEXT**|以 Unicode (已轉譯 UTF-16) 模式開啟檔案。

**_Open_osfhandle**呼叫 Win32 檔案控制代碼的擁有權轉移到的檔案描述項。 若要關閉檔案，以開啟 **_open_osfhandle**，呼叫[\_關閉](close.md)。 藉由呼叫也會關閉基礎的作業系統檔案控制代碼 **_close**，因此不需要呼叫 Win32 函式**CloseHandle**原始的控制代碼上。 如果所擁有的檔案描述項**檔案&#42;** 資料流，然後呼叫[fclose](fclose-fcloseall.md)上**檔案&#42;** 資料流也會關閉的檔案描述項和基礎控制代碼。 在此情況下，請勿呼叫 **_close**上的檔案描述項。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
