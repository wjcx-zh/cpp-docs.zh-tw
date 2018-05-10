---
title: unchecked_array_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdext::unchecked_array_iterator
dev_langs:
- C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a483d1509ce14a9192c237c5475ec9b8e65d24e6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator 類別

`unchecked_array_iterator` 類別可讓您將陣列或指標包裝在未檢查的迭代器中。 使用這個類別做為原始指標或陣列的包裝函式 (使用 [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) 函式)，做為管理未檢查指標警告的目標方式，而非全域的關閉這些警告訊息。 如果可能，請優先使用這個類別的已檢查版本 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。

> [!NOTE]
> 這個類別是 C++ 標準程式庫的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。

## <a name="syntax"></a>語法

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>備註

這個類別是在 [stdext](../standard-library/stdext-namespace.md) 命名空間中定義的。

這是 [checked_array_iterator 類別](../standard-library/checked-array-iterator-class.md)的未檢查版本，並支援所有相同的多載和成員。 如需已檢查的迭代器功能的詳細資訊和程式碼範例，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
