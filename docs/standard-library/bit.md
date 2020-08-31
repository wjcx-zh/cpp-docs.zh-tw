---
title: '&lt;bit&gt;'
description: 用來存取、操作及處理個別位和位元組順序的函式。
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: 7a87071d30756714e19c971281f642ce16f09d61
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194539"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

定義函式，以存取、操作及處理個別位和位序列。

例如，有一些函數可以旋轉位、找出連續的設定或清除的位數、查看數位是否為二的整數乘冪、找出代表數位的最小位數，依此類推。

## <a name="requirements"></a>規格需求

**標頭：**\<bit>

**命名空間：** std

`/std:c++latest` 是必要項

## <a name="members"></a>成員

### <a name="types"></a>類型

| 類型 | 說明 |
|--------|----------|
| [endian](bit-enum.md) | 指定純量類型的位元組順序。 |

### <a name="functions"></a>函式

| 函式 | 說明 |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | 將物件表示從某個類型重新解譯至另一個類型。 |
|[bit_ceil](bit-functions.md#bit_ceil) | 找出兩個大於或等於某個值的最小乘冪。 |
|[bit_floor](bit-functions.md#bit_floor) | 找出兩個不大於某個值的最大整數乘冪。 |
|[bit_width](bit-functions.md#bit_width) | 找出表示值所需的最小位數。 |
|[countl_zero](bit-functions.md#countl_zero) | 從最重要的位開始計算設定為零的連續位數。 |
|[countl_one](bit-functions.md#countl_one) | 從最重要的位開始計算設定為一個的連續位數。 |
|[countr_zero](bit-functions.md#countr_zero) | 從最不重要的位算起，計算設定為零的連續位數。 |
|[countr_one](bit-functions.md#countl_one) | 從最不重要的位算起，計算設定為1的連續位數。 |
|[has_single_bit](bit-functions.md#has_single_bit) | 檢查某個值是否只有一個位設定為一個。 這和測試值是否為2的乘冪一樣。 |
|[popcount](bit-functions.md#popcount) | 計算設定為1的位數目。 |
|[rotl](bit-functions.md#rotl) | 計算位左方旋轉的結果。 |
|[rotr](bit-functions.md#rotr) | 計算位右旋轉的結果。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)