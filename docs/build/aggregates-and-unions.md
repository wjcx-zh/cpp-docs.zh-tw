---
title: 彙總和等位 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aac6da94a0786e5cdc2eee4d16f5927f66e0a8d5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861183"
---
# <a name="aggregates-and-unions"></a>彙總和等位

其他類型，例如陣列、 結構和等位，有更嚴格的對齊需求，以確保一致彙總和等位的儲存體和資料擷取。 以下是陣列、 結構和等位的定義：

- 陣列

   包含已排序的一整組相鄰的資料物件。 每個物件稱為項目。 在陣列中的所有元素都有相同的大小和資料類型。

- 結構

   包含已排序的一整組資料物件。 不同於陣列的元素，在結構中的資料物件可以有不同的資料類型和大小。 在結構中的每個資料物件稱為 「 成員 」。

- 聯集

   物件，持有的一組具名成員的任何一個。 命名集的成員可以是任何類型。 配置給等位的儲存體等於所需的最大的成員，該聯集，再加上所需的對齊方式填補的儲存體。

下表顯示強烈建議純量的等位和結構成員對齊。

||||
|-|-|-|
|純量類型|C 資料類型|所需的對齊方式|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|字組|
|**UINT16**|**unsigned short**|字組|
|**INT32**|**int**，**長**|Doubleword|
|**UINT32**|**不帶正負號的 int、 unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 （單精確度）**|**float**|Doubleword|
|**FP64 （雙精確度）**|**double**|Quadword|
|**指標**|<strong>\*</strong>|Quadword|
|**__m64**|**結構 __m64**|Quadword|
|**__m128**|**結構 __m128**|Octaword|

適用下列的彙總的對齊方式規則：

- 陣列的對齊方式是其中一個陣列元素的對齊方式相同。

- 開頭的結構或等位的對齊方式會是任何個別成員的最大的對齊方式。 結構或等位中的每個成員必須放在正確的對齊方式，如同上表中，這可能需要隱含內部填補字元，根據先前的成員。

- 結構的大小必須是其對齊方式，可能需要在後的最後一個成員的填補整數倍數。 由於結構和等位可以歸類為陣列、 結構或等位的每個陣列元素必須在開始與結束先前決定正確的對齊方式。

- 可以對齊的方式，只要會保留上一個規則是大於對齊需求的資料。

- 個別的編譯器可能會調整大小基於結構的封裝。 比方說[/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)是用來調整結構的封裝。

## <a name="see-also"></a>另請參閱

[類型和儲存區](../build/types-and-storage.md)
