---
title: enable_shared_from_this 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bc34a0a176e39a30e6cdb5d4c2cdeeebc94b5b1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845748"
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this 類別

幫助產生 `shared_ptr`。

## <a name="syntax"></a>語法

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>參數

`Ty` 共用指標所控制的類型。

## <a name="remarks"></a>備註

衍生自 `enable_shared_from_this` 的物件可以使用成員函式中的 `shared_from_this` 方法，來建立執行個體的 [shared_ptr](../standard-library/shared-ptr-class.md) 擁有者，其與現有 `shared_ptr` 擁有者共用擁有權。 否則，如果您使用 `this` 建立新的 `shared_ptr`，它與現有 `shared_ptr` 擁有者不同，可能會導致參考無效，或物件遭到重複刪除。

建構函式、解構函式和指派運算子會受到保護以防止意外誤用。 範本引數類型 `Ty` 必須是衍生類別的類型。

如需使用方式的範例，請參閱 [enable_shared_from_this::shared_from_this](#shared_from_this)。

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

產生的 `shared_ptr` 會與現有的 `shared_ptr` 擁有者共用執行個體擁有權。

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>備註

當您從 `enable_shared_from_this` 基底類別衍生物件時，`shared_from_this` 範本成員函式會傳回 [shared_ptr 類別](../standard-library/shared-ptr-class.md)物件，其與現有的 `shared_ptr` 擁有者共用此執行個體的擁有權。 否則，如果您從 `this` 建立新的 `shared_ptr`，它與現有 `shared_ptr` 擁有者不同，可能會導致參考無效，或物件遭到重複刪除。 如果 `shared_ptr` 物件不再擁有某個執行個體，而您呼叫其中的 `shared_from_this`，則行為是未定義的。

### <a name="example"></a>範例

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="see-also"></a>另請參閱

[enable_shared_from_this::shared_from_this](#shared_from_this)<br/>
[shared_ptr 類別](../standard-library/shared-ptr-class.md)<br/>