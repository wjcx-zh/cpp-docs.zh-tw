---
title: "此指標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- this_cpp
dev_langs:
- C++
helpviewer_keywords:
- nonstatic member functions
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
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
ms.openlocfilehash: 86ccf50a089b1497bdc166ee9367215dc59b3ca1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="this-pointer"></a>this 指標
**這**指標是只能在非靜態成員函式中存取指標**類別**， `struct`，或**union**型別。 它會指向針對其呼叫成員函式的物件。 靜態成員函式沒有**這**指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      this   
this->member-identifier  
```  
  
## <a name="remarks"></a>備註  
 物件的**這**指標不屬於物件本身，不會反映在結果中的`sizeof`物件上的陳述式。 不過，呼叫物件的非靜態成員函式時，編譯器會將物件的位址當做隱藏的引數傳遞至函式。 例如，下列函式呼叫：  
  
```  
myDate.setMonth( 3 );  
```  
  
 可以用這種方式解譯：  
  
```  
setMonth( &myDate, 3 );  
```  
  
 物件的位址會做為成員函式可從**這**指標。 大部分的使用**這**隱含。 它是合法的不過並非必要明確使用**這**類別成員的參考時。 例如:   
  
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
  
 **這**指標也會用於防範自我參考：  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  因為**這**指標是無法修改，以指派**這**不允許。 舊版 c + + 實作允許指派**這**。  
  
 有時候，**這**指標會直接使用 — 例如，可操作自我參考的資料結構，需要目前物件的位址的地方。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
my buffer  
your buffer  
```  
  
## <a name="type-of-the-this-pointer"></a>this 指標的類型  
 **這**指標的類型都可以在函式宣告中藉由修改**const**和`volatile`關鍵字。 若要將函式宣告為擁有一個或多個這些關鍵字的屬性，請在函式引數清單後面加入關鍵字。  
  
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
  
 上述程式碼會宣告成員函式， `X`，在其中**這**指標會視為**const**指標**const**物件。 組合*cv mod 清單*可用選項，但永遠修改所指向的物件**這**，而非**這**指標本身。 因此，下列宣告會宣告函式`X`;**這**指標**const**指標**const**物件：  
  
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
  
 型別**這**在成員函式描述由下列語法，其中*cv 限定詞清單*取決於成員函式宣告子，而且可以是**const**或**volatile** （或兩者），和*類別類型*是類別的名稱：  
  
 *[cv 限定詞-清單] 類別型別*** \* const 這  **  
  
 換句話說，**這**永遠是 const 指標，而且無法重新指派。  **Const**或`volatile`限定詞用於成員函式宣告套用至類別執行個體所指**這**該函式的範圍內。  
  
 下表將進一步說明這些修飾詞的運作方式。  
  
### <a name="semantics-of-this-modifiers"></a>修飾詞的語意  
  
|修飾詞|意義|  
|--------------|-------------|  
|**const**|無法變更成員資料。無法叫用成員函式不**const**。|  
|`volatile`|每次存取成員時，就會從記憶體載入成員資料，而且會停用某些最佳化。|  
  
 它是要傳遞錯誤**const**物件不是成員函式**const**。 同樣地，將 `volatile` 物件傳遞至非 `volatile` 的成員函式也會發生錯誤。  
  
 成員函式宣告為**const**無法變更成員資料，在這類函式，**這**指標是指標**const**物件。  
  
> [!NOTE]
>  建構函式和解構函式不能宣告為**const**或`volatile`。 不過，它們可以是在叫用**const**或`volatile`物件。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 
