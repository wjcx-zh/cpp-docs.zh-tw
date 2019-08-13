---
title: bad_optional_access 類別
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957105"
---
# <a name="bad_optional_access-class"></a>bad_optional_access 類別

定義擲回為例外狀況的物件類型, 以報告嘗試存取不包含值之`optional`物件值的情況。

## <a name="syntax"></a>語法

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>另請參閱

[\<選擇性 >](optional.md)\
[選擇性類別](optional-class.md)
