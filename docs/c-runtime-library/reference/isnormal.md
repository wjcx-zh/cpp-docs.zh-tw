---
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 2e12cabb57f2e51c08b4d93af33dae85164d016b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213524"
---
# <a name="isnormal"></a>isnormal

判斷浮點值是否為標準值。

## <a name="syntax"></a>語法

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>參數

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

**isnormal** **`true`** 如果引數*x*不是零、偏低、無限，或 NaN，則 isnormal 會傳回非零值（在 c + + 程式碼中）。 否則， **isnormal**會傳回0（ **`false`** 在 c + + 程式碼中為）。

## <a name="remarks"></a>備註

當編譯成 C 時， **isnormal**是一個宏，而當編譯成 c + + 時，是內嵌函式樣板。

## <a name="requirements"></a>需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> 或 \<cmath>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
