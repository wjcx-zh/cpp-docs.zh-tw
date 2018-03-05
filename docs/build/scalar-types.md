---
title: "純量類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15b0915637025e176ee98d01be3991b30b4e6544
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="scalar-types"></a>純量類型
雖然資料的存取權可以源自任何對齊，建議您使用資料對齊自然界限，以避免發生效能損失 （或多個類別） 上。 列舉常數的整數，而且會被視為 32 位元整數。 下表描述的型別定義和建議的儲存體，因為它適用於使用下列的對齊值：  
  
-   位元組-8 位元  
  
-   Word-16 位元  
  
-   雙字組的 32 位元  
  
-   四 Word-64 位元  
  
-   Octa Word-128 位元  
  
|||||  
|-|-|-|-|  
|純量型別|C 資料類型|儲存體大小 （以位元組為單位）|建議的對齊方式|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**short**|2|字組|  
|**UINT16**|**unsigned short**|2|字組|  
|**INT32**|**int、 long**|4|Doubleword|  
|**UINT32**|**不帶正負號的 int、 unsigned long**|4|Doubleword|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64**|**unsigned __int64**|8|Quadword|  
|**FP32 （單一有效位數）**|**float**|4|Doubleword|  
|**FP64 （雙精確度）**|**double**|8|Quadword|  
|**指標**|**\***|8|Quadword|  
|`__m64`|**結構 __m64**|8|Quadword|  
|`__m128`|**結構 __m128**|16|Octaword|  
  
## <a name="see-also"></a>請參閱  
 [類型和儲存區](../build/types-and-storage.md)