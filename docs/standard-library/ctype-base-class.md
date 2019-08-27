---
title: ctype_base 類別
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: f23b9528cf9a921e1d005756aa82751f3fdb745e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449352"
---
# <a name="ctypebase-class"></a>ctype_base 類別

此類別可作為 [ctype](../standard-library/ctype-class.md) 範本類別 Facet 的基底類別。 ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。

## <a name="syntax"></a>語法

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>備註

此項目可定義列舉遮罩。 每個列舉常數皆描述不同字元分類方式的特性，如 \<ctype.h> 標頭中宣告之類似名稱的函式所定義。 這些常數如下：

- **space** (函式 [isspace](../standard-library/locale-functions.md#isspace))

- **print** (函式 [isprint](../standard-library/locale-functions.md#isprint))

- **cntrl** (函式 [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **upper** (函式 [isupper](../standard-library/locale-functions.md#isupper))

- **lower** (函式 [islower](../standard-library/locale-functions.md#islower))

- **digit** (函式 [isdigit](../standard-library/locale-functions.md#isdigit))

- **punct** (函式 [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (函式 [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alpha** (函式 [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (函式 [isalnum](../standard-library/locale-functions.md#isalnum))

- **graph** (函式 [isgraph](../standard-library/locale-functions.md#isgraph))

您可以搭配使用 OR 與這些常數來描述分類的組合。 特別是, **alnum** = = ( **Alpha** &#124; **數位**\)和**graph** \= \= \(  alnum &#124; **punct**) 一律為 true。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
