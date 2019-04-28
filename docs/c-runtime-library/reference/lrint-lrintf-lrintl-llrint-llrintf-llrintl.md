---
title: lrint、lrintf、lrintl、llrint、llrintf、llrintl
ms.date: 04/05/2018
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: 01680a62e654112475a55bd8eac0cc14d254e2a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285768"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint、lrintf、lrintl、llrint、llrintf、llrintl

使用目前的進位模式和方向，將指定的浮點值四捨五入成最接近的整數值。

## <a name="syntax"></a>語法

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
要四捨五入的值。

## <a name="return-value"></a>傳回值

如果成功，傳回的圓角的整數值*x*。

|問題|Return|
|-----------|------------|
|*x*超出傳回型別的範圍<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|會引發**FE_INVALID** ，並傳回零 (0)。|

## <a name="remarks"></a>備註

因為C++允許多載，您可以呼叫多載**lrint**並**llrint**採用**float**和**長** **雙**型別。 在 C 程式中， **lrint**並**llrint**蝯篔**double**。

如果*x*不代表整數值，這些函式會引發的浮點對應項**FE_INEXACT**。

**Microsoft 專有**:當結果超出傳回型別，範圍或參數為 NaN 或無限大，則傳回的值會是實作所定義。 Microsoft 編譯器會傳回零 (0) 值。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**lrint**， **lrintf**， **lrintl**， **llrint**， **llrintf**， **llrintl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
