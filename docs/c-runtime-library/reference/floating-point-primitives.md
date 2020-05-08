---
title: 浮點數基本類型
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: c103d28dc111af4736bdc299b498b98eccb3af60
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916689"
---
# <a name="floating-point-primitives"></a>浮點數基本類型

用來實作為標準 C 執行時間程式庫（CRT）浮點函式的 Microsoft 特定基本函數。 它們在此為完整性記載，但不建議使用。 這些函式中的某些函式會被視為未使用，因為已知這些函式有精確度、例外狀況處理，以及符合 IEEE-754 行為的問題。 它們只存在於程式庫中，以提供回溯相容性。 如需正確的行為、可攜性和遵循標準，建議您針對這些函式使用標準浮點函數。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass、_ldclass、_fdclass

### <a name="syntax"></a>語法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函數引數。

### <a name="remarks"></a>備註

這些浮點基本型別會針對浮點類型，實作為 CRT 宏[fpclassify](fpclassify.md)的 C 版本。 引數*x*的分類會當做其中一個常數（定義于 math. h 中）傳回：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正或負偏低（反正規化）值 |
| **FP_ZERO** | 正或負零值 |

如需其他詳細資料，您可以使用 Microsoft 專有的[_fpclass，_fpclassf](fpclass-fpclassf.md)函數。 使用[fpclassify](fpclassify.md)宏或函式來提供可攜性。

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign、_ldsign、_fdsign

### <a name="syntax"></a>語法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函數引數。

### <a name="remarks"></a>備註

這些浮點基本類型會在 CRT 中執行[signbit](signbit.md)宏或函式。 如果在引數*x*的有效位數（尾數）中設定正負號位，則會傳回非零值，如果未設定正負號位，則傳回0。

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp、_ldpcomp、_fdpcomp

### <a name="syntax"></a>語法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>參數

*x*、 *y*<br/>
浮點函數引數。

### <a name="remarks"></a>備註

這些浮點基本類型會採用兩個引數*x*和*y*，並傳回值，以顯示其順序關聯性（以這些常數的位 or 表示），定義于 math 中：

| 值 | 描述 |
|------------|-----------------|
| **_FP_LT** | *x*可視為小於*y* |
| **_FP_EQ** | *x*可以視為等於*y* |
| **_FP_GT** | *x*可以視為大於*y* |

這些基本專案會在 CRT 中執行[isgreater、isgreaterequal、isless、islessequal、islessgreater 和 isunordered](floating-point-ordering.md)宏和函數。

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest、_ldtest、_fdtest

### <a name="syntax"></a>語法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>參數

*圖元*<br/>
浮點引數的指標。

### <a name="remarks"></a>備註

這些浮點基本型別會針對浮點型別，實作用的 CRT 函式[fpclassify](fpclassify.md)的 c + + 版本。 會評估引數*x* ，並傳回分類作為下列其中一個常數（定義于 math. h 中）：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正或負偏低（反正規化）值 |
| **FP_ZERO** | 正或負零值 |

如需其他詳細資料，您可以使用 Microsoft 專有的[_fpclass，_fpclassf](fpclass-fpclassf.md)函數。 請使用[fpclassify](fpclassify.md)函式來提供可攜性。

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int、_ld_int、_fd_int

### <a name="syntax"></a>語法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>參數

*圖元*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類型的指數。

### <a name="remarks"></a>備註

這些浮點基本專案會取得浮點值*px*和指數值*exp*的指標，並盡可能移除指定指數底下的浮點值小數部分。 傳回的值是以*px*中的輸入值為**fpclassify**的結果（如果它是 NaN 或無限大），另一個則是*px*的輸出值。

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale、_ldscale、_fdscale

### <a name="syntax"></a>語法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>參數

*圖元*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類型的指數。

### <a name="remarks"></a>備註

這些浮點基本型別會使用浮點值*px*的指標和指數值*exp*，並盡可能將*px*中的值調整為 2<sup>*exp*</sup>。 傳回的值是以*px*中的輸入值為**fpclassify**的結果（如果它是 NaN 或無限大），另一個則是*px*的輸出值。 針對可攜性，建議使用[ldexp、ldexpf 和 ldexpl](ldexp.md)函式。

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale、_ldunscale、_fdunscale

### <a name="syntax"></a>語法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>參數

*pexp*<br/>
做為整數型別之指數的指標。

*圖元*<br/>
浮點引數的指標。

### <a name="remarks"></a>備註

這些浮點基本類型會在可能的情況下，將*px*所指向的浮點值分解成有效位數（尾數）和指數。 有效位數會進行調整，讓絕對值大於或等於0.5 且小於1.0。 指數是*n*值，其中原始浮點值等於相應縮小的有效位數時間 2<sup>*n*</sup>。 這個整數指數*n*會儲存在*pexp*所指向的位置。 傳回的值是以*px*中的輸入值為**fpclassify**的結果（如果它是 NaN 或無限大），而在輸出值上則為，否則為。 針對可攜性，偏好使用[frexp、frexpf、frexpl](frexp.md)函數。

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp、_ldexp、_fdexp

### <a name="syntax"></a>語法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>參數

*y*<br/>
浮點函數引數。

*圖元*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類型的指數。

### <a name="remarks"></a>備註

這些浮點基本類型會在*px*等於*y* * 2<sup>*exp*</sup>的位置中，建立浮點值。 傳回的值是在*y*的輸入值上**fpclassify**的結果（如果它是 NaN 或無限大），或以*px*的輸出值為依據。 針對可攜性，建議使用[ldexp、ldexpf 和 ldexpl](ldexp.md)函式。

## <a name="_dnorm-_fdnorm"></a>_dnorm，_fdnorm

### <a name="syntax"></a>語法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>參數

*ps*<br/>
以不**帶正負**號的**short**陣列表示的浮點值之位表示的指標。

### <a name="remarks"></a>備註

這些浮點基本類型會將 underflowed 浮點值的小數部分正規化，並調整*特性*或偏誤指數以符合。 此值會傳遞為浮點類型的位標記法，而轉換成不**帶正負****號 short**的陣列， `_double_val`方法`_ldouble_val`是透過`_float_val`在 math 中宣告的、或類型 punning 聯集。 傳回值是在輸入浮點值上**fpclassify**的結果（如果它是 NaN 或無限大），否則為輸出值。

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly、_ldpoly、_fdpoly

### <a name="syntax"></a>語法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函數引數。

*table*<br/>
多項式之常數係數的資料表指標。

*n*<br/>
要評估之多項式的順序。

### <a name="remarks"></a>備註

這些浮點基本型別會在 order *n*的多項式中傳回*x*的評估，其係數是由*資料表*中對應的常數值表示。 例如，如果*資料表*\[0] = 3.0、[*資料表*\[1] = 4.0、 *[資料表*\[2] = 5.0 和*n* = 2，則表示多項式 5.0 x<sup>2</sup> + 4.0 x + 3.0。 如果評估此多項式的*x*為2.0，則結果為31.0。 這些函數不會在內部使用。

## <a name="_dlog-_dlog-_dlog"></a>_dlog、_dlog、_dlog

### <a name="syntax"></a>語法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函數引數。

*base_flag*<br/>
控制要使用之基底的旗標，基*底為*0，base 10 則為非零。

### <a name="remarks"></a>備註

當*base_flag*為0時，這些浮點基本類型會傳回*x*、ln （*x*）或 log<sub>*e*</sub>（*x*）的自然記錄。 當*base_flag*為非零時，它們會傳回*x*的對數基底10或記錄<sub>10</sub>（*x*）。 這些函數不會在內部使用。 針對可攜性，偏好使用[log、logf、記錄、log10、log10f 和 log10l](log-logf-log10-log10f.md)函數。

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin、_ldsin、_fdsin

### <a name="syntax"></a>語法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函數引數。

*四分之一*<br/>
0、1、2或3的象限位移，用來`sin`產生、 `cos`、 `-sin`和`-cos`結果。

### <a name="remarks"></a>備註

這些浮點基本型別會以*象限*模數4傳回*x*位移的正弦值。 實際上，當*象限*模數4分別為0、1、2或3時，它們會傳回*x*的正弦、余弦、-正弦和-余弦。 這些函數不會在內部使用。 針對可攜性，偏好使用[sin、sinf、sinl](sin-sinf-sinl.md)、 [cos、cosf 和 cosl](cos-cosf-cosl.md)函數。

## <a name="requirements"></a>需求

Header： \<math. h>

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、ldexpf 和 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
