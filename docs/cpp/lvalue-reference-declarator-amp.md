---
title: 左值參考宣告子： &amp;
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 595f2b683d2abb4cdc8a328dc6e86338ab90f214
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178063"
---
# <a name="lvalue-reference-declarator-amp"></a>左值參考宣告子： &amp;

保存物件的位址，但語法上的行為與物件相似。

## <a name="syntax"></a>語法

```
type-id & cast-expression
```

## <a name="remarks"></a>備註

您可以將左值參考當做物件的另一個名稱。 左值參考宣告包含選擇性的指定名稱清單加上參考宣告符號。 參考必須經過初始化，而且不能變更。

只要物件的位址可以轉換為指定的指標類型，則該物件也可轉換為類似的參考類型。 例如，只要物件的位址可以轉換成 `char *` 類型，該物件也可轉換成 `char &` 類型。

請勿將參考宣告與使用[位址運算子](../cpp/address-of-operator-amp.md)混淆。 當 `&`*識別碼*前面加上類型（例如**int**或**char**）時， *identifier*會宣告為該類型的參考。 當 `&`*識別碼*的前面沒有類型時，其使用方式就是傳址運算子的用法。

## <a name="example"></a>範例

下列範例示範宣告 `Person` 物件和該物件之參考的參考宣告子。 因為 `rFriend` 是 `myFriend` 的參考，無論更新哪一個變數都會變更同一個物件。

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>另請參閱

[參考](../cpp/references-cpp.md)<br/>
[參考型別函式引數](../cpp/reference-type-function-arguments.md)<br/>
[參考型別函式傳回](../cpp/reference-type-function-returns.md)<br/>
[指標的參考](../cpp/references-to-pointers.md)
