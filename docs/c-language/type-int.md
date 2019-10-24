---
title: 類型 int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: c69d2308abe2ee3d7e6b392f5a9e78a004791501
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778365"
---
# <a name="type-int"></a>類型 int

帶正負號或不帶正負號 `int` 項目的大小是特定電腦上整數的標準大小。 例如，在 16 位元作業系統中，`int` 類型通常是 16 位元或 2 個位元組。 在 32 位元作業系統中，`int` 類型通常是 32 位元或 4 個位元組。 因此，根據目標環境而定，`int` 類型相當於 `short int` 或 **long int** 類型，而 `unsigned int` 類型相當於 **unsigned short** 或 `unsigned long` 類型。 除非另有指定，否則 `int` 類型皆表示帶正負號的值。

類型指定名稱 `int` 和 `unsigned int` (或 `unsigned`) 會定義 C 語言的某些功能 (例如，`enum` 類型)。 在這些情況下，`int` 的定義和特定實作的 unsigned int 會判斷實際儲存區。

**Microsoft 專屬**

帶正負號的整數以二補數格式表示。 最高有效位元會保存此正負號：1 為負數，0 為正數及零。 值的範圍是以[C 和C++整數限制](../c-language/cpp-integer-limits.md)提供，這是從限制中取得的。H 標頭檔。

**結束 Microsoft 專屬**

> [!NOTE]
>  int 和 unsigned int 類型指定名稱廣泛使用在 C 程式中，因為它們允許特定電腦以該電腦的最有效的方法處理整數值。 不過，由於 int 和 unsigned int 類型的大小不同，取決於特定 int 大小的程式可能無法移植至其他電腦。 若要使程式更具有可移植性，您可以使用含 sizeof 運算子的運算式 (如 [sizeof 運算子](../c-language/sizeof-operator-c.md)中所述) 而不是硬式編碼的資料大小。

## <a name="see-also"></a>請參閱

[基本類型的儲存體](../c-language/storage-of-basic-types.md)
