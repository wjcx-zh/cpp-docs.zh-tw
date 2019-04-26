---
title: __interface
ms.date: 11/04/2016
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 1ec3a1d2cddbf8dbbb248a7366d5d56dd95ad074
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166291"
---
# <a name="interface"></a>__interface

**Microsoft 專屬**

Visual C++ 介面可定義為如下：

- 能夠繼承自零個或多個基底介面。

- 不能繼承自基底類別。

- 只能包含公用的純虛擬方法。

- 不能包含建構函式、解構函式或運算子。

- 不能包含靜態方法。

- 不能包含資料成員；可以使用屬性。

## <a name="syntax"></a>語法

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>備註

C++ [類別](../cpp/class-cpp.md)或[結構](../cpp/struct-cpp.md)可能會實作這些規則，但 **__interface**強制執行它們。

例如，以下是介面定義範例：

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

如需 managed 介面的資訊，請參閱[介面類別](../extensions/interface-class-cpp-component-extensions.md)。

請注意，您不需要明確表明 `CommitX` 和 `get_X` 函式是純虛擬函式。 第一個函式的同等宣告如下：

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface**意味著[novtable](../cpp/novtable.md) **__declspec**修飾詞。

## <a name="example"></a>範例

下列範例示範如何使用在介面中宣告的屬性。

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[介面屬性](../windows/attributes/interface-attributes.md)