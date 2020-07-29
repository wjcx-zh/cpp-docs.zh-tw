---
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: 7366f340477bf1bb50ebe1e53bcec1f3e16e0863
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234090"
---
# <a name="isinf"></a>isinf

判斷浮點值是否為無限大。

## <a name="syntax"></a>語法

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>參數

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

**isinf** **`true`** 如果引數*x*是正的或負無限大，則 isinf 會傳回非零值（在 c + + 程式碼中）。 **isinf** **`false`** 如果引數為有限或 NAN，則 isinf 會傳回0（在 c + + 程式碼中）。 一般和偏低浮點值都會視為有限。

## <a name="remarks"></a>備註

當編譯成 C 時， **isinf**是一個宏，而當編譯為 c + + 時，則是內嵌的範本函式。

## <a name="requirements"></a>需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<math.h> 或 \<cmath>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
