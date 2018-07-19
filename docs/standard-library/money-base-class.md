---
title: money_base 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3195d2c988abcfb2d62acb4ece957c8c5156bbd7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965684"
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
