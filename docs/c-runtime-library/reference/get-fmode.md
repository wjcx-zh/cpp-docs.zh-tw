---
title: _get_fmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_fmode
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
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a3845de8feb36b995fec8d450bfc5a9656d429c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="getfmode"></a>_get_fmode

取得檔案 I/O 作業的預設檔案轉譯模式。

## <a name="syntax"></a>語法

```C
errno_t _get_fmode( 
   int * pmode 
);
```

### <a name="parameters"></a>參數

*pmode*<br/>
要填入目前的預設模式為整數的指標： **_O_TEXT**或 **_O_BINARY**。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pmode*是**NULL**，會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**EINVAL**。

## <a name="remarks"></a>備註

函式取得 [_fmode](../../c-runtime-library/fmode.md) 全域變數的值。 此變數的低層級指定預設檔案轉譯模式和資料流檔案 I/O 作業，例如 **_open**， **_pipe**， **fopen**，和[freopen](freopen-wfreopen.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_set_fmode](set-fmode.md) 中的範例。

## <a name="see-also"></a>另請參閱

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
