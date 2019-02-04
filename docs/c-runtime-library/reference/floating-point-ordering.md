---
title: isgreater、 isgreaterequal、 isless、 islessequal、 islessgreater、 isunordered
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
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703416"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater、 isgreaterequal、 isless、 islessequal、 islessgreater、 isunordered

判斷兩個浮點數的值之間的順序關聯性。

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

*x*， *y*<br/>
要比較的浮點值。

## <a name="return-value"></a>傳回值

在所有的比較中，將相同的正負號的比較為相等。 負的無限值是小於任何有限值或無限大的正數。 正無限值大於任何有限值或負的無限值。 零，而不論登相等。 Nan 不小於、 等於或大於任何值，包括另一的 NaN。

當兩種引數是 NaN、 排序的巨集**isgreater**， **isgreaterequal**， **isless**，以及**islessequal**傳回非零如果值之間指定的順序關聯*x*並*y*保存，則為 true。 如果任一個或兩個引數是 Nan，或如果排序的關聯性，則為 false，這些巨集就會傳回 0。 函式表單以相同的方式運作，但傳回**真**或是**false**。

**Islessgreater**巨集會傳回非零值，如果兩個*x*並*y*不是 Nan，以及*x*是小於或大於*y*。 如果任一個或兩個引數是 Nan，或如果值相等，則會傳回 0。 函式表單相同的行為，但會傳回**真**或是**false**。

**Isunordered**巨集會傳回非零值，如果有任一*x*， *y*，或兩者都是 Nan。 否則它會傳回 0。 函式表單相同的行為，但會傳回**真**或是**false**。

## <a name="remarks"></a>備註

這些比較作業會實作為巨集時編譯為 C，以及內嵌樣板函式編譯為 c + + 時。

## <a name="requirements"></a>需求

|功能|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**， **isgreaterequal**， **isless**，<br/>**islessequal**， **islessgreater**， **isunordered** | \<math.h> | \<math.h> 或 \<cmath> |

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite _finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
