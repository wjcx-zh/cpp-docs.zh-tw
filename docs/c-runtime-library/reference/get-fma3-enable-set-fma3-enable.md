---
title: _get_fma3_enable、_set_fma3_enable
ms.date: 04/05/2018
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544361"
---
# <a name="getfma3enable-setfma3enable"></a>_get_fma3_enable、_set_fma3_enable

取得或設定旗標，指定是否超越數學的浮點程式庫函式使用 FMA3 指示在編譯程式碼適用於 X64 平台。

## <a name="syntax"></a>語法

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>參數

*flag*<br/>
設為 1 以啟用 FMA3 超越數學的浮點程式庫函式的實作在 X64 平台，或 0 表示使用不使用 FMA3 指令的實作。

## <a name="return-value"></a>傳回值

如果啟用 FMA3 超越數學的浮點程式庫函式的實作，則非零值。 否則為零。

## <a name="remarks"></a>備註

使用  **_set_FMA3_enable**啟用或停用使用 fma3 超越數學浮點函式中的 CRT 程式庫中的函式。 傳回值會反映在變更後的實作中使用。 如果 CPU 不支援 FMA3 指示，此函式不能在程式庫中啟用它們，並傳回值為零。 使用 **_get_FMA3_enable**取得媒體櫃的目前狀態。 根據預設，在 X64 平台，CRT 啟始程式碼偵測到 CPU 支援 FMA3 指示，以及啟用或停用文件庫中的 FMA3 實作。

FMA3 實作會使用不同的演算法，因為有些微的差異計算的結果可能是可預見值，當 FMA3 實作已啟用或停用，或電腦或是不支援 FMA3 之間。 如需詳細資訊，請參閱 <<c0> [ 浮點數的移轉問題](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>需求

**_Set_FMA3_enable**並 **_get_FMA3_enable**函式只會適用於 X64 版本的 CRT。

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_FMA3_enable**， **_get_FMA3_enable**| C：\<math.h><br />C + +: \<cmath> > 或\<math.h> >|

**_Set_FMA3_enable**並 **_get_FMA3_enable**函式是 Microsoft 專有的。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[浮點數的移轉問題](../../porting/floating-point-migration-issues.md)<br/>
