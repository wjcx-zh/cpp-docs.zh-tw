---
title: 類型 int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 2bfd9e108b36f073635c6d9e55e2299764dcb309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198862"
---
# <a name="type-int"></a>類型 int

或專案的大小 **`signed int`** **`unsigned int`** 是特定電腦上整數的標準大小。 例如，在16位作業系統中， **`int`** 類型通常是16位或2個位元組。 在32位作業系統中， **`int`** 類型通常是32位或4個位元組。 因此， **`int`** 類型相當於 **`short int`** 或 **`long int`** 型別，而且型別等同于 **`unsigned int`** **`unsigned short`** 或型別 **`unsigned long`** ，視目標環境而定。 **`int`** 除非另有指定，否則所有類型都代表帶正負號的值。

型別規範 **`int`** 和 **`unsigned int`** （或直接 **`unsigned`** ）定義 C 語言的特定功能（例如， **`enum`** 型別）。 在這些情況下， **`int`** 特定執行的和定義會 **`unsigned int`** 決定實際的儲存體。

**Microsoft 特定的**

帶正負號的整數以二補數格式表示。 最高有效位元會保存此正負號：1 為負數，0 為正數及零。 值的範圍是以[c 和 c + + 整數限制](../c-language/cpp-integer-limits.md)提供，這是從限制中取得。H 標頭檔。

**結束 Microsoft 專有**

> [!NOTE]
> **`int`** 和 **`unsigned int`** 類型規範廣泛用於 C 程式，因為它們允許特定電腦以最有效率的方式處理該電腦的整數值。 不過，由於和類型的大小 **`int`** **`unsigned int`** 不同，相依于特定大小的程式 **`int`** 可能無法移植到其他電腦。 若要讓程式更具可攜性，您可以使用運算式搭配 **`sizeof`** 運算子（[如 `sizeof` 運算子](../c-language/sizeof-operator-c.md)中所述），而不是硬式編碼的資料大小。

## <a name="see-also"></a>另請參閱

[基本類型的儲存](../c-language/storage-of-basic-types.md)
