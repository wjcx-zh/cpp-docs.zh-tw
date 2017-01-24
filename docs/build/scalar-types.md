---
title: "純量類型 | Microsoft Docs"
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
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 純量類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雖然資料的存取可能起源於任何記憶體對齊 \(Alignment\)，但是建議您將資料對齊自然界限，以避免發生效能低落 \(或產生多重對齊的情形\)。  列舉是常數整數，會被視為 32 位元整數。  下表描述型別定義和建議的儲存區，它適用於使用下列對齊值的記憶體對齊：  
  
-   Byte – 8 位元  
  
-   Word – 16 位元  
  
-   Double Word – 32 位元  
  
-   Quad Word – 64 位元  
  
-   Octa Word – 128 位元  
  
|||||  
|-|-|-|-|  
|純量型別|C 資料型別|儲存區大小 \(以位元組為單位\)|建議的對齊方式|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**short**|2|Word|  
|**UINT16**|**unsigned short**|2|Word|  
|**INT32**|**int, long**|4|Doubleword|  
|**UINT32**|**unsigned int, unsigned long**|4|Doubleword|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64**|**unsigned \_\_int64**|8|Quadword|  
|**FP32 \(單精度\)**|**float**|4|Doubleword|  
|**FP64 \(雙精度\)**|**double**|8|Quadword|  
|**POINTER**|**\***|8|Quadword|  
|`__m64`|**struct \_\_m64**|8|Quadword|  
|`__m128`|**struct \_\_m128**|16|Octaword|  
  
## 請參閱  
 [類型和儲存區](../build/types-and-storage.md)