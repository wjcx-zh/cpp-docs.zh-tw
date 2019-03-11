---
title: 使用者定義的運算子 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: 462d0d2819d4c65b0e37d39f24566a7152a44cf3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739992"
---
# <a name="user-defined-operators-ccli"></a>使用者定義的運算子 (C++/CLI)

Managed 類型的使用者定義運算子允許為靜態成員或是執行個體成員，或位於全域範圍。 不過，不是以 Visual C++ 語言撰寫的程式中，只有靜態運算子可以透過用戶端的中繼資料可取得。

在參考類型中，其中一個靜態使用者定義運算子的參數必須是下列其中一個：

- 封入類型的執行個體之控制代碼 (`type` ^)。

- 對封入類型之執行個體的控制代碼進行參考類型的間接取值 (`type`^& 或 type^%)。

在實值類型中，其中一個靜態使用者定義運算子的參數必須是下列其中一個：

- 與封入實值類型相同的類型。

- 對封入類型的指標類型進行間接取值 (`type`^)。

- 對封入類型的參考類型進行間接取值 (`type`% 或 `type`&)。

- 對控制代碼的參考類型進行間接取值 (`type`^% 或 `type`^&)。

您可以定義下列運算子：

|運算子|一元/二元表單？|
|--------------|--------------------------|
|!|一元|
|!=|二元|
|%|二元|
|&|一元和二元|
|&&|二元|
|*|一元和二元|
|+|一元和二元|
|++|一元|
|,|二元|
|-|一元和二元|
|--|一元|
|->|一元|
|/|二元|
|<|二元|
|<<|二元|
|\<=|二元|
|=|二元|
|==|二元|
|>|二元|
|>=|二元|
|>>|二元|
|^|二元|
|False|一元|
|true|一元|
|&#124;|二元|
|&#124;&#124;|二元|
|~|一元|

## <a name="example"></a>範例

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>範例

下列範例將示範運算子合成，只有當您使用才 **/clr**編譯。 如果沒有定義任何一個二元運算子的工作表單，運算子合成會建立它，其中指派運算子左方會使用 CLR 類型。

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>另請參閱

[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)
