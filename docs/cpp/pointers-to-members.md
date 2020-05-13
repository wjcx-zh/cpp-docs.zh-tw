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
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320325"
---
# <a name="pointers-to-members"></a>成員的指標

成員指標宣告是特殊的指標宣告。  它們使用以下順序聲明:

> *儲存類別指定程式*<sub>選擇</sub> *cv 修飾符*<sub>選擇</sub>*類型-規範器**ms-修飾符*選擇 修飾符<sub>選擇</sub>修飾符 選擇*修飾名稱***`::*`** *cv 修飾符*<sub>選擇</sub>*識別子*pm*初始化程式*<sub>選擇</sub>**`;`**

1. 宣告規範：

   - 選擇性的儲存類別規範。

   - 可選**的針和****揮發**性規格。

   - 類型指定名稱：類型的名稱。 它是要指向的成員的類型,而不是類。

1. 宣告子：

   - 選擇性的 Microsoft 專有修飾詞。 有關詳細資訊,請參閱特定於[Microsoft 的修飾符](../cpp/microsoft-specific-modifiers.md)。

   - 包含指向成員之類別的限定名稱。

   - __`::`__ 運算符。

   - __`*`__ 運算符。

   - 可選**的針和****揮發**性規格。

   - 為成員指標命名的識別項。

1. 選擇式指標到成員初始化器:

   - **`=`** 運算符。

   - **`&`** 運算符。

   - 類別的限定名稱。

   - __`::`__ 運算符。

   - 相應類型的類的非靜態成員的名稱。

一如往常，單一宣告允許使用多個宣告子 (和任何關聯的初始設定式)。 指定成員的指標不能指向一個的靜態成員、引用類型的成員或**`void`**。

指向類成員的指標與普通指標不同:它同時具有成員類型和成員所屬的類的類型資訊。 一般指標只能識別記憶體中的單一物件 (能取得其位址)。 類別的成員指標可以在類別的任何執行個體中識別該成員。 下列範例宣告類別、`Window` 和某些成員資料指標。

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
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

在前面的範例中,`pwCaption`是指向`Window``char*`類的任何類型的成員的指標。 `pwCaption` 的類型是 `char * Window::*`。 下一個程式碼片段會宣告 `SetCaption` 和 `GetCaption` 成員函式的指標。

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

`pfnwGC` 和 `pfnwSC` 指標分別指向 `GetCaption` 類別的 `SetCaption` 和 `Window`。 程式碼會使用成員指標 `pwCaption`，將資訊直接複製到視窗標題：

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

**`.*`** 和**`->*`** 運算符(指標到成員運算符)之間的區別是**`.*`**,運算符選擇給定物件或物件引用的成員,而**`->*`** 運算符通過指標選擇成員。 有關這些運算子的詳細資訊,請參閱[具有指標到成員運算符的運算符號 。](../cpp/pointer-to-member-operators-dot-star-and-star.md)

指標到成員運算符的結果是成員的類型。 在此案例中，此名稱為 `char *`。

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

靜態成員的位址不是指向成員的指標。 它是指向靜態成員的一個實例的常規指標。 給定類的所有物件僅存在一個靜態成員的實例。 這意味著您可以使用**&**( )<strong>\*</strong>和取消引用 運算子的普通位址。

## <a name="pointers-to-members-and-virtual-functions"></a>成員指標和虛擬函式

通過指標到成員函數調用虛擬函數的工作方式就像該函數被直接調用一樣。 在 v 表中抬起並調用了正確的函數。

就如以往一般，虛擬函式運作的關鍵在於透過基底類別的指標叫用  (有關虛擬函數的詳細資訊,請參閱[虛擬函數](../cpp/virtual-functions.md)。

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
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
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

//Output: Print function for class Base
Print function for class Derived
```
