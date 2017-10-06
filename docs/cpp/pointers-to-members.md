---
title: "成員指標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 98a6db086443c15964a1dcf0a345b2fbaccfa233
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="pointers-to-members"></a>成員的指標
成員指標宣告是特殊的指標宣告。  函式是使用下列序列宣告：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  宣告規範：  
  
    -   選擇性的儲存類別規範。  
  
    -   選擇性**const**及/或`volatile`規範。  
  
    -   類型指定名稱：類型的名稱。  這是指向成員的類型，而不是類別的類型。  
  
2.  宣告子：  
  
    -   選擇性的 Microsoft 專有修飾詞。 如需詳細資訊，請參閱[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。  
  
    -   包含指向成員之類別的限定名稱。   
  
    -   :: 運算子。  
  
    -   ** \* **運算子。  
  
    -   選擇性**const**及/或`volatile`規範。  
  
    -   為成員指標命名的識別項。  
  
    -   選擇性的初始設定式：  
  
 ** = **運算子。  
  
 ** & **運算子。  
  
 類別的限定名稱。  
  
 `::` 運算子。  
  
 適當類型類別之非靜態成員的名稱  
  
 一如往常，單一宣告允許使用多個宣告子 (和任何關聯的初始設定式)。  
  
 類別成員指標不同於一般指標，因為這類指標包含成員類型及成員所屬類別的類型資訊。 一般指標只能識別記憶體中的單一物件 (能取得其位址)。 類別的成員指標可以在類別的任何執行個體中識別該成員。 下列範例宣告類別、`Window` 和某些成員資料指標。  
  
```  
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
  
 在上述範例中，`pwCaption`類別的任何成員的指標`Window`用具有型別的**char\***。 `pwCaption` 的類型是 `char * Window::*`。 下一個程式碼片段會宣告 `SetCaption` 和 `GetCaption` 成員函式的指標。  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 `pfnwGC` 和 `pfnwSC` 指標分別指向 `GetCaption` 類別的 `SetCaption` 和 `Window`。 程式碼會使用成員指標 `pwCaption`，將資訊直接複製到視窗標題：  
  
```  
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
  
 之間的差異**。\***和** -> \* **運算子 （成員指標運算子） 是**。\***運算子會選取指定物件或物件參考，而** -> \* **運算子會選取透過指標的成員。 (如需有關這些運算子的詳細資訊，請參閱[具有成員指標運算子的運算式](../cpp/pointer-to-member-operators-dot-star-and-star.md)。)  
  
 成員指標運算子的結果是成員的型別，在此情況下， **char \* **。  
  
 下一個程式碼片段會使用成員指標叫用 `GetCaption` 和 `SetCaption` 成員函式：  
  
```  
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
 靜態成員的位址不是成員的指標。 它是某一個靜態成員執行個體的一般指標。 因為只有一個執行個體的靜態成員存在之所有物件的指定類別，一般的地址的**(&)**取值 （dereference） 和**(\*)**運算子可用。  
  
## <a name="pointers-to-members-and-virtual-functions"></a>成員指標和虛擬函式  
 透過成員指標函式叫用虛擬函式的運作方式就像直接呼叫函式，正確的函式會在 v-table 中查閱及叫用。  
  
 就如以往一般，虛擬函式運作的關鍵在於透過基底類別的指標叫用  (如需虛擬函式的詳細資訊，請參閱[虛擬函式](../cpp/virtual-functions.md)。)  
  
 下列程式碼將示範如何透過成員指標函式叫用虛擬函式：  
  
```  
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
  
## <a name="see-also"></a>另請參閱  
 
