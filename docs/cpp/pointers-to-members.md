---
title: 成員的指標
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: fe92f848c5d5240f1afc657f5fb176513c8f9d88
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213290"
---
# <a name="pointers-to-members"></a>成員的指標

成員指標宣告是特殊的指標宣告。  它們是使用下列順序來宣告：

> *儲存類別*指定名稱<sub>opt</sub> *cv 限定詞*<sub>opt</sub> *類型規範* *ms-修飾*<sub>詞 opt</sub> *限定名稱* **`::*`** *cv 限定詞*<sub>opt</sub> *識別碼* *pm-初始化運算式*<sub>opt</sub>**`;`**

1. 宣告規範：

   - 選擇性的儲存類別規範。

   - 選擇性 **`const`** 和規範 **`volatile`** 。

   - 類型指定名稱：類型的名稱。 這是要指向的成員類型，而不是類別。

1. 宣告子：

   - 選擇性的 Microsoft 專有修飾詞。 如需詳細資訊，請參閱[Microsoft 專有的](../cpp/microsoft-specific-modifiers.md)修飾詞。

   - 包含指向成員之類別的限定名稱。

   - __`::`__ 運算子。

   - __`*`__ 運算子。

   - 選擇性 **`const`** 和規範 **`volatile`** 。

   - 為成員指標命名的識別項。

1. 選擇性的成員指標初始化運算式：

   - **`=`** 運算子。

   - **`&`** 運算子。

   - 類別的限定名稱。

   - __`::`__ 運算子。

   - 適當型別之類別的非靜態成員名稱。

一如往常，單一宣告允許使用多個宣告子 (和任何關聯的初始設定式)。 成員的指標可能不會指向類別的靜態成員、參考型別的成員，或 **`void`** 。

類別成員的指標與一般指標不同：它具有成員類型的類型資訊，以及該成員所屬的類別。 一般指標只能識別記憶體中的單一物件 (能取得其位址)。 類別的成員指標可以在類別的任何執行個體中識別該成員。 下列範例宣告類別、`Window` 和某些成員資料指標。

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       // Window size.
   bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

在上述範例中， `pwCaption` 是型別之任何類別成員的指標 `Window` **`char*`** 。 `pwCaption` 的類型是 `char * Window::*`。 下一個程式碼片段會宣告 `SetCaption` 和 `GetCaption` 成員函式的指標。

```cpp
const char * (Window::* pfnwGC)() = &Window::GetCaption;
bool (Window::* pfnwSC)( const char * ) = &Window::SetCaption;
```

`pfnwGC` 和 `pfnwSC` 指標分別指向 `GetCaption` 類別的 `SetCaption` 和 `Window`。 程式碼會使用成員指標 `pwCaption`，將資訊直接複製到視窗標題：

```cpp
Window  wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int     cUntitledLen  = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     // same as
// wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; // same as
// pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

**`.*`** 和 **`->*`** 運算子（成員指標運算子）之間的差異在於， **`.*`** 運算子會選取指定物件或物件參考的成員，而 **`->*`** 運算子會透過指標選取成員。 如需這些運算子的詳細資訊，請參閱[使用成員指標運算子的運算式](../cpp/pointer-to-member-operators-dot-star-and-star.md)。

成員指標運算子的結果是成員的類型。 在此案例中，此名稱為 `char *`。

下一個程式碼片段會使用成員指標叫用 `GetCaption` 和 `SetCaption` 成員函式：

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>成員指標的限制

靜態成員的位址不是成員的指標。 這是一個靜態成員實例的一般指標。 只有一個靜態成員的實例存在於指定類別的所有物件中。 這表示您可以使用一般的位址（ **&** ）和引用（ <strong>\*</strong> ）運算子。

## <a name="pointers-to-members-and-virtual-functions"></a>成員指標和虛擬函式

透過成員指標函式叫用虛擬函式的運作方式，如同已直接呼叫函式一樣。 在 v 資料表中查閱正確的函式，並加以叫用。

就如以往一般，虛擬函式運作的關鍵在於透過基底類別的指標叫用  （如需虛擬函式的詳細資訊，請參閱[虛擬](../cpp/virtual-functions.md)函式）。

下列程式碼將示範如何透過成員指標函式叫用虛擬函式：

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
public:
    virtual void Print();
};
void (Base::* bfnPrint)() = &Base::Print;
void Base::Print()
{
    cout << "Print function for class Base" << endl;
}

class Derived : public Base
{
public:
    void Print();  // Print is still a virtual function.
};

void Derived::Print()
{
    cout << "Print function for class Derived" << endl;
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

// Output:
// Print function for class Base
// Print function for class Derived
```
