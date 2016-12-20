---
title: "C++ 整數限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "整數限制"
  - "限制, 整數"
  - "限制, 整數常數"
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 整數限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 下表列出整數類型的限制。  這些限制在標準標頭檔 LIMITS.H 中定義。  Microsoft C 也允許使用可調整大小的整數變數，即大小為 8、16 或 32 位元的整數類型。  如需可調整大小整數的詳細資訊，請參閱[可調整大小的整數類型](../c-language/c-sized-integer-types.md)。  
  
### 整數常數的限制  
  
|**常數**|意義|值|  
|------------|--------|-------|  
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
|**INT\_MIN**|變數類型為 `int` 的最小值。|–2147483647 – 1|  
|**INT\_MAX**|變數類型為 `int` 的最大值。|2147483647|  
|**UINT\_MAX**|變數類型為 `unsigned int` 的最大值。|4294967295 \(0xffffffff\)|  
|**LONG\_MIN**|變數類型為 **long** 的最小值。|–2147483647 – 1|  
|**LONG\_MAX**|變數類型為 **long** 的最大值。|2147483647|  
|**ULONG\_MAX**|變數類型為 `unsigned long` 的最大值。|4294967295 \(0xffffffff\)|  
  
 如果值超過最大的整數表示，Microsoft 編譯器會產生錯誤。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C 整數常數](../c-language/c-integer-constants.md)