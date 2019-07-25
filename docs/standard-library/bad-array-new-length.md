---
title: bad_array_new_length 類別
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459494"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length 類別

類別描述擲回的例外狀況, 指出由於陣列大小小於零或大於其限制, 配置要求未成功。

## <a name="syntax"></a>語法

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>備註

所傳回的值`what`是由實作為定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。

## <a name="requirements"></a>需求

**標頭：** \<new>

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
