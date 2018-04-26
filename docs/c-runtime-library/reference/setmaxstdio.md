---
title: _setmaxstdio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c0f54f43b0abb5fff2d13233847b45acdb5f0be
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio

設定在同時開啟的檔案數目上限**stdio**層級。

## <a name="syntax"></a>語法

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>參數

*newmax*<br/>
新的最大的在同時開啟的檔案數目**stdio**層級。

## <a name="return-value"></a>傳回值

傳回*newmax*如果成功; 否則為-1。

如果*newmax*是小於 **_IOB_ENTRIES**或更高，則可以使用作業系統無效參數處理常式中的控制代碼的數目上限會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，此函數會傳回-1 和設定允許執行**errno**至**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Setmaxstdio**函式變更可能會在同時開啟的檔案數目的最大值**stdio**層級。

C 執行階段 I/O 支援在 Win32 平台上的開啟檔案數目，現在會多於舊版本。 2048 的檔案最多可以同時在開啟[lowio 層級](../../c-runtime-library/low-level-i-o.md)(也就是開啟，並藉由存取 **_open**，**閱讀**， **_write**、 依此類推系列的 I/O 函式)。 512 檔案最多可以同時在開啟[stdio 層級](../../c-runtime-library/stream-i-o.md)(也就是開啟，並藉由存取**fopen**， **fgetc**， **fputc**依此類推系列的函式)。 在 512 開啟檔案的限制**stdio**層級可以增加至 2048 藉由最多 **_setmaxstdio**函式。

因為**stdio**層級函式，例如**fopen**，最上層的內建**lowio**函式數目上限 2048 是永久的數目上限同時開啟存取透過 C 執行階段程式庫的檔案。

> [!NOTE]
> 這個上限可能超過特定 Win32 平台和組態所支援的值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[_getmaxstdio](getmaxstdio.md)的使用範例 **_setmaxstdio**。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
