---
title: _get_FMA3_enable、_set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: e18db90779ed59a6ca6976f69a5993d94d61c6bc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955938"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable、_set_FMA3_enable

取得或設定旗標，指定超越數學浮點程式庫函式是否使用針對 X64 平臺編譯之程式碼中的 FMA3 指示。

## <a name="syntax"></a>語法

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>參數

*flag*<br/>
設定為1可在 X64 平臺上啟用超越 math 浮點程式庫函式的 FMA3 執行，或設為0，以使用不使用 FMA3 指示的執行。

## <a name="return-value"></a>傳回值

如果已啟用超越 math 浮點程式庫函式的 FMA3 執行，則為非零值。 否則為零。

## <a name="remarks"></a>備註

您可以使用 **_set_FMA3_enable**函式來啟用或停用 CRT 程式庫中超越數學浮點函數的 FMA3 指示。 傳回值會反映在變更之後所使用的執行。 如果 CPU 不支援 FMA3 指令，則此函式無法在程式庫中啟用它們，而且傳回值為零。 使用 **_get_FMA3_enable**來取得程式庫的目前狀態。 根據預設，在 X64 平臺上，CRT 啟動程式碼會偵測 CPU 是否支援 FMA3 指令，並啟用或停用程式庫中的 FMA3 程式。

由於 FMA3 的執行會使用不同的演算法，因此當啟用或停用 FMA3 的 FMA3 時，或是在執行或不支援的電腦之間，可能會觀察到計算結果的些許差異。 如需詳細資訊，請參閱[浮點遷移問題](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>需求

**_Set_FMA3_enable**和 **_get_FMA3_enable**函數僅適用于 CRT 的 X64 版本。

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_FMA3_enable**、 **_get_FMA3_enable**| C：\<math.h><br />C++： \<h > 或\<math >|

**_Set_FMA3_enable**和 **_get_FMA3_enable**函式是 Microsoft 特有的功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[浮點數的移轉問題](../../porting/floating-point-migration-issues.md)<br/>
