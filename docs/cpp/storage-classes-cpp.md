---
title: 儲存類別 (C++)
ms.date: 11/04/2016
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: e50e5da5ea24d59131f123bb0c772897f9a30218
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266929"
---
# <a name="storage-classes-c"></a>儲存類別 (C++)

A*儲存類別*的內容中C++變數宣告為類型規範，可控管物件的存留期、 連結和記憶體位置。 指定的物件只能有一個儲存類別。 區塊內定義的變數會具有自動儲存區，除非另有指定使用**extern**，**靜態**，或`thread_local`規範。 自動物件和變數沒有連結；區塊外部的程式碼看不到它們。

**備註**

1. [可變](../cpp/mutable-data-members-cpp.md)關鍵字可視為儲存類別規範。 不過，它只能在類別定義的成員清單中使用。

1. **視覺化C++2010年及更新版本：**  **自動**關鍵字不再是C++儲存類別規範，而**註冊**關鍵字已被取代。 **Visual Studio 2017 15.7 版及更新版本：** (適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**註冊**關鍵字會從移除C++語言。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>本節內容：

- [static](#static)
- [extern](#extern)
- [thread_local](#thread_local)

## <a name="static"></a> static

**靜態**關鍵字可以用來宣告變數和函式，在全域範圍、 命名空間範圍和類別範圍。 靜態變數也可以在區域範圍內進行宣告。

靜態持續期間是指，物件或變數會在程式啟動時配置，並在程式結束時解除配置。 外部連結是指，變數名稱在變數宣告所在的檔案外部可見。 相反地，內部連結是指，名稱在變數宣告所在的檔案外部不可見。 根據預設，全域命名空間中所定義的物件或變數具有靜態持續期間和外部連結。 **靜態**關鍵字可用於下列情況。

1. 當您宣告變數或函式在檔案範圍 (全域和/或命名空間範圍)，則**靜態**關鍵字指定變數或函式具有內部連結。 當您宣告變數時，變數會擁有靜態持續期間，且編譯器會將其初始化為 0 (除非您指定其他值)。

1. 當您宣告函式中的變數**靜態**關鍵字指定變數會保留其對該函式的呼叫之間的狀態。

1. 當您宣告在類別宣告中，資料成員**靜態**關鍵字可讓您指定之成員的一個複本會共用類別的所有執行個體。 靜態資料成員必須以檔案範圍定義。 您將宣告為整數類資料的資料成員**const 靜態**可以有初始設定式。

1. 當您宣告在類別宣告中，成員函式**靜態**關鍵字可讓您指定的函式會共用類別的所有執行個體。 靜態成員函式無法存取執行個體成員，因為函式沒有隱含**這**指標。 若要存取執行個體成員，請使用本身為執行個體指標或參考的參數宣告函式。

1. 您無法將等位的成員宣告為靜態。 不過，必須明確宣告全域宣告的匿名等位**靜態**。

此範例示範如何宣告的變數**靜態**函式中會保留其對該函式的呼叫之間的狀態。

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

此範例示範如何使用**靜態**類別中。

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

此範例示範宣告的區域變數**靜態**的成員函式。 靜態變數可供整個程式使用，而類型的所有執行個體會共用靜態變數的相同複本。

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

從 C++11 開始，保證靜態區域變數初始化為執行緒安全。 這項功能有時稱為*magic 靜態變數*。 不過，在多執行緒應用程式中，必須同步處理所有後續指派。 安全執行緒靜態初始設定 」 功能可以使用已停用[/zc: threadsafeinit](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)旗標，以避免相依於 CRT。

## <a name="extern"></a> extern

物件和變數宣告為**extern**宣告定義於另一個轉譯單位中，或為具有外部連結封閉範圍中的物件。

Deklarace **const**變數**extern**儲存類別會強制該變數具有外部連結。 初始**extern const**允許定義轉譯單位中的變數。 若在定義轉譯單位以外的轉譯單位中初始化，會產生未定義的結果。 如需詳細資訊，請參閱[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)編譯器選項可讓編譯器套用[外部連結](../c-language/external-linkage.md)變數宣告可透過`extern constexpr`。 在舊版的 Visual Studio，並依預設或如果 **/Zc:externConstexpr-** 指定時，Visual Studio 會套用到的內部連結**constexpr**變數，即使**extern**使用關鍵字。 **/Zc: externconstexpr**選項是從 Visual Studio 2017 Update 15.6 中推出。 和預設為關閉。 /Permissive-option 不會啟用 /zc: externconstexpr。

下列程式碼示範兩個**extern**宣告`DefinedElsewhere`（這是指不同的轉譯單位中定義的名稱） 和`DefinedHere`（參考封閉範圍中定義的名稱）：

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;
int main() {
   int DefinedHere;
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> thread_local (C + + 11)

如果變數是使用 `thread_local` 規範所宣告，則只有在建立它的執行緒上才能進行存取。 變數會在建立執行緒時建立，並在終結執行緒時終結。 每個執行緒都有它自己的變數複本。 在 Windows 中，`thread_local`相當於 Microsoft 專有[__declspec (thread)](../cpp/thread.md)屬性。

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

注意事項`thread_local`規範：

- 以動態方式初始化的執行緒區域變數 Dll 中可能無法正確初始化所有的呼叫執行緒上。 如需詳細資訊，請參閱[執行緒](thread.md)。

- `thread_local`規範也可以結合**靜態**或是**extern**。

- 您可以套用`thread_local`至資料宣告和定義;`thread_local`不能在函式宣告或定義。

- 您只能在具有靜態儲存持續時間的資料項目上指定 `thread_local`。 這包括全域資料物件 (兩者**靜態**並**extern**)、 區域靜態物件和類別的靜態資料成員。 宣告的任何區域變數`thread_local`是以隱含方式靜態，如果沒有其他的儲存體類別會提供; 換句話說，在區塊範圍`thread_local`相當於`thread_local static`。

- 不論是在相同的檔案還是不同的檔案進行宣告和定義，您都必須指定執行緒區域物件之宣告和定義的 `thread_local`。

在 Windows 中，`thread_local`相當於[__declspec （thread)](../cpp/thread.md)不同之處在於 **__declspec （thread)** 可以套用至類型定義，並在 C 程式碼中有效。 只要可能，都請使用 `thread_local`，因為它是 C++ 標準的一部分，因此更具可攜性。

##  <a name="register"></a>  register

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**註冊**關鍵字不再是支援的存放裝置類別。 關鍵字是仍保留供日後使用標準的。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>範例： 自動格式設定與靜態初始設定

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

此範例示範如何及何時物件`I1`， `I2`，和`I3`會初始化，而且損毀時。

有幾點要注意關於此計畫：

- 首先，`I1` 和 `I2` 會在控制流程離開其定義所在的區塊時自動終結。

- 其次，在 C++ 中，不需要在區塊開頭宣告物件或變數。 再者，只有在控制流程到達其定義時，這些物件才會初始化  (這類定義的範例包括 `I2` 和 `I3`)。輸出中會顯示它們初始化的確切時間。

- 最後，靜態區域變數 (例如 `I3`) 會在程式執行期間保留其值，不過會在程式終止時終結。

## <a name="see-also"></a>另請參閱

[宣告和定義](../cpp/declarations-and-definitions-cpp.md)