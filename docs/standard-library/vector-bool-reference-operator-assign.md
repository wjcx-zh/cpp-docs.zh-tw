---
title: vector&lt;bool&gt;::reference::operator= | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- =
- operator=
- vector<bool>::reference::operator=
- std::vector<bool>::reference::operator=
dev_langs:
- C++
helpviewer_keywords:
- = operator, with specific C++ Standard Library objects
- reference::operator=
ms.assetid: eed20d81-36b9-40b2-a3b6-340ed0bb4f34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eddd4ce677adfb51192302357dfbd72be36df3c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721496"
---
# <a name="vectorltboolgtreferenceoperator"></a>vector&lt;bool&gt;::reference::operator=

將布林值指派給位元，或是將參考的項目所表示的值指派給位元。

## <a name="syntax"></a>語法

```cpp
reference& operator=(const reference& Right);

reference& operator=(bool Val);
```

### <a name="parameters"></a>參數

*右邊*<br/>
值會指派給位元的項目參考。

*val*<br/>
要指派給位元的布林值。

## <a name="example"></a>範例

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}

```

## <a name="output"></a>輸出

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="requirements"></a>需求

**標頭：** \<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[向量\<bool >:: reference 類別](../standard-library/vector-bool-reference-class.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
