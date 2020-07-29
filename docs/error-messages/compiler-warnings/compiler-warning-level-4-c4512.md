---
title: 編譯器警告 (層級 4) C4512
ms.date: 11/04/2016
f1_keywords:
- C4512
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
ms.openlocfilehash: 068bdb2c7c87e8fe7cd3e482f53934de098a6166
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218087"
---
# <a name="compiler-warning-level-4-c4512"></a>編譯器警告 (層級 4) C4512

'class'：無法產生指派運算子

編譯器無法為指定的類別產生指派運算子。 未建立任何指派運算子。

衍生類別所無法存取的基底類別之指派運算子可能會導致此警告。

若要避免這個警告，請為該類別指定使用者定義的指派運算子。

編譯器也會為未定義的類別產生指派運算子函式。 此指派運算子是物件資料成員的成員複本。 由於 **`const`** 無法在初始化之後修改資料項目，因此，如果類別包含 **`const`** 專案，預設指派運算子將無法使用。 C4512 警告的另一個原因是宣告參考類型的非靜態資料成員。 如果目的是要建立不可複製的類型，您也必須防止建立預設複製建構函式。

您可以用三種方式之一來解決程式碼的 C4512 警告：

- 明確地定義類別的指派運算子。

- **`const`** 從類別中的資料項目移除或參考運算子。

- 請使用 #pragma [warning](../../preprocessor/warning.md)語句來隱藏警告。

## <a name="example"></a>範例

下列範例會產生 C4512。

```cpp
// C4512.cpp
// compile with: /EHsc /W4
// processor: x86

class Base {
private:
   const int a;

public:
   Base(int val = 0) : a(val) {}
   int get_a() { return a; }
};   // C4512 warning

class Base2 {
private:
   const int a;

public:
   Base2(int val = 0) : a(val) {}
   Base2 & operator=( const Base2 & ) { return *this; }
   int get_a() { return a; }
};

// Type designer intends this to be non-copyable because it has a
// reference member
class Base3
{
private:
   char& cr;

public:
   Base3(char& r) : cr(r) {}
   // Uncomment the following line to explicitly disable copying:
   // Base3(const Base3&) = delete;
};   // C4512 warning

int main() {
   Base first;
   Base second;

   // OK
   Base2 first2;
   Base2 second2;

   char c = 'x';
   Base3 first3(c);
   Base3 second3 = first3; // C2280 if no default copy ctor
}
```
