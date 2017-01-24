---
title: "彙總和等位 | Microsoft Docs"
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
helpviewer_keywords: 
  - "彙總 [C++], 和等位"
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 彙總和等位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其他的型別，例如陣列、結構和等位，有較嚴格的對齊需求，確保一致的彙總和等位儲存區以及資料擷取。  此處為陣列、結構和等位的定義：  
  
 陣列  
 包含相鄰資料物件的有序群組。  每個物件稱為元素。  陣列中所有的元素具有相同的大小和資料型別。  
  
 結構  
 包含資料物件的有序群組。  與陣列的元素不同，結構中的資料物件可以有不同的資料型別和大小。  結構中每個資料物件稱為成員。  
  
 Union  
 含有一組具名成員中任何一個成員的物件。  具名集合的成員可以為任何型別。  為等位所配置的儲存區，等於等位中最大的成員所需之儲存區，再加上對齊所需的填補。  
  
 下表顯示強烈建議的等位和結構之純量成員的對齊。  
  
||||  
|-|-|-|  
|純量型別|C 資料型別|必要的對齊|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Word|  
|**UINT16**|**unsigned short**|Word|  
|**INT32**|**int, long**|Doubleword|  
|**UINT32**|**unsigned int, unsigned long**|Doubleword|  
|**INT64**|`__int64`|Quadword|  
|**UINT64**|**unsigned \_\_int64**|Quadword|  
|**FP32 \(單精度\)**|**float**|Doubleword|  
|**FP64 \(雙精度\)**|**double**|Quadword|  
|**POINTER**|**\***|Quadword|  
|`__m64`|**struct \_\_m64**|Quadword|  
|`__m128`|**struct \_\_m128**|Octaword|  
  
 下列為適用的彙總對齊規則：  
  
-   陣列的對齊和陣列中單一元素的對齊相同。  
  
-   結構或等位開頭的對齊，是所有個別成員的對齊之最大者。  結構或等位中的每個成員必須放置在其適當的對齊上 \(如上列表格所定義\)，此對齊可能需要隱含的內部填補 \(視前一個成員而定\)。  
  
-   結構的大小必須是其對齊的整數倍數，這可能需要在最後一個成員之後填補。  因為結構和等位可以群集在陣列中，所以陣列的每個結構或等位元素必須在如上所述的適當對齊上開始和結束。  
  
-   只要上述規則成立，就可能會以大於對齊需求的方式來對齊資料。  
  
-   不同的編譯器 \(Compiler\) 可能會基於大小的考量而調整結構的封裝。  例如 [\/Zp \(結構成員對齊\)](../build/reference/zp-struct-member-alignment.md) 允許調整結構的封裝。  
  
## 請參閱  
 [類型和儲存區](../build/types-and-storage.md)