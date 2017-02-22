---
title: "類別成員概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別成員"
  - "類別成員, 類型"
  - "成員"
  - "成員, 類別成員的類型"
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 類別成員概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別或結構包含其成員。  類別所執行的工作是由其成員函式執行。  它所維護的狀態會儲存在其資料成員中。  成員是透過建構函式進行初始化，而清除工作 \(例如，釋放記憶體以及釋放資源\) 是透過建構函式所完成。  在 C\+\+11 和更新版本中，可以 \(且通常應該\) 在宣告時初始化資料成員。  
  
## 類別成員的類型  
 成員分類的完整清單如下：  
  
-   特殊成員函式。  
  
-   [成員函式](../misc/member-functions-cpp.md)。  
  
-   [資料成員](../cpp/static-members-cpp.md) \(包括內建類型和其他使用者定義類型\)。  
  
-   運算子  
  
-   [巢狀類別宣告](../cpp/nested-class-declarations.md) 及  
  
-   [等位](../cpp/unions.md)  
  
-   [列舉](../cpp/enumerations-cpp.md)。  
  
-   [位元欄位](../cpp/cpp-bit-fields.md)。  
  
-   [Friend](../cpp/friend-cpp.md)。  
  
-   [別名和 Typedef](../cpp/aliases-and-typedefs-cpp.md)。  
  
    > [!NOTE]
    >  前述清單包含 Friend，是因為它們包含在類別宣告中。  不過，它們不是真正的類別成員，因為它們不在類別的範圍內。  
  
## 範例類別宣告  
 下列範例示範簡單類別宣告：  
  
```  
// TestRun.h  
  
class TestRun  
{  
    // Start member list.  
  
    //The class interface accessible to all callers.  
public:  
    // Use compiler-generated default constructor:  
    TestRun() = default;   
    // Don't generate a copy constructor:  
    TestRun(const TestRun&) = delete;    
    TestRun(std::string name);  
    void DoSomething();  
    int Calculate(int a, double d);  
    virtual ~TestRun();  
    enum class State { Active, Suspended };  
  
    // Accessible to this class and derived classes only.  
protected:  
    virtual void Initialize();  
    virtual void Suspend();  
    State GetState();  
  
    // Accessible to this class only.  
private:  
    // Default brace-initialization of instance members:  
    State _state{ State::Suspended };   
    std::string _testName{ "" };   
    int _index{ 0 };  
  
    // Non-const static member:  
    static int _instances;  
    // End member list.  
};  
  
// Define and initialize static member.  
int TestRun::_instances{ 0 };  
```  
  
## 成員存取範圍  
 成員清單中所宣告類別的成員。  類別的成員清單可以使用稱為存取規範的關鍵字分成任意數目的 `private`、`protected` 和 **public** 區段。  冒號 **:** 必須接在存取指定名稱後面。  這些區段不需要是連續的，也就是說，這些關鍵字中任何一個都可以在成員清單中出現多次。  關鍵字會指定到下一個存取指定名稱，或右大括號之前所有成員的存取權限。  如需詳細資訊，請參閱[成員存取控制 \(C\+\+\)](../cpp/member-access-control-cpp.md)。  
  
## 靜態成員  
 資料成員可以宣告為靜態，這表示類別的所有物件都可以存取其相同複本。  成員函式可以宣告為靜態，在此情況下，它只能存取類別的靜態資料成員 \(且沒有 *this* 指標\)。  如需詳細資訊，請參閱[靜態資料成員](../cpp/static-members-cpp.md)。  
  
## 特殊成員函式  
 特殊成員函式是未在原始程式碼中指定函式時由編譯器自動提供的函式。  
  
1.  預設建構函式  
  
2.  複製建構函式  
  
3.  **\(C\+\+11\)** 移動建構函式  
  
4.  複製指派運算子  
  
5.  **\(C\+\+11\)** 移動指派運算子  
  
6.  解構函式  
  
## 成員方式初始化  
 在 C\+\+11 和更新版本中，非靜態成員宣告子可以包含初始設定式。  
  
```  
  
class CanInit  
{  
public:  
    long num {7};       // OK in C++11  
    int k = 9;          // OK in C++11  
    static int i = 9; // Error: must be defined and initialized  
                      // outside of class declaration.  
  
    // initializes num to 7 and k to 9  
    CanInit(){}  
  
    // overwrites original initialized value of num:  
    CanInit(int val) : num(val) {}  
};  
int main()  
{  
}  
```  
  
 如果成員在建構函式中獲指派值，該值會覆寫用來在宣告時初始化成員的值。  
  
 特定類別類型的所有物件只會有一個共用的靜態資料成員複本。  靜態資料成員必須以檔案範圍定義，而且可以依檔案範圍初始化   \(如需靜態資料成員的詳細資訊，請參閱[靜態資料成員](../cpp/static-members-cpp.md)\)。 下列範例將示範如何執行這些初始化：  
  
```  
// class_members2.cpp  
class CanInit2  
{  
public:  
    CanInit2() {} // Initializes num to 7 when new objects of type   
                 //  CanInit are created.  
    long     num {7};  
    static int i;  
    static int j;  
};  
  
// At file scope:  
  
// i is defined at file scope and initialized to 15.  
// The initializer is evaluated in the scope of CanInit.  
int CanInit2::i = 15;  
  
// The right side of the initializer is in the scope   
// of the object being initialized  
int CanInit2::j = i;  
```  
  
> [!NOTE]
>  類別名稱 `CanInit2` 前面必須加上 `i`，才能將所要定義的 `i` 指定為 `CanInit2` 類別的成員。  
  
## 請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)