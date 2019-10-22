---
title: money_base 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689317"
---
# <a name="money_base-class"></a>money_base 類別

類別描述列舉，以及類別樣板[moneypunct](../standard-library/moneypunct-class.md)之所有特製化通用的結構。

## <a name="syntax"></a>語法

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>備註

列舉 `part` 描述結構模式中 [陣列] 欄位的元素中可能的值。 @No__t_0 的值如下：

- `none` 比對零或多個空格，或不產生任何內容。

- `sign` 符合或產生正號或負號。

- `space`，以符合零或多個空格或產生空格。

- `symbol` 以符合或產生貨幣符號。

- `value` 以符合或產生貨幣值。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
