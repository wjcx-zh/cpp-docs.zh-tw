---
title: 函式樣板呼叫的多載解析
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: d96046c629e812e342ce86b850b6d52a57094997
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188437"
---
# <a name="overload-resolution-of-function-template-calls"></a>函式樣板呼叫的多載解析

函式樣板可以多載相同名稱的非樣板函式。 在這種情節中，函式呼叫會先使用樣板引數推算解析，以具現化具有唯一特製化的函式樣板。 如果樣板引數推算失敗，才會考慮使用其他函式多載解析呼叫。 這些其他多載也稱為候選集合，包括非樣板函式和其他具現化的函式樣板。 如果樣板引數推算成功，則會依照多載解析的規則將產生的函式與其他函式進行比較，以判斷最符合的項目。 如需詳細資訊，請參閱[函數](function-overloading.md)多載。

## <a name="example"></a>範例

如果非樣板函式是與樣板函式一樣理想的相符項目，則會選擇非樣板函式 (除非明確指定樣板引數)，如同下列範例中的呼叫 `f(1, 1)`。

```cpp
// template_name_resolution9.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }
void f(char, char) { cout << "f(char, char)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   f(1, 1);   // Equally good match; choose the nontemplate function.
   f('a', 1); // Chooses the template function.
   f<int, int>(2, 2);  // Template arguments explicitly specified.
}
```

```Output
f(int, int)
void f(T1, T2)
void f(T1, T2)
```

## <a name="example"></a>範例

下一個範例將說明，如果非樣板函式需要轉換，則建議您使用完全相符的樣板函式。

```cpp
// template_name_resolution10.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   long l = 0;
   int i = 0;
   // Call the template function f(long, int) because f(int, int)
   // would require a conversion from long to int.
   f(l, i);
}
```

```Output
void f(T1, T2)
```

## <a name="see-also"></a>另請參閱

[名稱解析](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)
