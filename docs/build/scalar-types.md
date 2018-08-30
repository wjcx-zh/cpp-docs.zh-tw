---
title: 純量類型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6af598ec6e27138f4e666007018ce803177697b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211137"
---
# <a name="scalar-types"></a>純量類型
雖然資料的存取權可以出自於任何對齊方式，建議您使用資料對齊自然界限，以避免效能損失 （或多個類別）。 列舉常數的整數，並會被視為 32 位元整數。 下表描述的型別定義和建議的儲存體，因為它適用於使用下列的對齊值的對齊方式：  
  
-   8 位元位元組  
  
-   Word-16 位元  
  
-   雙字組為 32 位元  
  
-   四啼聲-64 位元  
  
-   顆 Octa 啼聲-128 位元  
  
|||||  
|-|-|-|-|  
|純量類型|C 資料類型|儲存體大小 （以位元組為單位）|建議的對齊方式|  
|**INT8**|**char**|1|Byte|  
|**UINT8**|**unsigned char**|1|Byte|  
|**INT16**|**short**|2|字組|  
|**UINT16**|**unsigned short**|2|字組|  
|**INT32**|**int**，**長**|4|Doubleword|  
|**UINT32**|**不帶正負號的 int、 unsigned long**|4|Doubleword|  
|**INT64**|**__int64**|8|Quadword|  
|**UINT64**|**unsigned __int64**|8|Quadword|  
|**FP32 （單精確度）**|**float**|4|Doubleword|  
|**FP64 （雙精確度）**|**double**|8|Quadword|  
|**指標**|<strong>\*</strong>|8|Quadword|  
|**__m64**|**結構 __m64**|8|Quadword|  
|**__m128**|**結構 __m128**|16|Octaword|  
  
## <a name="see-also"></a>另請參閱  
 [類型和儲存區](../build/types-and-storage.md)