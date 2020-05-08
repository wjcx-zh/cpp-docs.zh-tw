---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: 3e59e608f83874088b64d316c04053b94d8fbfdd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909852"
---
# <a name="_get_fmode"></a>_get_fmode

取得檔案 I/O 作業的預設檔案轉譯模式。

## <a name="syntax"></a>語法

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>參數

*pmode*<br/>
要以目前預設模式填滿之整數的指標： **_O_TEXT**或 **_O_BINARY**。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pmode*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**EINVAL**。

## <a name="remarks"></a>備註

函式取得 [_fmode](../../c-runtime-library/fmode.md) 全域變數的值。 這個變數會指定低層級和資料流程檔案 i/o 作業的預設檔案轉譯模式，例如 **_open**、 **_pipe**、 **fopen**和[freopen](freopen-wfreopen.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_set_fmode](set-fmode.md) 中的範例。

## <a name="see-also"></a>另請參閱

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[文字和二進位模式檔案 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
