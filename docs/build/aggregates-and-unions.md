---
title: "彙總和等位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74ee1bbcf1a39171b18c09274543c72e0b844748
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="aggregates-and-unions"></a>彙總和等位
其他類型，例如陣列、 結構和等位有更嚴格的對齊需求可確保一致彙總和等位的儲存體和資料擷取。 以下是陣列、 結構和等位的定義：  
  
 陣列  
 包含已排序的一整組相鄰的資料物件。 每個物件稱為項目。 在陣列中的所有項目具有相同的大小和資料類型。  
  
 結構  
 包含已排序的資料物件的群組。 不同於陣列的元素，在結構中的資料物件可以有不同的資料類型和大小。 在結構中的每個資料物件稱為 「 成員 」。  
  
 聯集  
 物件，包含一組具名任何的成員一個。 命名集的成員可以是任何類型。 配置給等位的儲存體等於該等，加上任何填補的所需對齊的最大的成員所需的儲存體。  
  
 下表顯示強烈建議純量的等位和結構成員對齊。  
  
||||  
|-|-|-|  
|純量型別|C 資料類型|所需的對齊|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|字組|  
|**UINT16**|**unsigned short**|字組|  
|**INT32**|**int、 long**|Doubleword|  
|**UINT32**|**不帶正負號的 int、 unsigned long**|Doubleword|  
|**INT64**|`__int64`|Quadword|  
|**UINT64**|**unsigned __int64**|Quadword|  
|**FP32 （單一有效位數）**|**float**|Doubleword|  
|**FP64 （雙精確度）**|**double**|Quadword|  
|**指標**|**\***|Quadword|  
|`__m64`|**結構 __m64**|Quadword|  
|`__m128`|**結構 __m128**|Octaword|  
  
 適用下列彙總的對齊方式規則：  
  
-   陣列的對齊方式是相同的對齊方式的其中一個陣列的項目。  
  
-   開頭的結構或等位的對齊方式是任何個別成員的最大的對齊方式。 每個成員結構或等位內必須放在其正確對齊上, 表中，這可能需要隱含內部的邊框距離，根據上一個成員中所定義。  
  
-   結構的大小必須是其對齊，可能需要之後的最後一個成員的填補整數倍數。 由於結構和等位可以群組在陣列中，結構或等位的每個陣列元素必須開頭，而且在先前決定適當的對齊方式結束。  
  
-   很可能對齊資料的方式，只要一個規則會維護是大於的對齊需求。  
  
-   個別的編譯器可能會調整大小基於結構的封裝。 例如[/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)允許調整結構的封裝。  
  
## <a name="see-also"></a>請參閱  
 [類型和儲存區](../build/types-and-storage.md)