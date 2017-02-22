---
title: "浮點支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浮點數"
  - "浮點數, 數學常式"
  - "數學常式"
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 浮點支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多 Microsoft 執行階段程式庫函式需要數學副處理器，或是隨附於編譯器的浮點程式庫對浮點的支援。  僅在需要時才會載入浮點支援函式。  
  
 當您在 `printf` 或 `scanf` 系列中的函式呼叫的格式字串中，使用浮點類型規範時，必須指定浮點值或引數清單中的浮點值指標，以告訴編譯器需要浮點支援。  
  
 如需示範如何處理浮點例外狀況的範例程式碼，請參閱 [\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)。  
  
 中間值的浮點精確度是由函式 [\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) 所控制。  根據預設，`_controlfp` 中的精確度控制會設為 53 位元 \(\_PC\_53\)。  使用 FP10.OBJ 進行連結會將預設精確度控制變更為 64 位元 \(\_PC\_64\)。  在連結器命令列上，FP10.OBJ 必須顯示在 LIBC.LIB、LIBCMT.LIB 或 MSVCRT.LIB 之前。  
  
### 浮點函式  
  
|常式|用法|.NET Framework 同等|  
|--------|--------|-----------------------|  
|[abs](../Topic/abs.md)|傳回 `int` 的絕對值|[\<caps:sentence id\="tgt14" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[acos、acosf](../c-runtime-library/reference/acos-acosf-acosl.md)|計算反餘弦|[\<caps:sentence id\="tgt17" sentenceid\="954a441495360a1fa8b0170297b2ff38" class\="tgtSentence"\>System::Math::Acos\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)|  
|[asin、asinf](../c-runtime-library/reference/asin-asinf-asinl.md)|計算反正弦|[\<caps:sentence id\="tgt20" sentenceid\="313917cde9698a0924536719f5bece25" class\="tgtSentence"\>System::Math::Asin\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.asin.aspx)|  
|[atan、atanf、atan2、atan2f](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|計算反正切|[System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx)、[System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字元字串轉換為雙精確度浮點值|[System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)、[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[Bessel 函式](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|計算 Bessel 函式 `_j0`、`_j1`、`_jn`、`_y0`、`_y1`、`_yn`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|尋找複數的絕對值|不適用。|  
|[cbrt](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|計算立方根|不適用。|  
|[ceil、ceilf](../c-runtime-library/reference/ceil-ceilf-ceill.md)|尋找整數上限|[\<caps:sentence id\="tgt39" sentenceid\="656009d71fb974368bded363746de018" class\="tgtSentence"\>System::Math::Ceiling\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ceiling.aspx)|  
|[\_chgsign、\_chgsignf、\_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|反轉雙精確度浮點值或長雙精度浮點引數的符號|不適用。|  
|[\_clear87、\_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|取得及清除浮點狀態字組|不適用。|  
|[\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md), [\_controlfp\_s](../c-runtime-library/reference/controlfp-s.md)|取得舊的浮點控制字組，並設定新的控制字組值。|不適用。|  
|[copysign、copysignf、copysignl、\_copysign、\_copysignf、\_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|以另一個符號傳回某個值|不適用。|  
|[cos、cosf、cosh、coshf](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|計算餘弦|[System::Math::Cos](https://msdn.microsoft.com/en-us/library/system.math.cos.aspx)、[System::Math::Cosh](https://msdn.microsoft.com/en-us/library/system.math.cosh.aspx)|  
|[difftime](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|計算兩個指定時間值之間的差異|[\<caps:sentence id\="tgt54" sentenceid\="5f4f365a3cd7f368db2f6ce31b797fdf" class\="tgtSentence"\>System::DateTime::Subtract\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[div](../c-runtime-library/reference/div.md)|將某個整數除以另一個整數，傳回商數及餘數。|不適用。|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md), [\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|將 `double` 轉換為指定長度的字元字串|[\<caps:sentence id\="tgt60" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[exp、expf](../c-runtime-library/reference/exp-expf.md)|計算指數函式|[\<caps:sentence id\="tgt63" sentenceid\="81a65df6ac66cdc4a4b12c2f7e555487" class\="tgtSentence"\>System::Math::Exp\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)|  
|[fabs、fabsf](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|尋找絕對值|[\<caps:sentence id\="tgt66" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md)、[\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|將 `double` 轉換為小數點後具有指定位數的字串|[\<caps:sentence id\="tgt69" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|決定指定的雙精確度浮點值是否為有限|[\<caps:sentence id\="tgt72" sentenceid\="8d081c50adeda3dde4cebab81a0b3583" class\="tgtSentence"\>System::Double::IsInfinity\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)|  
|[floor、floorf](../c-runtime-library/reference/floor-floorf-floorl.md)|尋找小於或等於引數的最大整數|[\<caps:sentence id\="tgt75" sentenceid\="609db9ab0433b647d5350d3b965d70f9" class\="tgtSentence"\>System::Math::Floor\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)|  
|[fmod、fmodf](../c-runtime-library/reference/fmod-fmodf.md)|尋找浮點餘數|[\<caps:sentence id\="tgt78" sentenceid\="127a04426267ccb17fb4b566ad56de9c" class\="tgtSentence"\>System::Math::IEEERemainder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)|  
|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|傳回包含浮點類別相關資訊的狀態字組|[System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)、[System::Double::IsNegativeInfinity](https://msdn.microsoft.com/en-us/library/system.double.isnegativeinfinity.aspx)、[System::Double::IsPositiveInfinity](https://msdn.microsoft.com/en-us/library/system.double.ispositiveinfinity.aspx)、[System::Double::IsNan](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|針對 IEEE 浮點例外狀況叫用使用者定義的設陷處理常式|不適用。|  
|[\_fpreset](../c-runtime-library/reference/fpreset.md)|重新初始化浮點數學封裝||  
|[frexp](../c-runtime-library/reference/frexp.md)|計算指數值|不適用。|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md)、[\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|將浮點值轉換為字元字串|[\<caps:sentence id\="tgt92" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[hypot、hypotf、hypotl、\_hypot、\_hypotf、\_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|計算直角三角形的弦|不適用。|  
|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|檢查不是數字 \(NaN\) 的指定雙精確度浮點值|[\<caps:sentence id\="tgt97" sentenceid\="18f7dc07d0c506c23f2f7eb89262d274" class\="tgtSentence"\>System::Double::IsNan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[labs](../misc/labs-llabs.md)|傳回 `long` 的絕對值|[\<caps:sentence id\="tgt100" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[ldexp](../c-runtime-library/reference/ldexp.md)|計算引數和 2<sup>exp</sup> \(指定的冪\) 的乘積|[\<caps:sentence id\="tgt103" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[ldiv](../c-runtime-library/reference/ldiv-lldiv.md)|將某個 `long` 整數除以另一個，並傳回商數及餘數。|不適用。|  
|[log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)|計算自然對數或底數 10 的對數。|[System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx)、[System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)|  
|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|擷取雙精確度浮點引數的指數值|不適用。|  
|[\_lrotl、\_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|將 `unsigned long int` 向左移 \(`_lrotl`\) 或向右移 \(`_lrotr`\)|不適用。|  
|[\_matherr](../c-runtime-library/reference/matherr.md)|處理數學錯誤|不適用。|  
|[\_\_max](../c-runtime-library/reference/max.md)|傳回兩個值中的較大值|[\<caps:sentence id\="tgt121" sentenceid\="6f9dcb228534c3e5b0013615b2b1d003" class\="tgtSentence"\>System::Math::Max\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)|  
|[\_\_min](../c-runtime-library/reference/min.md)|傳回兩個值中的較小值|[\<caps:sentence id\="tgt124" sentenceid\="ff471983fc666dec7ba58b17a0bf76e6" class\="tgtSentence"\>System::Math::Min\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)|  
|[modf、modff](../c-runtime-library/reference/modf-modff-modfl.md)|將引數分為整數和分數部分|不適用。|  
|[nan、nanf、nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|傳回無訊息 NaN 值|[\<caps:sentence id\="tgt129" sentenceid\="c251043405ffa73fe857c83428b58fdc" class\="tgtSentence"\>System::Double::NaN\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)|  
|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|傳回下一個可表示的鄰近項目|不適用。|  
|[pow、powf](../c-runtime-library/reference/pow-powf-powl.md)|計算與冪自乘的值|[\<caps:sentence id\="tgt135" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|根據指定的格式將資料寫入 `stdout`|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)、[System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)|  
|[rand](../c-runtime-library/reference/rand.md)、[rand\_s](../c-runtime-library/reference/rand-s.md)|取得虛擬亂數|[\<caps:sentence id\="tgt141" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[rint、rintf、rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|四捨五入至浮點格式的最接近整數|[\<caps:sentence id\="tgt143" sentenceid\="1c04aeb4aeff1752cb65adabcee29f53" class\="tgtSentence"\>System::Math::Round\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)|  
|[\_rotl、\_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|將 `unsigned int` 向左移 \(`_rotl`\) 或向右移 \(`_rotr`\)|不適用。|  
|[\_scalb](../c-runtime-library/reference/scalb.md)|將引數依 2 的冪進位|不適用。|  
|[scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|乘以 `FLT_RADIX` 的整數冪|不適用。|  
|[scanf、wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)；[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|根據指定的格式讀取 `stdin` 的資料，並將資料寫入指定的位置。|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)、[System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)|  
|[\_set\_controlfp](../c-runtime-library/reference/set-controlfp.md)|設定新的控制字組值|不適用。|  
|[sin、sinf、sinh、sinhf](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|計算正弦或雙曲正弦|[System::Math::Sin](https://msdn.microsoft.com/en-us/library/system.math.sin.aspx)、[System::Math::Sinh](https://msdn.microsoft.com/en-us/library/system.math.sinh.aspx)|  
|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|尋找平方根|[\<caps:sentence id\="tgt162" sentenceid\="1a91af0bd8c63b4be64c7a0bec8dc8c4" class\="tgtSentence"\>System::Math::Sqrt\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)|  
|[srand](../c-runtime-library/reference/srand.md)|初始化虛擬隨機數列|[\<caps:sentence id\="tgt165" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[\_status87、\_statusfp、\_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|取得浮點狀態字組|不適用。|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|將字元字串轉換為雙精確度值|[\<caps:sentence id\="tgt169" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[tan、tanf、tanh、tanhf](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|計算正切或雙曲正切|[System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)、[System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)