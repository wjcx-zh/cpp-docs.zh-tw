---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2d5d4e224b39e9fa597e12975d27fa5720fbfbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345248"
---
# <a name="_get_doserrno"></a>_get_doserrno

獲取作業系統返回的錯誤值,然後再將其轉換為**errno**值。

## <a name="syntax"></a>語法

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指向要填充 **_doserrno**全域宏的當前值的整數的指標。

## <a name="return-value"></a>傳回值

如果 **_get_doserrno**成功,它將返回零;如果成功,則返回零。如果失敗,它將返回一個錯誤代碼。 如果*pValue*為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,此函數將**errno**設定到**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

在 CRT 初始化期間,在進程執行開始之前 **,_doserrno**全域宏設置為零。 此巨集是設定為由會傳回作業系統錯誤的任何系統層級函式呼叫所傳回的作業系統錯誤值，且在執行期間永不重設為 0。 編寫代碼以檢查函數返回的錯誤值時,始終使用函數調用前的[_set_doserrno](set-doserrno.md)清除 **_doserrno。** 因為另一個函數調用可能會覆蓋 **_doserrno,** 因此在函數調用後立即使用 **_get_doserrno**檢查值。

我們建議[_get_errno](get-errno.md)而不是 **_get_doserrno**便攜式錯誤代碼。

**_doserrno**的可能值在 errno.h\<>中 定義。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

**_get_doserrno**是微軟的擴展。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_set_doserrno](set-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist，和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
