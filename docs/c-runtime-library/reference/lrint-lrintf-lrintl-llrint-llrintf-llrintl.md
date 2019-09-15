---
title: lrint、lrintf、lrintl、llrint、llrintf、llrintl
ms.date: 04/05/2018
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 72870c3548f0fd6972183b0c090708c6eddc591e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953120"
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

如果成功，會傳回*x*的圓角整數值。

|問題|Return|
|-----------|------------|
|*x*超出傳回類型的範圍<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|引發**FE_INVALID** ，並傳回零（0）。|

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用**float**和**long** **double**類型的**lrint**和**llrint**多載。 在 C 程式中， **lrint**和**llrint**一律採用**雙精度浮點數**。

如果*x*不代表整數值的對等浮點，這些函數會引發**FE_INEXACT**。

**Microsoft 特定**：當結果超出傳回型別的範圍時，或是當參數是 NaN 或無限大時，傳回值就會定義為執行。 Microsoft 編譯器會傳回零 (0) 值。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**lrint**、 **lrintf**、 **lrintl**、 **llrint**、 **llrintf**、 **llrintl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
