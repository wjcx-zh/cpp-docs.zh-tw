---
title: char_traits&lt;char&gt; 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a20e9c1df241feb8dd7f16891f1e2a67068f772
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt; 結構

結構，其為類型 `char` 之元素的樣板結構 **char_traits\<CharType>** 的特製化。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此 `char` 類型物件的程式庫函式。

## <a name="example"></a>範例

請參閱樣板類別 [char_traits 類別](../standard-library/char-traits-struct.md)的 typedef 和成員函式
