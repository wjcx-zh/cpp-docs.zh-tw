---
title: logic_error 類別
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::logic_error
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
ms.openlocfilehash: b94f7f4c2482f0317e37c6f4bf3618b91a175147
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521183"
---
# <a name="logic_error-class"></a>logic_error 類別

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告在程式執行前假定可偵測的錯誤，例如邏輯前置條件的違規。

## <a name="syntax"></a>語法

```cpp
class logic_error : public exception {
public:
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};
```

## <a name="remarks"></a>備註

所傳回的值 `what()` 是的複本 `message.data()` 。 如需詳細資訊，請參閱 [`what`](../standard-library/exception-class.md) 和 [`data`](../standard-library/basic-string-class.md#data) 。

## <a name="example"></a>範例

```cpp
// logic_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;

int main( )
{
   try
   {
      throw logic_error( "logic error" );
   }
   catch ( exception &e )
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
```

```Output
Caught: logic error
Type: class std::logic_error
```

## <a name="requirements"></a>需求

**標頭：**\<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
