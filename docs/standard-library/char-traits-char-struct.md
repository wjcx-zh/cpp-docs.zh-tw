---
title: char_traits&lt;char&gt; 結構
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: ccb08f3e505122757080129b36558490456fc2c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688317"
---
# <a name="char_traitsltchargt-struct"></a>char_traits&lt;char&gt; 結構

結構，這是樣板結構 char_traits 的特製化， **\<CharType >** 至**char**類型的專案。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用程式庫函式來操作此類型**char**的物件。

## <a name="example"></a>範例

請參閱類別樣板[Char_traits 類別](../standard-library/char-traits-struct.md)的 typedef 和成員函式
