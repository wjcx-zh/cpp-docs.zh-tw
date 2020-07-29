---
title: 作法：在 C++/CLI 中定義和使用列舉
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: f09bb6e9fac30b72c3c4e0682c3d90f2ea9f8760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216410"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>作法：在 C++/CLI 中定義和使用列舉

本主題討論 c + +/CLI 中的列舉

## <a name="specifying-the-underlying-type-of-an-enum"></a>指定列舉的基礎類型

根據預設，列舉的基礎類型是 **`int`** 。  不過，您可以指定要簽署的類型或 **`int`** 、 **`short`** 、 **`long`** 、 **`__int32`** 或的不帶正負號形式 **`__int64`** 。  您也可以使用 **`char`** 。

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**輸出**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>如何在 managed 和標準列舉之間轉換

列舉和整數類資料類型之間沒有標準轉換;需要轉換。

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**輸出**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>運算子和列舉

下列運算子在 c + +/CLI 的列舉中是有效的：

|運算子|
|--------------|
|== != \< >\<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

運算子 &#124; ^ & ~ + +--僅針對具有整數基礎類型的列舉（不包括 bool）定義。  這兩個運算元都必須是列舉型別。

編譯器不會對列舉運算的結果進行靜態或動態檢查;作業可能會導致值不在列舉的有效枚舉器範圍內。

> [!NOTE]
> C + + 11 引進了非受控程式碼中的列舉類別類型，這與 c + +/CLI 中的 managed 列舉類別截然不同 特別是 c + + 11 列舉類別類型不支援與 c + +/CLI 中的 managed 列舉類別類型相同的運算子，而 c + +/CLI 原始程式碼必須在 managed enum 類別宣告中提供存取範圍規範，才能區別它們與非受控（c + + 11）列舉類別宣告。 如需 c + +/CLI、c + +/CX 和 c + + 11 中列舉類別的詳細資訊，請參閱[enum 類別](../extensions/enum-class-cpp-component-extensions.md)。

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**輸出**

```Output
4
1
True
```

## <a name="see-also"></a>另請參閱

[enum 類別](../extensions/enum-class-cpp-component-extensions.md)
