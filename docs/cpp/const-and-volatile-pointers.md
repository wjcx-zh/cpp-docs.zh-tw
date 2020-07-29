---
title: const 和 volatile 指標
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: a8fd25777d1169ba281fbee173c1c8f5673c8b56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227565"
---
# <a name="const-and-volatile-pointers"></a>const 和 volatile 指標

[Const](const-cpp.md)和[volatile](volatile-cpp.md)關鍵字會變更指標的處理方式。 **`const`** 關鍵字指定在初始化之後無法修改指標; 之後，指標會受到保護而無法修改。

**`volatile`** 關鍵字指定與後面的名稱相關聯的值可以由使用者應用程式以外的動作來修改。 因此， **`volatile`** 關鍵字適用于宣告共用記憶體中的物件，可供多個進程或用於與插斷服務常式通訊的全域資料區域存取。

當名稱宣告為時 **`volatile`** ，編譯器會在每次由程式存取時，從記憶體重載值。 這將可大幅減少進行最佳化的次數。 不過，當物件的狀態可能遭到意外變更時，它仍是確保可預測程式效能的唯一方式。

若要將指標所指向的物件宣告為 **`const`** 或 **`volatile`** ，請使用下列格式的宣告：

```cpp
const char *cpch;
volatile char *vpch;
```

若要宣告指標的值（也就是儲存在指標中的實際位址）， **`const`** **`volatile`** 請使用下列格式的宣告：

```cpp
char * const pchc;
char * volatile pchv;
```

C + + 語言會防止允許修改宣告為之物件或指標的指派 **`const`** 。 這類指派會移除用來宣告物件或指標的資訊，因此違反了原始宣告的用意。 請考慮下列宣告：

```cpp
const char cch = 'A';
char ch = 'B';
```

假設有兩個物件的前面宣告（ `cch` ，類型為**const char**，而 `ch` ，類型為**char）**，下列宣告/初始化是有效的：

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

下列宣告/初始化是錯誤的。

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

`pch2` 的宣告會宣告一項指標，但是常數物件可能會透過該指標而遭到修改，因此不允許此宣告。 的宣告 `pch3` 會指定指標為常數，而不是物件; 因為不允許宣告，所以不允許宣告 `pch2` 。

下列八個指派顯示透過指標進行的指派，以及變更上述宣告的指標值；現在，我們可以假設透過 `pch1` 進行 `pch8` 的初始化是正確的。

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

宣告為 **`volatile`** 或混合使用的指標會 **`const`** **`volatile`** 遵守相同的規則。

**`const`** 物件的指標通常用於函式宣告，如下所示：

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

上述語句會宣告函式， [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中三個引數的其中兩個是的類型指標 **`char`** 。 由於引數是以傳址方式傳遞，而不是以傳值方式傳遞，因此，如果未宣告為，則函式可自由修改 `strDestination` 和 `strSource` `strSource` **`const`** 。 的宣告 `strSource` **`const`** 會確保呼叫端 `strSource` 無法由被呼叫的函式變更。

> [!NOTE]
> 因為有從*typename*到 typename 的標準轉換，所以將 <strong>\*</strong> **`const`** *typename* <strong>\*</strong> 類型的引數傳遞 `char *` 給[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)是合法的。 不過，反向並不成立;從物件或指標移除屬性時，不會有隱含轉換 **`const`** 。

**`const`** 指定類型的指標可以指派給相同類型的指標。 不過，不 **`const`** 能將指標指派給 **`const`** 指標。 下列程式碼顯示正確和不正確的指派：

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

下列範例顯示在您有一個指標指向物件的指標時，如何將物件宣告為常數。

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>另請參閱

[指標](pointers-cpp.md) 
[原始指標](raw-pointers.md)
