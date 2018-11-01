---
title: money_base 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: b0c77b523dbe31bc5b07ae3d736441880fe04546
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610441"
---
# <a name="moneybase-class"></a>money_base 類別

此類別描述範本類別 [moneypunct](../standard-library/moneypunct-class.md) 之所有特製化通用的列舉和結構。

## <a name="syntax"></a>語法

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>備註

列舉型別`part`描述結構模式中陣列欄位的項目中的可能值。 值`part`是：

- `none` 若要比對零或多個空格，或產生任何項目。

- `sign` 若要比對或產生正負號。

- `space` 若要比對零或多個空格，或是產生空格。

- `symbol` 若要比對或產生貨幣符號。

- `value` 若要比對或產生貨幣值。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
