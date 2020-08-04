---
title: domain_error 類別
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::domain_error
helpviewer_keywords:
- domain_error class
ms.assetid: a1d8245d-61c2-4d1e-973f-073bd5dd5fa3
ms.openlocfilehash: 850615f07af022aff3ed209d9142823b0f038134
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521235"
---
# <a name="domain_error-class"></a>domain_error 類別

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告網域錯誤。

## <a name="syntax"></a>語法

```cpp
class domain_error : public logic_error {
public:
    explicit domain_error(const string& message);

    explicit domain_error(const char *message);

};
```

## <a name="remarks"></a>備註

所傳回的值 `what()` 是的複本 `message.data()` 。 如需詳細資訊，請參閱 [`what`](../standard-library/exception-class.md) 和 [`data`](../standard-library/basic-string-class.md#data) 。

## <a name="example"></a>範例

```cpp
// domain_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      throw domain_error( "Your domain is in error!" );
   }
   catch (exception &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid(e).name( ) << endl;
   };
}
/* Output:
Caught: Your domain is in error!
Type: class std::domain_error
*/
```

## <a name="requirements"></a>需求

**標頭：**\<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[logic_error 類別](../standard-library/logic-error-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
