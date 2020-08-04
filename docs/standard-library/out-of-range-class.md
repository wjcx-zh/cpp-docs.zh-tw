---
title: out_of_range 類別
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::out_of_range
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
ms.openlocfilehash: 3bbbc48aa2020782594606c6a53a34f7b937fc58
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521274"
---
# <a name="out_of_range-class"></a>out_of_range 類別

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告引數超出其有效範圍。

## <a name="syntax"></a>語法

```cpp
class out_of_range : public logic_error {
public:
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};
```

## <a name="remarks"></a>備註

所傳回的值 `what()` 是的複本 `message.data()` 。 如需詳細資訊，請參閱 [`what`](../standard-library/exception-class.md) 和 [`data`](../standard-library/basic-string-class.md#data) 。

## <a name="example"></a>範例

```cpp
// out_of_range.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

using namespace std;

int main() {
// out_of_range
   try {
      string str( "Micro" );
      string rstr( "soft" );
      str.append( rstr, 5, 3 );
      cout << str << endl;
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
   };
}
```

## <a name="output"></a>輸出

```cpp
Caught: invalid string position
```

## <a name="requirements"></a>需求

**標頭：**\<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[logic_error 類別](../standard-library/logic-error-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
