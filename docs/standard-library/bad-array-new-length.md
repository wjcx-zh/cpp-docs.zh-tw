---
title: bad_array_new_length 類別
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 823da1555119735e9aa1c46aa4db2e3a47affdec
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268690"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length 類別

此類別描述發生的例外狀況表示配置要求不會成功由於陣列大小小於零或大於其限制。

## <a name="syntax"></a>語法

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>備註

所傳回的值`what`是一個實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。

## <a name="requirements"></a>需求

**標頭：** \<new>

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
