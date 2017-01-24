---
title: "整數限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "整數限制"
  - "整數限制"
  - "限制, 整數"
  - "LIMITS.H 標頭檔"
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 整數限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 下表列出整數類型的限制。  這些限制也在標準標頭檔 LIMITS.H 中定義。  
  
### 整數常數的限制  
  
|常數|意義|值|  
|--------|--------|-------|  
|**CHAR\_BIT**|不是位元欄位之最小變數中的位元數目。|8|  
|**SCHAR\_MIN**|變數類型為 **signed char** 的最小值。|–128|  
|**SCHAR\_MAX**|變數類型為 **signed char** 的最大值。|127|  
|**UCHAR\_MAX**|變數類型為 `unsigned char` 的最大值。|255 \(0xff\)|  
|**CHAR\_MIN**|變數類型為 `char` 的最小值。|–128，如果使用 \/J 選項則為 0|  
|**CHAR\_MAX**|變數類型為 `char` 的最大值。|127，如果使用 \/J 選項則為 255|  
|**MB\_LEN\_MAX**|多重字元常數中位元組數目的上限。|5|  
|**SHRT\_MIN**|變數類型為 **short** 的最小值。|–32768|  
|**SHRT\_MAX**|變數類型為 **short** 的最大值。|32767|  
|**USHRT\_MAX**|變數類型為 **unsigned short** 的最大值。|65535 \(0xffff\)|  
|**INT\_MIN**|變數類型為 `int` 的最小值。|–2147483648|  
|**INT\_MAX**|變數類型為 `int` 的最大值。|2147483647|  
|**UINT\_MAX**|變數類型為 `unsigned int` 的最大值。|4294967295 \(0xffffffff\)|  
|**LONG\_MIN**|變數類型為 **long** 的最小值。|–2147483648|  
|**LONG\_MAX**|變數類型為 **long** 的最大值。|2147483647|  
|**ULONG\_MAX**|變數類型為 `unsigned long` 的最大值。|4294967295 \(0xffffffff\)|  
|**\_I64\_MIN**|變數類型為 `__int64` 的最小值|\-9223372036854775808|  
|**\_I64\_MAX**|變數類型為 `__int64` 的最大值|9223372036854775807|  
|**\_UI64\_MAX**|變數類型為 **unsigned \_\_int64** 的最大值|18446744073709551615 \(0xffffffffffffffff\)|  
  
 如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [浮點數限制](../cpp/floating-limits.md)