---
title: "資料類型常數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FLT_MIN"
  - "SHRT_MAX"
  - "CHAR_MIN"
  - "MB_LEN_MAX"
  - "DBL_EPSILON"
  - "SHRT_MIN"
  - "_FLT_RADIX"
  - "FLT_DIG"
  - "FLT_MAX_10_EXP"
  - "FLT_MANT_DIG"
  - "DBL_MAX_EXP"
  - "SCHAR_MIN"
  - "SCHAR_MAX"
  - "DBL_MIN"
  - "FLT_MIN_10_EXP"
  - "_DBL_ROUNDS"
  - "USHRT_MAX"
  - "FLT_MAX_EXP"
  - "LONG_MAX"
  - "DBL_MAX"
  - "DBL_DIG"
  - "FLT_MIN_EXP"
  - "INT_MIN"
  - "DBL_MIN_10_EXP"
  - "CHAR_BIT"
  - "INT_MAX"
  - "ULONG_MAX"
  - "DBL_MIN_EXP"
  - "LONG_MIN"
  - "_FLT_ROUNDS"
  - "DBL_MANT_DIG"
  - "_DBL_RADIX"
  - "CHAR_MAX"
  - "FLT_MAX"
  - "DBL_MAX_10_EXP"
  - "UCHAR_MAX"
  - "FLT_EPSILON"
  - "UINT_MAX"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_DBL_RADIX 常數"
  - "_DBL_ROUNDS 常數"
  - "_FLT_RADIX 常數"
  - "_FLT_ROUNDS 常數"
  - "CHAR_BIT 常數"
  - "CHAR_MAX 常數"
  - "CHAR_MIN 常數"
  - "常數 [C++], 資料類型"
  - "資料類型常數 [C++]"
  - "DBL_DIG 常數"
  - "DBL_EPSILON 常數"
  - "DBL_MANT_DIG 常數"
  - "DBL_MAX 常數"
  - "DBL_MAX_10_EXP 常數"
  - "DBL_MAX_EXP 常數"
  - "DBL_MIN 常數"
  - "DBL_MIN_10_EXP 常數"
  - "DBL_MIN_EXP 常數"
  - "DBL_RADIX 常數"
  - "DBL_ROUNDS 常數"
  - "FLT_DIG 常數"
  - "FLT_EPSILON 常數"
  - "FLT_MANT_DIG 常數"
  - "FLT_MAX 常數"
  - "FLT_MAX_10_EXP 常數"
  - "FLT_MAX_EXP 常數"
  - "FLT_MIN 常數"
  - "FLT_MIN_10_EXP 常數"
  - "FLT_MIN_EXP 常數"
  - "FLT_RADIX 常數"
  - "FLT_ROUNDS 常數"
  - "INT_MAX 常數"
  - "INT_MIN 常數"
  - "LONG_MAX 常數"
  - "LONG_MIN 常數"
  - "MB_LEN_MAX 常數"
  - "SCHAR_MAX 常數"
  - "SCHAR_MIN 常數"
  - "SHRT_MAX 常數"
  - "SHRT_MIN 常數"
  - "UCHAR_MAX 常數"
  - "UINT_MAX 常數"
  - "ULONG_MAX 常數"
  - "USHRT_MAX 常數"
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資料類型常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料型別的常數是整數資料型別所允許的值的實作相關範圍。  下面列出的常數，LIMITS.H. 給整數資料型別的範圍和定義。  
  
> [!NOTE]
>  \/J 編譯器選項將預設值從 `char` 型別改變為`unsigned`。  
  
|常數|值|意義|  
|--------|-------|--------|  
|**SCHAR\_MAX**|127|最大值簽署的 `char` 值。|  
|**SCHAR\_MIN**|–128|最小簽署的 `char` 值。|  
|**UCHAR\_MAX**|255 \(0xff\)|最大`unsigned char`值|  
|**CHAR\_BIT**|8|位元數的 `char`。|  
|**USHRT\_MAX**|65535 \(0xffff\)|最大 **unsigned short** 值|  
|**SHRT\_MAX**|32767|最大 \(帶正負號\) **short** 值|  
|**SHRT\_MIN**|–32768|最小 \(帶正負號\) **short** 值|  
|**UINT\_MAX**|4294967295 \(0xffffffff\)|最大`unsigned int`值|  
|**ULONG\_MAX**|4294967295 \(0xffffffff\)|最大`unsigned long`值|  
|**INT\_MAX**|2147483647|最大\(簽署的\) `int` 值。|  
|**INT\_MIN**|–2147483647–1|最小\(簽署的\) `int` 值。|  
|**LONG\_MAX**|2147483647|最大 \(帶正負號\) **long** 值|  
|**LONG\_MIN**|–2147483647–1|最小 \(帶正負號\) **long** 值|  
|**CHAR\_MAX**|127\(如果使用 \/J 選項則為 255\)|最大`char`值|  
|**CHAR\_MIN**|–128\(如果使用 \/J 選項則為 0\)|最小`char`值|  
|**MB\_LEN\_MAX**|2|最大位元組數目多位元組的 `char`|  
|**\_I64\_MAX**|9223372036854775807|最大 \(帶正負號\)\_**int64** 值|  
|**\_I64\_MIN**|\-9223372036854775807\-1|最小 \(帶正負號\)\_**int64** 值|  
|**\_UI64\_MAX**|0xffffffffffffffff|最大 \(不帶正負號\)\_**int64**值|  
  
 下列常數在 FLOAT.H 給範圍和 **double** 和 **float** 資料型別的其他特性和定義:  
  
|常數|值|說明|  
|--------|-------|--------|  
|**DBL\_DIG**|15|\# 整數位數十進位數字。|  
|**DBL\_EPSILON**|2.2204460492503131e\-016|最小這類 1.0\+**DBL\_EPSILON** \! \=1.0|  
|**DBL\_MANT\_DIG**|53|\# 在小數的位元|  
|**DBL\_MAX**|1.7976931348623158e\+308|最大值|  
|**DBL\_MAX\_10\_EXP**|308|最大十進位的指數。|  
|**DBL\_MAX\_EXP**|1024|最大二進位指數|  
|**DBL\_MIN**|2.2250738585072014e\-308|最小正值|  
|**DBL\_MIN\_10\_EXP**|\(\-307\)|最小十進位的指數。|  
|**DBL\_MIN\_EXP**|\(–1021\)|最小的二進位指數|  
|**\_DBL\_RADIX**|2|指數基數|  
|**\_DBL\_ROUNDS**|1|加入捨入:在周圍|  
|**FLT\_DIG**|6|十進位數的精準度|  
|**FLT\_EPSILON**|1.192092896e\-07F|最小這類 1.0\+**FLT\_EPSILON** \! \=1.0|  
|**FLT\_MANT\_DIG**|24|位元數目的尾數|  
|**FLT\_MAX**|3.402823466e\+38F|最大值|  
|**FLT\_MAX\_10\_EXP**|38|最大十進位的指數。|  
|**FLT\_MAX\_EXP**|128|最大二進位指數|  
|**FLT\_MIN**|1.175494351e\-38F|最小正值|  
|**FLT\_MIN\_10\_EXP**|\(–37\)|最小十進位的指數。|  
|**FLT\_MIN\_EXP**|\(–125\)|最小的二進位指數|  
|**FLT\_RADIX**|2|指數基數|  
|**FLT\_ROUNDS**|1|加入捨入:在周圍|  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)