---
title: 儲存類別 (C++)
description: 在C++中,靜態、外部和thread_local關鍵字指定變數或函數的存留期、連結和記憶體位置。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365352"
---
# <a name="storage-classes"></a>儲存體類別

C++變數聲明上下文中的*儲存類*是控制物件的存留期、連結和記憶體位置的類型指定器。 指定的物件只能有一個儲存類別。 在區塊中定義的變數具有自動儲存,除非使用**外部**、**靜態**或**thread_local**指定器指定。 自動物件和變數沒有連結；區塊外部的程式碼看不到它們。 當執行進入塊時,將自動為其分配記憶體,並在模組退出時取消分配記憶體。

**注意**

1. [可變](../cpp/mutable-data-members-cpp.md)關鍵字可被視為儲存類指定器。 不過，它只能在類別定義的成員清單中使用。

1. **視覺工作室 2010 及更高版本:****自動**關鍵字不再是儲存類C++指定器,**寄存器**關鍵字被棄用。 **Visual Studio 2017 版本 15.7 及更高版本:(** 提供[/std:c++17):](../build/reference/std-specify-language-standard-version.md)**註冊**關鍵字從C++語言中刪除。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>靜態

**靜態**關鍵字可用於在全域作用域、命名空間範圍和類作用域中聲明變數和函數。 靜態變數也可以在區域範圍內進行宣告。

靜態持續期間是指，物件或變數會在程式啟動時配置，並在程式結束時解除配置。 外部連結是指，變數名稱在變數宣告所在的檔案外部可見。 相反地，內部連結是指，名稱在變數宣告所在的檔案外部不可見。 根據預設，全域命名空間中所定義的物件或變數具有靜態持續期間和外部連結。 **靜態**關鍵字可用於以下情況。

1. 在檔案作用網域(全域和/或命名空間作用域)中聲明變數或函數時,**靜態**關鍵字指定變數或函數具有內部連結。 當您宣告變數時，變數會擁有靜態持續期間，且編譯器會將其初始化為 0 (除非您指定其他值)。

1. 在函數中聲明變數時,**靜態**關鍵字指定變數在調用該函數之間保留其狀態。

1. 在類別聲明中聲明資料成員時,**靜態**關鍵字指定該成員的一個副本由類的所有實例共用。 靜態資料成員必須以檔案範圍定義。 您聲明為**const 靜態**的整積分數據成員可以具有初始化程式。

1. 在類別聲明中聲明成員函數時,**靜態**關鍵字指定該函數由類的所有實例共用。 靜態成員函數無法訪問實例成員,因為該函數沒有隱式**此**指標。 若要存取執行個體成員，請使用本身為執行個體指標或參考的參數宣告函式。

1. 您無法將等位的成員宣告為靜態。 但是,必須顯式聲明全域聲明的匿名聯合**是靜態**的 。

此示例顯示函數中聲明**靜態**的變數如何在調用該函數之間保持其狀態。

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

這個範例顯示在類別中使用**靜態**。

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

此示例顯示成員函數中聲明**靜態**的局部變數。 靜態變數可供整個程式使用，而類型的所有執行個體會共用靜態變數的相同複本。

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

從 C++11 開始，保證靜態區域變數初始化為執行緒安全。 此功能有時稱為*魔法靜態*。 不過，在多執行緒應用程式中，必須同步處理所有後續指派。 可以使用[/Zc:線程SafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)標誌來禁用線程安全的靜態初始化功能,以避免依賴 CRT。

## <a name="extern"></a><a name="extern"></a>Extern

聲明為**extern**的物件和變數聲明在另一個轉換單元或封閉作用域中定義的物件具有外部連結。 有關詳細資訊,請參閱[外部](extern-cpp.md)和[翻譯單元和連結](program-and-linkage-cpp.md)。

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++11)

使用**thread_local**指定器聲明的變數只能在創建該變數的線程上訪問。 變數會在建立執行緒時建立，並在終結執行緒時終結。 每個執行緒都有它自己的變數複本。 在 Windows 上 **,thread_local**在功能上等效於特定於 Microsoft[的__declspec(線程 )](../cpp/thread.md)屬性。

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

關於**thread_local**規格需要注意的事項:

- 並非所有調用線程上都正確初始化 DLL 中的動態初始化線程局部變數。 如需詳細資訊，請參閱[執行緒](thread.md)。

- **thread_local**規格器可與**靜態**或**外部**結合。

- 您可以僅將**thread_local**應用於數據聲明和定義;因此,您可以將thread_local應用於數據聲明和定義。**thread_local**不能用於函數聲明或定義。

- 只能對具有靜態存儲持續時間的數據項指定**thread_local。** 這包括全域資料物件(**靜態**和**外部**)、本地靜態物件和類的靜態資料成員。 如果未提供其他存儲類,則聲明**thread_local**的任何本地變數都是隱式靜態的;換句話說,在塊範圍**thread_local**等`thread_local static`效於 。

- 您必須為線程本地物件的聲明和定義指定**thread_local,** 無論聲明和定義是在同一檔中發生的還是單獨的檔。

在 Windows 上 **,thread_local**在功能上等效於[__declspec(線程),](../cpp/thread.md)只不過 **__declspec(線程)** 可以應用於類型定義,並且在 C 代碼中有效。 盡可能使用**thread_local**因為它是C++標準的一部分,因此更加便攜。

## <a name="register"></a><a name="register"></a>註冊

**Visual Studio 2017 版本 15.3 及更高版本**(隨[/std:c++17](../build/reference/std-specify-language-standard-version.md)提供):**寄存器**關鍵字不再是受支援的存儲類。 關鍵字仍保留在標準中以供將來使用。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>範例:自動與靜態初始化

區域自動物件或變數會在每次控制流程到達其定義時初始化。 區域靜態物件或變數會在控制流程第一次到達其定義時初始化。

請考慮下列範例，範例中會定義記錄物件初始化和解構的類別，然後再定義三個物件 `I1`、`I2` 和 `I3`：

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

此範例展示如何以及何時初始化物件`I1`,`I2``I3`以及何時銷毀它們。

關於該程式,需要注意幾點:

- 首先，`I1` 和 `I2` 會在控制流程離開其定義所在的區塊時自動終結。

- 其次，在 C++ 中，不需要在區塊開頭宣告物件或變數。 再者，只有在控制流程到達其定義時，這些物件才會初始化  (`I2``I3`是此類定義的範例。輸出準確顯示初始化時間。

- 最後，靜態區域變數 (例如 `I3`) 會在程式執行期間保留其值，不過會在程式終止時終結。

## <a name="see-also"></a>另請參閱

[宣告和訂](../cpp/declarations-and-definitions-cpp.md)
