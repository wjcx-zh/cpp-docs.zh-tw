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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346716"
---
# <a name="floating-point-primitives"></a>浮點數基本類型

特定於 Microsoft 的原始函數,用於實現某些標準 C 運行時庫 (CRT) 浮點函數。 此處記錄它們的完整性,但不建議使用。 其中一些函數被標記為未使用,因為它們在精度、異常處理和符合 IEEE-754 行為方面存在問題。 它們僅存在於庫中,以便向後相容性。 為了正確的行為、可移植性和對標準的遵守,首選標準浮點功能而不是這些函數。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass,_ldclass,_fdclass

### <a name="syntax"></a>語法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點函數參數。

### <a name="remarks"></a>備註

這些浮點基元實現針對浮點類型的 CRT 宏[fp 分類](fpclassify.md)的 C 版本。 參數*x*的類別傳回為以下常量之一,在 math.h 中定義:

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正或負次正次正態 (非規範化)值 |
| **FP_ZERO** | 正或負零值 |

有關其他詳細資訊,可以使用特定於Microsoft[的_fpclass,_fpclassf](fpclass-fpclassf.md)功能。 使用[fp分類](fpclassify.md)宏或函數進行便攜性。

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign,_ldsign,_fdsign

### <a name="syntax"></a>語法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點函數參數。

### <a name="remarks"></a>備註

這些浮點基元在 CRT 中實現[符號位](signbit.md)宏或函數。 如果符號位設置在參數*x*的符號(mantissa)中,則返回非零值;如果未設定符號位,則返回 0。

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp、_ldpcomp、_fdpcomp

### <a name="syntax"></a>語法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>參數

*x*, *y*<br/>
浮點函數參數。

### <a name="remarks"></a>備註

這些浮點基元採用兩個參數 *,x*和*y*,並傳回一個值,顯示它們的排序關係,表示為位或這些常量,在 math.h 中定義:

| 值 | 描述 |
|------------|-----------------|
| **_FP_LT** | *x*可視為小於*y* |
| **_FP_EQ** | *x*可以被視為等於*y* |
| **_FP_GT** | *x*可視為大於*y* |

這些基元在CRT中實現["較大"、"相等"、"無均"、"無均"、"無命令"和"無命令](floating-point-ordering.md)宏"和"無命令"宏和函數。

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest,_ldtest,_fdtest

### <a name="syntax"></a>語法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>參數

*Px*<br/>
指向浮點參數的指標。

### <a name="remarks"></a>備註

這些浮點基元實現C++版本的CRT 函數[fp 分類](fpclassify.md)的浮點類型。 參數*x*被計算,分類傳回為以下常數之一,在 math.h 中定義:

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正或負次正次正態 (非規範化)值 |
| **FP_ZERO** | 正或負零值 |

有關其他詳細資訊,可以使用特定於Microsoft[的_fpclass,_fpclassf](fpclass-fpclassf.md)功能。 使用[fp分類](fpclassify.md)函數進行便攜性。

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int,_ld_int,_fd_int

### <a name="syntax"></a>語法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>參數

*Px*<br/>
指向浮點參數的指標。

*exp*<br/>
作為積分類型的指數。

### <a name="remarks"></a>備註

這些浮點基元獲取指向浮點值*px*和指數值*exp*的指標,並盡可能刪除給定指數下浮點值的分數部分。 返回的值是按*px(* 如果是 NaN 或無窮大)和對以*px(* 否則)的輸出值進行**fp 分類**的結果。

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale,_ldscale,_fdscale

### <a name="syntax"></a>語法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>參數

*Px*<br/>
指向浮點參數的指標。

*exp*<br/>
作為積分類型的指數。

### <a name="remarks"></a>備註

這些浮點基元採用指向浮點值*px*和指數值*exp*的指標,如果可能,以*px*為例縮放值 2<sup>*exp。*</sup> 返回的值是按*px(* 如果是 NaN 或無窮大)和對以*px(* 否則)的輸出值進行**fp 分類**的結果。 對於可移植性,請首選[ldexp、ldexpf 和 ldexpl](ldexp.md)函數。

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale,_ldunscale,_fdunscale

### <a name="syntax"></a>語法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>參數

*pexp*<br/>
指向指數作為積分類型的指標。

*Px*<br/>
指向浮點參數的指標。

### <a name="remarks"></a>備註

如果可能,這些浮點基元將*px*指向的浮點值分解為符號(mantissa)和指數(如果可能)。 符號縮放,使絕對值大於或等於 0.5 和小於 1.0。 指數是值*n,* 其中原始浮點值等於縮放的符號乘法乘以 2<sup>*n*</sup>。 此整數指數*n*存儲在*pexp*指向的位置。 返回的值是輸入*值(如果是*NaN 或無窮大)和對輸出值(否則)的**fp 分類**的結果。 對於便攜性,請首選[frexp、frexpf、frexpl](frexp.md)函數。

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp,_ldexp,_fdexp

### <a name="syntax"></a>語法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>參數

*Y*<br/>
浮點函數參數。

*Px*<br/>
指向浮點參數的指標。

*exp*<br/>
作為積分類型的指數。

### <a name="remarks"></a>備註

這些浮點基元在*以 px*表示等於*y* = 2<sup>*exp*</sup>的位置建構一個浮點值。 返回的值是*y*中的輸入值(如果是 NaN 或無窮大)和對*以 px*表示的輸出值(否則)的 fp**分類**的結果。 對於可移植性,請首選[ldexp、ldexpf 和 ldexpl](ldexp.md)函數。

## <a name="_dnorm-_fdnorm"></a>_dnorm,_fdnorm

### <a name="syntax"></a>語法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>參數

*ps*<br/>
指向以**無符號****短**陣列表示的浮點值的位表示。

### <a name="remarks"></a>備註

這些浮點基元使浮點值的分餾部分規範化,並調整*特徵*或偏置指數來匹配。 該值作為浮點類型的位錶示形式傳遞,轉換為`_double_val`透過`_ldouble_val`、`_float_val`或類型在 math.h 中聲明的無**符號****短**的陣列。 返回值是輸入浮點值(如果是 NaN 或無窮大)和輸出值(否則)上的**fp 分類**的結果。

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly,_ldpoly,_fdpoly

### <a name="syntax"></a>語法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點函數參數。

*表*<br/>
指向多項式常量係數表的指標。

*n*<br/>
要評估的多項式順序。

### <a name="remarks"></a>備註

這些浮點基元返回階的多項式*n*中*x*的評估,其係數由*表中*的相應常量值表示。 例如,如果*表*\[0= = 3.0,*表*\[1= 4.0,*表*\[2= 5.0,n = 2,則表示多項式 5.0x<sup>2</sup> = 4.0x = 3.0。 *n* 如果此多項式計算為*x* 2.0,則結果為 31.0。 這些函數不在內部使用。

## <a name="_dlog-_dlog-_dlog"></a>_dlog,_dlog,_dlog

### <a name="syntax"></a>語法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點函數參數。

*base_flag*<br/>
控制要使用的基礎的標誌,0 表示基*e,0*表示基 10。

### <a name="remarks"></a>備註

當*base_flag*為 0 時,這些浮點基元傳回 x、ln(x ) 或日誌*x*<sub>*e*</sub> * * *(x)* 的自然日誌。 當*base_flag*為非零時,它們返回*x*的日誌基 10 或日誌<sub>10</sub>*(x*)。 這些函數不在內部使用。 對於可移植性,請首選函數[日誌、logf、logl、log10、log10f 和 log10l](log-logf-log10-log10f.md)。

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin,_ldsin,_fdsin

### <a name="syntax"></a>語法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點函數參數。

*象限*<br/>
象限偏移 0、1、2 或`sin``cos`3`-sin``-cos`用於生成 、 和 結果。

### <a name="remarks"></a>備註

這些浮點基元返回*象**限*莫杜洛 4 偏移 x 的子值。 當*象限*莫杜洛 4 分別為 0、1、2 或 3 時,它們返回*x*的正子、協和子、正子和 -協和子。 這些函數不在內部使用。 對於便攜性,首選[子、鼻、弦、](sin-sinf-sinl.md)[科斯、科斯夫和科斯爾](cos-cosf-cosl.md)函數。

## <a name="requirements"></a>需求

標題:\<數學.h>

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支撐](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[是因夫](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、ldexpf 和 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
