---
title: 浮點數基本類型
ms.date: 01/31/2019
apiname:
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
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703419"
---
# <a name="floating-point-primitives"></a>浮點數基本類型

Microsoft 專有基本函式用來實作一些標準 C 執行階段程式庫 (CRT) 浮點函式。 它們為求完整性，這裡記載，但不建議使用。 其中一些函式會有註明為未使用，因為它們已知的有效位數、 例外狀況處理和 IEEE-754 行為的相容性問題。 它們存在於程式庫僅為回溯相容性。 為正確的行為，可攜性，並遵循標準，而不用標準的浮點函式這些函式。

## <a name="dclass-ldclass-fdclass"></a>_dclass _ldclass _fdclass

### <a name="syntax"></a>語法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函式引數。

### <a name="remarks"></a>備註

下列浮點數基本類型實作 CRT 巨集的 C 新版[fpclassify](fpclassify.md)浮點類型。 引數分類*x*傳回做為其中一個這些常數，定義於 math.h 中：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正數或負數 subnormal （反正規化） 值 |
| **FP_ZERO** | 正或負零值 |

如需詳細資料，您可以使用 Microsoft 專有[_fpclass、 _fpclassf](fpclass-fpclassf.md)函式。 使用[fpclassify](fpclassify.md)巨集或函式的可攜性。

## <a name="dsign-ldsign-fdsign"></a>_dsign _ldsign _fdsign

### <a name="syntax"></a>語法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函式引數。

### <a name="remarks"></a>備註

下列浮點數基本類型實作[signbit](signbit.md)巨集或 CRT 中的函式。 它們會傳回非零值，如果正負號位元引數的有效數字 （尾數） 中設定*x*，0，如果未設定正負號位元。

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp _ldpcomp _fdpcomp

### <a name="syntax"></a>語法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>參數

*x*， *y*<br/>
浮點函式引數。

### <a name="remarks"></a>備註

下列浮點數基本類型不接受兩個引數， *x*並*y*，並傳回值，以顯示其排序的關聯性，以位元，或兩個常數，定義於 math.h 中表示：

| 值 | 描述 |
|------------|-----------------|
| **_FP_LT** | *x*可以視為小於*y* |
| **_FP_EQ** | *x*可以視為等於*y* |
| **_FP_GT** | *x*可以視為大於*y* |

下列基本類型實作[isgreater，isgreaterequal，isless，islessequal，islessgreater，和 isunordered](floating-point-ordering.md)巨集和 CRT 中的函式。

## <a name="dtest-ldtest-fdtest"></a>_dtest _ldtest _fdtest

### <a name="syntax"></a>語法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>參數

*px*<br/>
浮點引數的指標。

### <a name="remarks"></a>備註

下列浮點數基本類型實作 c + + 版本的 CRT 函式[fpclassify](fpclassify.md)浮點類型。 引數*x*會評估並傳回做為其中一個這些常數，定義於 math.h 中分類：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 無訊息、訊號或不確定的 NaN |
| **FP_INFINITE** | 正或負無限大 |
| **FP_NORMAL** | 正或負標準化非零值 |
| **FP_SUBNORMAL** | 正數或負數 subnormal （反正規化） 值 |
| **FP_ZERO** | 正或負零值 |

如需詳細資料，您可以使用 Microsoft 專有[_fpclass、 _fpclassf](fpclass-fpclassf.md)函式。 使用[fpclassify](fpclassify.md)可攜性的函式。

## <a name="dint-ldint-fdint"></a>_d_int _ld_int _fd_int

### <a name="syntax"></a>語法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>參數

*px*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類資料類型的指數。

### <a name="remarks"></a>備註

下列浮點數基本類型將指標帶到浮點值*px*和指數值*exp*，並盡可能移除給定的指數，以下的浮點值的小數部分. 傳回的值是結果**fpclassify**中的輸入值*px* NaN 或無限大，是否與執行中的輸出值*px*否則。

## <a name="dscale-ldscale-fdscale"></a>_dscale _ldscale _fdscale

### <a name="syntax"></a>語法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>參數

*px*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類資料類型的指數。

### <a name="remarks"></a>備註

下列浮點數基本類型將指標帶到浮點值*px*和指數值*exp*，並調整中的值*px* 2<sup> *exp*</sup>、 的話。 傳回的值是結果**fpclassify**中的輸入值*px* NaN 或無限大，是否與執行中的輸出值*px*否則。 對於可攜性，想[ldexp、 ldexpf、 ldexpl 和](ldexp.md)函式。

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale _ldunscale _fdunscale

### <a name="syntax"></a>語法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>參數

*pexp*<br/>
整數類資料類型為指數的指標。

*px*<br/>
浮點引數的指標。

### <a name="remarks"></a>備註

下列浮點數基本類型細分所指向的浮點數值*px*有效數字 （尾數） 和指數，如果可能的話。 有效數字會縮放，這類的絕對值是大於或等於 0.5 並小於 1.0。 指數是值*n*原始浮點數的值等於乘以 2，調整有效位數<sup>*n*</sup>。 此整數指數*n*所指向的位置會儲存*pexp*。 傳回的值是結果**fpclassify**中的輸入值*px* NaN 或無限大，是否和輸出值，否則為。 對於可攜性，想[frexp、 frexpf、 frexpl](frexp.md)函式。

## <a name="dexp-ldexp-fdexp"></a>_dexp _ldexp _fdexp

### <a name="syntax"></a>語法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>參數

*y*<br/>
浮點函式引數。

*px*<br/>
浮點引數的指標。

*exp*<br/>
做為整數類資料類型的指數。

### <a name="remarks"></a>備註

下列浮點數基本類型建構所指向的位置中的浮點值*px*等於*y* * 2<sup>*exp*</sup>。 傳回的值是結果**fpclassify**中的輸入值*y* NaN 或無限大，是否與執行中的輸出值*px*否則。 對於可攜性，想[ldexp、 ldexpf、 ldexpl 和](ldexp.md)函式。

## <a name="dnorm-fdnorm"></a>_dnorm _fdnorm

### <a name="syntax"></a>語法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>參數

*ps*<br/>
位元表示浮點值，表示為陣列的指標**不帶正負號****簡短**。

### <a name="remarks"></a>備註

下列浮點數基本類型標準化 underflowed 的浮點值的小數部分，並調整*特性*，或比對的偏誤的指數。 值會傳遞為位元的浮點數轉換為陣列的型別表示**不帶正負號****簡短**透過`_double_val`， `_ldouble_val`，或`_float_val`類型punning 等位宣告於 math.h 中。 傳回值是結果**fpclassify**輸入浮點數的值是否為 NaN 或無限大，以及輸出值，否則為。

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly _ldpoly _fdpoly

### <a name="syntax"></a>語法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函式引數。

*table*<br/>
多項式次方的常數係數資料表指標。

*n*<br/>
多項式次方的評估的順序。

### <a name="remarks"></a>備註

下列浮點數基本類型傳回的評估*x*中的順序多項式*n*的係數都由在對應的常數值*資料表*. 比方說，如果*資料表*\[0] = 3.0*資料表*\[1] = 4.0、windows*資料表*\[2] = 5.0 版，和*n*= 2，它代表多項式 5.0 x<sup>2</sup> + 4.0 x + 3.0。 如果用於評估此多項式次方*x*的 2.0 時，結果會是 31.0。 這些函式不會在內部使用。

## <a name="dlog-dlog-dlog"></a>_dlog _dlog _dlog

### <a name="syntax"></a>語法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函式引數。

*base_flag*<br/>
控制要使用，0 為基底的基底的旗標*e*且非零為基底為 10。

### <a name="remarks"></a>備註

下列浮點數基本類型傳回的自然對數*x*，ln (*x*) 或記錄檔<sub>*電子*</sub>(*x*)，當*base_flag*為 0。 它們會傳回記錄檔的基底 10 *x*，或記錄檔<sub>10</sub>(*x*)，當*base_flag*為非零。 這些函式不會在內部使用。 可攜性，偏好使用函式[記錄檔、 logf、 logl、 log10、 log10f 和 log10l](log-logf-log10-log10f.md)。

## <a name="dsin-ldsin-fdsin"></a>_dsin _ldsin _fdsin

### <a name="syntax"></a>語法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點函式引數。

*quadrant*<br/>
0、 1、 2 或 3，以使用產生的四分色方塊位移`sin`， `cos`， `-sin`，和`-cos`結果。

### <a name="remarks"></a>備註

下列浮點數基本類型傳回的正弦*x*位移所*象限*取 4 的模數。 實際上，它們會傳回正弦、 餘弦函數、 正弦、 和-的餘弦函數*x*時*象限*取 4 的模數是 0、 1、 2 或 3，分別。 這些函式不會在內部使用。 對於可攜性，想[sin、 sinf、 sinl](sin-sinf-sinl.md)， [cos、 cosf、 cosl 和](cos-cosf-cosl.md)函式。

## <a name="requirements"></a>需求

標頭： \<math.h> >

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite _finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、 ldexpf、 和 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
