---
title: runtime_error 類別
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: a860e10994934ae0e97950fddb14e573f8752833
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520897"
---
# <a name="runtime_error-class"></a>runtime_error 類別

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告僅當程式執行時假定可偵測的錯誤。

## <a name="syntax"></a>語法

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>備註

所傳回的值 `what()` 是的複本 `message.data()` 。 如需詳細資訊，請參閱 [`what`](../standard-library/exception-class.md) 和 [`data`](../standard-library/basic-string-class.md#data) 。

## <a name="example"></a>範例

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>需求

**標頭：**\<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
