---
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 20116674feffaa5b4bbddf707dd3a4d0c1d9ad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364436"
---
# <a name="friend-c"></a>friend (C++)

在某些情況下,向非類成員或單獨類中的所有成員授予成員級訪問許可權更為方便。 只有類別實作器才能宣告它的 friend 是誰。 函式或類別不能將它自己宣告為任何類別的 friend。 在類定義中,使用**friend**關鍵字和非成員函數或其他類的名稱授予其對類的私有和受保護成員的訪問許可權。 在範本定義中,類型參數可以聲明為好友。

## <a name="syntax"></a>語法

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>friend 宣告

如果您宣告先前未宣告的 friend 函式，會將該函式匯出至封入 nonclass 範圍。

在友元聲明中聲明的函數被視為已使用**extern**關鍵字聲明的函數。 有關詳細資訊,請參閱[外部](extern-cpp.md)。

雖然可以在全域範圍函式的原型之前將此類函式宣告為 friend，但不可在其完整類別宣告出現之前將成員函式宣告為 friend。 下列程式碼示範失敗的原因：

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

上述範例在範圍中輸入類別名稱 `ForwardDeclared`，不過，完整宣告 (明確地說是宣告函式 `IsAFriend` 的部分) 是未知的。 因此,類**friend**`HasFriends`中的好友聲明生成錯誤。

從 C++11 開始,類有兩種形式的好友聲明:

```cpp
friend class F;
friend F;
```

如果在最裡面的命名空間中找不到該名稱的現有類,則第一個窗體將引入新的類 F。 **C++11:** 第二種形式不引入新類;它可以在已聲明類時使用,並且在將範本類型參數或 typedef 聲明為朋友時必須使用它。

若`class friend F`尚未宣告的型態時使用:

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

在下面的範例中,`friend F`引用`F`在 NS 範圍之外聲明的類。

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

將`friend F`樣本參數的聲明為好友:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

將`friend F`typedef 宣告為好友:

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
> 雖然整個第二個類別必須是第一個類別的 friend，但您可以第一個類別中的哪些函式是第二個類別的 friend。

## <a name="friend-functions"></a>friend 函式

**朋友**函數不是類的成員,但有權訪問類的私有和受保護成員。 friend 函式並非類別成員，而是擁有特殊存取權限的一般外部函式。 好友不在類的範圍內,並且不使用成員選擇運算符 **()** 調用它們。 和**>**- ),除非他們是另一個類的成員。 **朋友**函數由授予訪問許可權的類聲明。 **友號**聲明可以放置在類聲明中的任意位置。 不會受存取控制關鍵字的影響。

下列範例顯示 `Point` 類別和 friend 函式 `ChangePrivate`。 **友元**函數可以訪問它作為參數`Point`接收 的物件的私有數據成員。

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

類別成員函式可以宣告為其他類別的 friend。 請考慮下列範例：

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

上述範例只授與 `A::Func1( B& )` 函式類別 `B` 的 friend 存取權限。 `_b`因此,對私有成員的訪問在類`Func1``A`中是正確的,但在`Func2`中則不正確。

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

託管類型(C++/CLI 中)不能具有任何好友函數、朋友類或友號介面。

夥伴關係不能繼承，也就是說，衍生自 `YourOtherClass` 的類別不能存取 `YourClass` 的 private 成員。 夥伴關係不可轉移，因此，若類別屬於 `YourOtherClass` 的 friend，就無法存取 `YourClass` 的 private 成員。

下圖說明四種類別宣告：`Base`、`Derived`、`aFriend` 和 `anotherFriend`。 只有類別 `aFriend` 可以直接存取 `Base` 的 private 成員 (以及 `Base` 可能繼承的任何成員)。

![friend 關聯性的含意](../cpp/media/vc38v41.gif "friend 關聯性的含意") <br/>
friend 關聯性的含意

## <a name="inline-friend-definitions"></a>內嵌 friend 定義

可以在類聲明內定義(給定函數正文)友元函數。 這些函式為內嵌函式，而且如同成員內嵌函式一般，它們就像是緊接著在已查看所有類別成員之後，類別範圍關閉之前 (類別宣告的結尾) 所定義。 在類聲明中定義的好友函數在封閉類的範圍內。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
