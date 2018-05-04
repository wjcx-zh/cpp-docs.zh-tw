---
title: friend （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- friend_cpp
dev_langs:
- C++
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1538ad67ce1b742c55dc413d78e40e8dcc9884df
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="friend-c"></a>friend (C++)
在某些情況下，它會授與不是類別的成員函式或個別的類別中的所有成員的成員層級存取較為方便。 只有類別實作器才能宣告它的 friend 是誰。 函式或類別不能將它自己宣告為任何類別的 friend。 在類別定義中，使用`friend`關鍵字和非成員函式或其他類別，以授與其存取類別的 private 和 protected 成員的名稱。         在樣板定義中，型別參數可以宣告為 friend。  
  
## <a name="syntax"></a>語法  
  
```  
class friend F  
friend F;  
```  
  
## <a name="friend-declarations"></a>friend 宣告  
 如果您宣告先前未宣告的 friend 函式，會將該函式匯出至封入 nonclass 範圍。  
  
 在 friend 宣告中宣告的函式視同使用 `extern` 關鍵字宣告  (如需有關`extern`，請參閱[靜態儲存類別規範](http://msdn.microsoft.com/en-us/3ba9289a-a412-4a17-b319-ceb2c087df48)。)  
  
 雖然可以在全域範圍函式的原型之前將此類函式宣告為 friend，但不可在其完整類別宣告出現之前將成員函式宣告為 friend。 下列程式碼示範失敗的原因：  
  
```cpp  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 上述範例在範圍中輸入類別名稱 `ForwardDeclared`，不過，完整宣告 (明確地說是宣告函式 `IsAFriend` 的部分) 是未知的。 因此，在類別 `friend` 中的 `HasFriends` 宣告會產生錯誤。  
  
 從 C + + 11 開始，有兩種類別的 friend 宣告：  
  
```cpp  
friend class F;  
friend F;  
```  
  
 如果沒有現有的類別，該名稱的最內層的命名空間中找不到第一種形式導入了新的類別 F。  **C + + 11**： 第二種形式不會產生新的類別; 它可以用於當已經宣告的類別，且必須在宣告樣板類型參數或做為 friend 的 typedef 時使用。  
  
 使用`class friend F`時參考的型別具有尚未宣告：  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        class friend F;  // Introduces F but doesn't define it  
    };  
}  
```  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations  
    };  
}  
```  
  
 在下列範例中，`friend F`指`F`NS 範圍外宣告為類別。  
  
```cpp  
class F {};  
namespace NS  
{  
    class M  
    {  
        friend F;  // OK   
    };  
}  
```  
  
 使用`friend F`宣告為 friend 的範本參數：  
  
```cpp  
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
 使用`friend F`宣告為 friend 的 typedef:  
  
```cpp  
class Foo {};  
typedef Foo F;  
  
class G  
{  
    friend F; // OK  
    friend class F // Error C2371 -- redefinition  
};  
```  
  
 若要宣告兩個類別為彼此的 Friend，必須將第二個類別完整指定為第一個類別的 friend。 這項限制的理由是編譯器的資訊只足以在宣告第二個類別的點宣告個別 friend 函式。  
  
> [!NOTE]
>  雖然整個第二個類別必須是第一個類別的 friend，但您可以第一個類別中的哪些函式是第二個類別的 friend。  
  
## <a name="friend-functions"></a>friend 函式  
 `friend` 函式不屬於類別成員，但可以存取類別的 Private 和 Protected 成員。 friend 函式並非類別成員，而是擁有特殊存取權限的一般外部函式。 Friend 不在類別的範圍內，且它們不會呼叫使用成員選取運算子 (**。** 和-**>**) 除非它們是另一個類別的成員。 `friend` 函式是由授與存取權的類別宣告。 `friend` 宣告可以放在類別宣告中的任何位置。 不會受存取控制關鍵字的影響。  
  
 下列範例顯示 `Point` 類別和 friend 函式 `ChangePrivate`。 `friend` 函式可以存取將其當做參數接收之 `Point` 物件的私用資料成員。  
  
```cpp  
// friend_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
    friend void ChangePrivate( Point & );  
public:  
    Point( void ) : m_i(0) {}  
    void PrintPrivate( void ){cout << m_i << endl; }  
  
private:  
    int m_i;  
};  
  
void ChangePrivate ( Point &i ) { i.m_i++; }  
  
int main()  
{  
   Point sPoint;  
   sPoint.PrintPrivate();  
   ChangePrivate(sPoint);  
   sPoint.PrintPrivate();  
// Output: 0  
           1  
}  
```  
  
## <a name="class-members-as-friends"></a>做為 friend 的類別成員  
 類別成員函式可以宣告為其他類別的 friend。 參考下列範例：  
  
```cpp  
// classes_as_friends1.cpp  
// compile with: /c  
class B;  
  
class A {  
public:  
   int Func1( B& b );  
  
private:  
   int Func2( B& b );  
};  
  
class B {  
private:  
   int _b;  
  
   // A::Func1 is a friend function to class B  
   // so A::Func1 has access to all members of B  
   friend int A::Func1( B& );  
};  
  
int A::Func1( B& b ) { return b._b; }   // OK  
int A::Func2( B& b ) { return b._b; }   // C2248  
```  
  
 上述範例只授與 `A::Func1( B& )` 函式類別 `B` 的 friend 存取權限。 因此，存取私用成員`_b`是正確的`Func1`類別的`A`但無法在`Func2`。  
  
 `friend` 類別是其所有成員函式皆為某個類別之 friend 函式的類別，也就是說，其成員函式可以存取其他類別的 private 成員和 protected 成員。 假設 `friend` 類別中的 `B` 宣告如下：  
  
```cpp  
friend class A;  
```  
  
 在這種情況下，`A` 類別中的所有成員函式將獲得類別 `B` 的 friend 存取權限。 下列程式碼是 friend 類別的範例：  
  
```cpp  
// classes_as_friends2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class YourClass {  
friend class YourOtherClass;  // Declare a friend class  
public:  
   YourClass() : topSecret(0){}  
   void printMember() { cout << topSecret << endl; }  
private:  
   int topSecret;  
};  
  
class YourOtherClass {  
public:  
   void change( YourClass& yc, int x ){yc.topSecret = x;}  
};  
  
int main() {  
   YourClass yc1;  
   YourOtherClass yoc1;  
   yc1.printMember();  
   yoc1.change( yc1, 5 );  
   yc1.printMember();  
}  
```  
  
 除非明確指定，否則夥伴關係不是雙向的。 在上述範例中，`YourClass` 的成員函式無法存取 `YourOtherClass` 的 private 成員。  
  
 Managed 型別不能包含任何 friend 函式、friend 類別或 friend 介面。  
  
 夥伴關係不能繼承，也就是說，衍生自 `YourOtherClass` 的類別不能存取 `YourClass` 的 private 成員。 夥伴關係不可轉移，因此，若類別屬於 `YourOtherClass` 的 friend，就無法存取 `YourClass` 的 private 成員。  
  
 下圖說明四種類別宣告：`Base`、`Derived`、`aFriend` 和 `anotherFriend`。 只有類別 `aFriend` 可以直接存取 `Base` 的 private 成員 (以及 `Base` 可能繼承的任何成員)。  
  
 ![Friend 關聯性的含意](../cpp/media/vc38v41.gif "vc38V41")  
隱含的 friend 關聯性  
  
## <a name="inline-friend-definitions"></a>內嵌 friend 定義  
 Friend 函式可以在類別宣告內定義。 這些函式為內嵌函式，而且如同成員內嵌函式一般，它們就像是緊接著在已查看所有類別成員之後，類別範圍關閉之前 (類別宣告的結尾) 所定義。  
  
 在類別宣告內定義的 friend 函式不會視為在封入類別的範圍內，而是在檔案範圍內。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)