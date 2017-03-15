---
title: "浮點數限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FLOAT.H 標頭檔"
  - "浮點常數, 限制"
  - "浮點數, 浮點限制"
  - "限制, 浮點常數"
  - "範圍, 浮點常數"
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 浮點數限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 下表列出浮點常數值的限制。  標準標頭檔 FLOAT.H 中也會定義這些限制。  
  
### 浮點常數的限制  
  
|常數|意義|值|  
|--------|--------|-------|  
|FLT\_DIG DBL\_DIG LDBL\_DIG|位數 q，使得有 q 個小數位數的浮點數可以捨入為浮點表示 \(反向亦然\)，而不會失去精確度。|6 15 15|  
|FLT\_EPSILON DBL\_EPSILON LDBL\_EPSILON|最小正數 x，使得 x \+ 1.0 不會等於 1.0。|1.192092896e–07F 2.2204460492503131e–016 2.2204460492503131e–016|  
|FLT\_GUARD||0|  
|FLT\_MANT\_DIG DBL\_MANT\_DIG LDBL\_MANT\_DIG|基數中以浮點數有效數字的 FLT\_RADIX 指定的位數。  基數為 2，因此這些值會指定位元。|24 53 53|  
|FLT\_MAX DBL\_MAX LDBL\_MAX|可顯示的最大浮點數。|3.402823466e\+38F 1.7976931348623158e\+308 1.7976931348623158e\+308|  
|FLT\_MAX\_10\_EXP DBL\_MAX\_10\_EXP LDBL\_MAX\_10\_EXP|最大整數，使得增加至該數字的 10 會是可顯示的浮點數。|38 308 308|  
|FLT\_MAX\_EXP DBL\_MAX\_EXP LDBL\_MAX\_EXP|最大整數，使得增加至該數字的 FLT\_RADIX 會是可顯示的浮點數。|128 1024 1024|  
|FLT\_MIN DBL\_MIN LDBL\_MIN|最小正值。|1.175494351e–38F 2.2250738585072014e–308 2.2250738585072014e–308|  
|FLT\_MIN\_10\_EXP DBL\_MIN\_10\_EXP LDBL\_MIN\_10\_EXP|最小負整數，使得增加至該數字的 10 會是可顯示的浮點數。|–37<br /><br /> –307<br /><br /> –307|  
|FLT\_MIN\_EXP DBL\_MIN\_EXP LDBL\_MIN\_EXP|最小負整數，使得增加至該數字的 FLT\_RADIX 會是可顯示的浮點數。|–125<br /><br /> –1021<br /><br /> –1021|  
|FLT\_NORMALIZE||0|  
|FLT\_RADIX \_DBL\_RADIX \_LDBL\_RADIX|指數表示的基數。|2 2 2|  
|FLT\_ROUNDS \_DBL\_ROUNDS \_LDBL\_ROUNDS|浮點加法的捨入模式。|1 \(near\) 1 \(near\) 1 \(near\)|  
  
> [!NOTE]
>  上表中的資訊在未來的產品版本中可能有所不同。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [整數限制](../cpp/integer-limits.md)