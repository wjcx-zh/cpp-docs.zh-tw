---
title: 如何：在 C++/CLI 中定義和使用列舉
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370179"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>如何：在 C++/CLI 中定義和使用列舉

本主題討論C++/CLI中的枚舉。

## <a name="specifying-the-underlying-type-of-an-enum"></a>指定一個枚舉的基礎型態

預設情況下,枚舉的基礎類型為`int`。  但是,您可以指定要簽署的類型或`int`未簽署的表`short`單`long`、、`__int32``__int64`或 。  您也可以使用 `char`。

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

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>如何在託管和標準枚舉之間進行轉換

枚舉和積分類型之間沒有標準轉換;需要強制轉換。

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

## <a name="operators-and-enums"></a>運算子和枚舉

以下運算子在 C++/CLI 中的枚舉中有效:

|運算子|
|--------------|
|[ \<  >  \<! ] >*|
|+ -|
|&#124; [ & ]|
|++ --|
|sizeof|

運算符&#124; = & = = - 僅定義為具有積分基礎類型的枚舉,不包括 bool。  兩個操作數都必須為枚舉類型。

編譯器不靜態或動態檢查枚舉操作的結果;操作可能會導致值不在枚舉的有效枚舉器範圍內。

> [!NOTE]
> C++11 在非託管代碼中引入了枚舉類類型,這些類型與 C++/CLI 中的託管枚舉類明顯不同。 特別是,C++11枚舉類類型不支援與C++/CLI 中的託管枚舉類類型相同的運算符,並且C++/CLI 原始程式碼必須在託管枚舉類聲明中提供輔助功能指定器,以便將它們與非託管 (C++11) 枚舉類聲明區分開來。 有關C++/CLI、C++/CX 和 C++11 中的枚舉類的詳細資訊,請參閱[枚舉類](../extensions/enum-class-cpp-component-extensions.md)。

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
