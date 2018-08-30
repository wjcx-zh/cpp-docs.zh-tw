---
title: underflow_error 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::underflow_error
dev_langs:
- C++
helpviewer_keywords:
- underflow_error class
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4d5dcf640e46bfb3a0ac6e9b29dbaff36f4b868
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204403"
---
# <a name="underflowerror-class"></a>underflow_error 類別

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告算術反向溢位。

## <a name="syntax"></a>語法

```cpp
class underflow_error : public runtime_error {
public:
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};
```

## <a name="remarks"></a>備註

[what](../standard-library/exception-class.md) 所傳回的值為 **message**`.`[data](../standard-library/basic-string-class.md#data) 的複本。

## <a name="example"></a>範例

```cpp
// underflow_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      throw underflow_error( "The number's a bit small, captain!" );
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
\* Output:
Caught: The number's a bit small, captain!
Type: class std::underflow_error
*\
```

## <a name="requirements"></a>需求

**標頭：**\<stdexcept>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<stdexcept> > 成員](https://msdn.microsoft.com/7b6b0a73-916e-44aa-9a3f-f5b6b3ce98e6)<br/>
[runtime_error 類別](../standard-library/runtime-error-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
