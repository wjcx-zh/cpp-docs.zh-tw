---
title: isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 907b26f4e1824d7ef5c7c1a36b4e4d8ccb74c978
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220713"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered

判斷兩個浮點值之間的順序關聯性。

## <a name="syntax"></a>語法

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>參數

*x*、 *y*<br/>
要比較的浮點值。

## <a name="return-value"></a>傳回值

在所有比較中，具有相同正負號比較的無窮大不相等。 負無限大小於任何有限值或正無限大。 正無限大大於任何有限值或負無限大。 無論正負號，零都是相等的。 Nan 不小於、等於或大於任何值，包括另一個 NaN。

當兩個引數都不是 NaN 時，如果*x*和*y*之間指定的順序關聯為 true，則排序宏**isgreater**、 **isgreaterequal**、 **isless**和**islessequal**會傳回非零值。 如果其中一個或兩個引數為 Nan，或如果排序關聯性為 false，則這些宏會傳回0。 函式表單的行為方式相同，但會傳回 **`true`** 或 **`false`** 。

如果*x*和*y*都不是 nan，而且*x*小於或大於*y*，則**islessgreater**宏會傳回非零值。 如果其中一個或兩個引數都是 Nan，或如果值相等，則會傳回0。 函式表單的行為方式相同，但會傳回 **`true`** 或 **`false`** 。

如果*x*、 *y*或兩者都是 nan，則**isunordered**宏會傳回非零值。 否則，它會傳回 0。 函式表單的行為方式相同，但會傳回 **`true`** 或 **`false`** 。

## <a name="remarks"></a>備註

當編譯成 C 時，這些比較作業會實作為宏，並在編譯為 c + + 時當做內嵌範本函式來執行。

## <a name="requirements"></a>需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**、 **isgreaterequal**、 **isless**、<br/>**islessequal**、 **islessgreater**、 **isunordered** | \<math.h> | \<math.h> 或 \<cmath> |

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
