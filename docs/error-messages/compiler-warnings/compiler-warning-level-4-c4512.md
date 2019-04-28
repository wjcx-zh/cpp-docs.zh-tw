---
title: 編譯器警告 (層級 4) C4512
ms.date: 11/04/2016
f1_keywords:
- C4512
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
ms.openlocfilehash: c5e84fe1d0e558e689e48fba8df112861f81acec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220986"
---
# <a name="compiler-warning-level-4-c4512"></a>編譯器警告 (層級 4) C4512

'class'：無法產生指派運算子

編譯器無法為指定的類別產生指派運算子。 未建立任何指派運算子。

衍生類別所無法存取的基底類別之指派運算子可能會導致此警告。

若要避免這個警告，請為該類別指定使用者定義的指派運算子。

編譯器也會為未定義的類別產生指派運算子函式。 此指派運算子是物件資料成員的成員複本。 由於在初始設定之後無法修改 `const` 資料項目，因此如果類別含有 `const` 項目，則預設指派運算子將無法運作。 C4512 警告的另一個原因是宣告參考類型的非靜態資料成員。 如果目的是要建立不可複製的類型，您也必須防止建立預設複製建構函式。

您可以用三種方式之一來解決程式碼的 C4512 警告：

- 明確地定義類別的指派運算子。

- 移除**const**或參考運算子，從資料中的項目類別。

- 使用 #pragma[警告](../../preprocessor/warning.md)陳述式來隱藏警告。

## <a name="example"></a>範例

下列範例會產生 C4512。

```
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