---
title: _setmaxstdio
ms.date: 05/21/2019
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
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 94b768d920ffd86a5bd762f8994244dda67fb15f
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174818"
---
# <a name="setmaxstdio"></a>_setmaxstdio

設定在資料流 I/O 層級同時開啟的檔案數目上限。

## <a name="syntax"></a>語法

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>參數

*new_max*<br/>
在資料流 I/O 層級同時開啟的檔案數目新上限。

## <a name="return-value"></a>傳回值

若成功，傳回 *new_max*；否則傳回 -1。

若 *new_max* 小於 **_IOB_ENTRIES**，或是大於作業系統中可用的控點數量上限，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 -1，並將 **errno** 設為 **EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_setmaxstdio** 函式會變更在資料流層級可同時開啟的檔案數量上限值。

C 執行階段 I/O 現在支援在[低 I/O 層級](../../c-runtime-library/low-level-i-o.md)最多同時開啟 8,192 個檔案。 此層級包含使用 **_open**、**_read** 及 **_write** I/O 函式系列開啟及存取的檔案。 根據預設，最多可在[資料流 I/O 層級](../../c-runtime-library/stream-i-o.md)同時開啟 512 個檔案。 此層級包含使用 **fopen**、 及 **fputc** 函式系列開啟及存取的檔案。 在資料流 I/O 層級開啟 512 個檔案的限制，可透過使用 **_setmaxstdio** 函式將上限增加到最多 8,192。

因為串流 I/O 層級函式 (例如 **fopen**) 是建置在低 I/O 層級函式上，8,192 的上限是透過 C 執行階段程式庫同時開啟檔案的固定數量上限。

> [!NOTE]
> 此上限可能會超過特定 Win32 平台和組態支援的值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需 **_setmaxstdio** 的使用範例，請參閱 [_getmaxstdio](getmaxstdio.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
