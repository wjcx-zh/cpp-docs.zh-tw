---
title: "this 指標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "this"
  - "this_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "非靜態成員函式"
  - "指標, 至類別執行個體"
  - "this 指標"
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# this 指標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**this** 指標是只能在 **class**、`struct` 或 **union** 類型的非靜態成員函式內存取的指標。  它會指向針對其呼叫成員函式的物件。  靜態成員函式沒有 **this** 指標。  
  
## 語法  
  
```  
  
        this   
this->member-identifier  
```  
  
## 備註  
 物件的 **this** 指標不屬於物件本身，因此不會在物件上 `sizeof` 陳述式的結果中反映出來。  不過，呼叫物件的非靜態成員函式時，編譯器會將物件的位址當做隱藏的引數傳遞至函式。  例如，下列函式呼叫：  
  
```  
myDate.setMonth( 3 );  
```  
  
 可以用這種方式解譯：  
  
```  
setMonth( &myDate, 3 );  
```  
  
 物件的位址可在成員函式內做為 **this** 指標使用。  **this** 的用法大多是隱含的。  在參考類別的成員時明確使用 **this** 是合法的，不過並非必要。  例如:  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 `*this` 運算式通常用來從成員函式傳回目前物件：  
  
```  
return *this;  
```  
  
 **this** 指標也會用於防範自我參考：  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  由於 **this** 指標無法修改，因此不允許對 **this** 進行指派。  較早的 C\+\+ 實作允許對 **this** 進行指派。  
  
 有時候 **this** 指標會直接使用，例如，用於管理需要目前物件位址的自我參考資料結構。  
  
## 範例  
  
```  
// this_pointer.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
class Buf   
{  
public:  
    Buf( char* szBuffer, size_t sizeOfBuffer );  
    Buf& operator=( const Buf & );  
    void Display() { cout << buffer << endl; }  
  
private:  
    char*   buffer;  
    size_t  sizeOfBuffer;  
};  
  
Buf::Buf( char* szBuffer, size_t sizeOfBuffer )  
{  
    sizeOfBuffer++; // account for a NULL terminator  
  
    buffer = new char[ sizeOfBuffer ];  
    if (buffer)  
    {  
        strcpy_s( buffer, sizeOfBuffer, szBuffer );  
        sizeOfBuffer = sizeOfBuffer;  
    }  
}  
  
Buf& Buf::operator=( const Buf &otherbuf )   
{  
    if( &otherbuf != this )   
    {  
        if (buffer)  
            delete [] buffer;  
  
        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;   
        buffer = new char[sizeOfBuffer];  
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );  
    }  
    return *this;  
}  
  
int main()  
{  
    Buf myBuf( "my buffer", 10 );  
    Buf yourBuf( "your buffer", 12 );  
  
    // Display 'my buffer'  
    myBuf.Display();  
  
    // assignment opperator  
    myBuf = yourBuf;  
  
    // Display 'your buffer'  
    myBuf.Display();  
}  
```  
  
  **my buffer**  
**your buffer**   
## this 指標的類型  
 **this** 指標的類型可以在函式宣告中藉由 **const** 和 `volatile` 關鍵字修改。  若要將函式宣告為擁有一個或多個這些關鍵字的屬性，請在函式引數清單後面加入關鍵字。  
  
 請考量以下範例：  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 上述程式碼會宣告成員函式 `X`，其中 **this** 指標會視為 **const** 物件的 **const** 指標。  您可以使用 *cv\-mod\-list* 選項的組合，但是這些組合一定會修改 **this** 所指向的物件，而非 **this** 指標本身。  因此，下列宣告會宣告 `X` 函式，而 **this** 指標是 **const** 物件的 **const** 指標：  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 成員函式中 **this** 的類型會以下列語法描述，其中 *cv\-qualifier\-list* 是從成員函式宣告子判斷而來，而且可以是 **const** 或 **volatile** \(或兩者皆是\)，*class\-type* 則是類別的名稱：  
  
 *\[cv\-qualifier\-list\] class\-type*  **\* const this**  
  
 換句話說，**this** 永遠是 const 指標，而且無法重新指派。  成員函式宣告中使用的 **const** 或 `volatile` 限定詞適用於 **this** 於該函式範圍內所指向的類別執行個體。  
  
 下表將進一步說明這些修飾詞的運作方式。  
  
### 修飾詞的語意  
  
|修飾詞|意義|  
|---------|--------|  
|**const**|無法變更成員資料，也無法叫用非 **const** 的成員函式。|  
|`volatile`|每次存取成員時，就會從記憶體載入成員資料，而且會停用某些最佳化。|  
  
 將 **const** 物件傳遞至非 **const** 的成員函式會發生錯誤。  同樣地，將 `volatile` 物件傳遞至非 `volatile` 的成員函式也會發生錯誤。  
  
 宣告為 **const** 的成員函式無法變更成員資料，在這類函式中，**this** 指標是 **const** 物件的指標。  
  
> [!NOTE]
>  建構函式和解構函式不能宣告為 **const** 或 `volatile`。  不過，它們可以在 **const** 或 `volatile` 物件上叫用。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [this 指標的類型](../misc/type-of-this-pointer.md)   
 [引數對應和 this 指標](../misc/argument-matching-and-the-this-pointer.md)