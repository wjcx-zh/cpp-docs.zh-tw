---
title: 靜態成員 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: c18b29cf69c2f899fbf06c7cb75ebbd2242ab427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178557"
---
# <a name="static-members-c"></a>靜態成員 (C++)

類別可以包含靜態資料成員和成員函式。 當資料成員宣告為**static**時，只會針對類別的所有物件維護一個資料複本。

靜態資料成員不是特定類別類型之物件的一部分。 因此，靜態資料成員的宣告不視為定義。 資料成員是在類別範圍中宣告的，不過，定義是在檔案範圍執行。 這些靜態成員具有外部連結。 下列範例會加以說明：

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

在上述程式碼中，成員 `bytecount` 是在類別 `BufferedOutput` 中宣告，但必須在類別宣告之外加以定義。

靜態資料成員可以在不參考類別類型物件的情況下參考。 使用 `BufferedOutput` 物件撰寫的位元組數目可以如下取得：

```cpp
long nBytes = BufferedOutput::bytecount;
```

若要靜態成員存在，不需要有類別類型的物件存在。 也可以使用成員選取（）來存取靜態成員 **。** 和 **->** ）運算子。 例如：

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

在上述情況中，不會評估物件 (`Console`) 的參考；傳回值是靜態物件 `bytecount` 的傳回值。

靜態資料成員是受類別成員存取規則規範，因此，只有類別成員函式和 friend 才能進行靜態資料成員的私用存取。 [成員存取控制](../cpp/member-access-control-cpp.md)中會描述這些規則。 例外狀況是不管其存取限制，靜態資料成員必須在檔案範圍中定義。 如果資料成員將明確初始化，定義中必須提供初始設定式。

靜態成員的類型未以類別名稱限定。 因此，`BufferedOutput::bytecount` 的類型很**長**。

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)
