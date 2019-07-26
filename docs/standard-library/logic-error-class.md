---
title: logic_error 類別
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::logic_error
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
ms.openlocfilehash: 9b7c432a649b566b455109f6de1f7bcc0734ff9b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453794"
---
# <a name="logicerror-class"></a>logic_error 類別

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

[what](../standard-library/exception-class.md) 所傳回的值為 **message**`.`[data](../standard-library/basic-string-class.md#data) 的複本。

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

**標頭：** \<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
