---
title: bad_weak_ptr 類別
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: e1d536eed6727a5d1e828d358aa6b64521d748b8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454260"
---
# <a name="badweakptr-class"></a>bad_weak_ptr 類別

報告錯誤 weak_ptr 例外狀況。

## <a name="syntax"></a>語法

```cpp
class bad_weak_ptr : public std::exception
{
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>備註

這個類別描述來自接受 [weak_ptr 類別](../standard-library/weak-ptr-class.md)類型引數的 [shared_ptr 類別](../standard-library/shared-ptr-class.md)建構函式可能擲回的例外狀況。 成員函式 `what` 會傳回 `"bad_weak_ptr"`。

## <a name="example"></a>範例

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="see-also"></a>另請參閱

[weak_ptr 類別](../standard-library/weak-ptr-class.md)
