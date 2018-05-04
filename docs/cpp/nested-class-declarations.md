---
title: 巢狀類別宣告 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fe55a1f67ff3c6ac06f1d6431e6e1a2fb8052d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="nested-class-declarations"></a>巢狀類別宣告
可以在某個類別的範圍內宣告另一個類別。 這種類別稱為「巢狀類別」。 巢狀類別被視為在封入類別的範圍內，可在該範圍內使用。 若要在直接封入範圍以外參考巢狀類別，則必須使用完整名稱。  
  
 下列範例顯示如何宣告巢狀類別：  
  
```  
// nested_class_declarations.cpp  
class BufferedIO  
{  
public:  
   enum IOError { None, Access, General };  
  
   // Declare nested class BufferedInput.  
   class BufferedInput  
   {  
   public:  
      int read();  
      int good()  
      {  
         return _inputerror == None;  
      }  
   private:  
       IOError _inputerror;  
   };  
  
   // Declare nested class BufferedOutput.  
   class BufferedOutput  
   {  
      // Member list  
   };  
};  
  
int main()  
{  
}  
```  
  
 `BufferedIO::BufferedInput` 和 `BufferedIO::BufferedOutput` 會在 `BufferedIO` 內宣告。 這些類別名稱在類別 `BufferedIO` 的範圍外不會顯示。 不過，類型為 `BufferedIO` 的物件不包含任何類型為 `BufferedInput` 或 `BufferedOutput` 的物件。  
  
 巢狀類別只能直接使用封入類別中的名稱、類型名稱、靜態成員的名稱及列舉程式。 若要使用其他類別成員的名稱，您必須使用指標、參考或物件名稱。  
  
 在上述 `BufferedIO` 範例中，可以在巢狀類別、`IOError` 或 `BufferedIO::BufferedInput` 中直接存取列舉 `BufferedIO::BufferedOutput`，如函式 `good` 中所示。  
  
> [!NOTE]
>  巢狀類別只能宣告類別範圍中的類型。 它們不會導致建立巢狀類別中所包含的物件。 上述範例宣告兩個巢狀類別，但不會宣告這些類別類型的任何物件。  
  
 巢狀類別宣告範圍可視性的例外是同時宣告類型名稱和向前宣告。  在這種情況下，向前宣告所宣告的類別名稱會在封入類別以外顯示，且其範圍定義為最小的封入非類別範圍。  例如:   
  
```  
// nested_class_declarations_2.cpp  
class C  
{  
public:  
    typedef class U u_t; // class U visible outside class C scope  
    typedef class V {} v_t; // class V not visible outside class C  
};  
  
int main()  
{  
    // okay, forward declaration used above so file scope is used  
    U* pu;  
  
    // error, type name only exists in class C scope  
    u_t* pu2; // C2065  
  
    // error, class defined above so class C scope  
    V* pv; // C2065  
  
    // okay, fully qualified name  
    C::V* pv2;  
}  
```  
  
## <a name="access-privilege-in-nested-classes"></a>巢狀類別中的存取權限  
 在某一個類別中將另一個類別設為巢狀，並不會對巢狀類別的成員函式提供特殊存取權限。 同樣地，封入類別的成員函式對於巢狀類別的成員不具有特殊存取權限。  
  
## <a name="member-functions-in-nested-classes"></a>巢狀類別中的成員函式  
 在巢狀類別中宣告的成員函式可以在檔案範圍中定義。 上一個範例可能已撰寫：  
  
```  
// member_functions_in_nested_classes.cpp  
class BufferedIO  
{  
public:  
    enum IOError { None, Access, General };  
    class BufferedInput  
    {  
    public:  
        int read(); // Declare but do not define member  
        int good(); //  functions read and good.  
    private:  
        IOError _inputerror;  
    };  
  
    class BufferedOutput  
    {  
        // Member list.  
    };  
};  
// Define member functions read and good in  
//  file scope.  
int BufferedIO::BufferedInput::read()  
{  
   return(1);  
}  
  
int BufferedIO::BufferedInput::good()  
{  
    return _inputerror == None;  
}  
int main()  
{  
}  
```  
  
 在上述範例中，*限定類型名稱*語法用於宣告函式名稱。 該宣告：  
  
```  
BufferedIO::BufferedInput::read()  
```  
  
 表示「`read` 函式是 `BufferedInput` 類別的成員，而該類別在 `BufferedIO` 類別的範圍中」。 因為這個宣告會使用*限定類型名稱*語法中，可能會在下列形式的建構：  
  
```  
typedef BufferedIO::BufferedInput BIO_INPUT;  
  
int BIO_INPUT::read()  
```  
  
 上述宣告等於前一個宣告，但此宣告使用 `typedef` 名稱取代類別名稱。  
  
## <a name="friend-functions-in-nested-classes"></a>巢狀類別中的 friend 函式  
 在巢狀類別中宣告的 friend 函式會被視為在巢狀類別的範圍內，而非封入類別的範圍內。 因此，friend 函式不會取得對封入類別之成員或成員函式的特殊存取權限。 如果您想要使用在 friend 函式的巢狀類別中宣告的名稱，而且 friend 函式是在檔案範圍中定義，請使用限定類型名稱，如下所示：  
  
```  
// friend_functions_and_nested_classes.cpp  
  
#include <string.h>  
  
enum  
{  
    sizeOfMessage = 255  
};  
  
char *rgszMessage[sizeOfMessage];  
  
class BufferedIO  
{  
public:  
    class BufferedInput  
    {  
    public:  
        friend int GetExtendedErrorStatus();  
        static char *message;  
        static int  messageSize;  
        int iMsgNo;  
   };  
};  
  
char *BufferedIO::BufferedInput::message;  
int BufferedIO::BufferedInput::messageSize;  
  
int GetExtendedErrorStatus()  
{  
    int iMsgNo = 1; // assign arbitrary value as message number  
  
    strcpy_s( BufferedIO::BufferedInput::message,  
              BufferedIO::BufferedInput::messageSize,  
              rgszMessage[iMsgNo] );  
  
    return iMsgNo;  
}  
  
int main()  
{  
}  
```  
  
 下列程式碼示範宣告為 friend 函式的 `GetExtendedErrorStatus` 函式。 在檔案範圍內定義的函式中，訊息會從靜態陣列複製到類別成員。 請注意，較理想的 `GetExtendedErrorStatus` 實作是將其宣告為：  
  
```  
int GetExtendedErrorStatus( char *message )  
```  
  
 前述介面可讓數個類別藉由傳遞要將錯誤訊息複製到其中的記憶體位置，使用這個函式的服務。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)