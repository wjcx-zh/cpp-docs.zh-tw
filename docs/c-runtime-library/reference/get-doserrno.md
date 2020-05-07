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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7b889bccc0b1f1fd99a9a0526bbfb42a2e520970
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919378"
---
# <a name="_get_doserrno"></a>_get_doserrno

取得作業系統傳回的錯誤值，再將其轉譯成**errno**值。

## <a name="syntax"></a>語法

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
要以 **_doserrno**全域宏的目前值填入的整數指標。

## <a name="return-value"></a>傳回值

如果 **_get_doserrno**成功，則會傳回零;如果失敗，則會傳回錯誤碼。 如果*pValue*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

## <a name="remarks"></a>備註

在啟動進程之前， **_doserrno**全域宏會在 CRT 初始化期間設定為零。 此巨集是設定為由會傳回作業系統錯誤的任何系統層級函式呼叫所傳回的作業系統錯誤值，且在執行期間永不重設為 0。 當您撰寫程式碼來檢查函式所傳回的錯誤值時，請一律在函式呼叫之前使用[_set_doserrno](set-doserrno.md)來清除 **_doserrno** 。 因為另一個函式呼叫可能會覆寫 **_doserrno**，所以請在函式呼叫之後立即使用 **_get_doserrno**來檢查該值。

我們建議[_get_errno](get-errno.md) ，而不是可移植錯誤碼的 **_get_doserrno** 。

**_Doserrno**的可能值會定義在\<errno> 中。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

**_get_doserrno**是 Microsoft 擴充功能。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_set_doserrno](set-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist，和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
