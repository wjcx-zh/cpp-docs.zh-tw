---
title: 儲存類別 (C++)
description: 在C++中，static、extern 和 thread_local 關鍵字會指定變數或函數的存留期、連結和記憶體位置。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- extern_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: ab00a5c64a32dc1dab5fef4bc15b722587bc2d6b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418395"
---
# <a name="storage-classes"></a>儲存體類別

變數宣告內容中的*儲存類別*是一種類型規範，可控制物件的存留期、連結和記憶體位置。 C++ 指定的物件只能有一個儲存類別。 除非使用**extern**、 **static**或**thread_local**規範來指定，否則區塊內定義的變數會具有自動儲存區。 自動物件和變數沒有連結；區塊外部的程式碼看不到它們。 當執行進入區塊時，系統會自動為它們配置記憶體，並在結束區塊時解除配置。

**注意**

1. 可以將[可變](../cpp/mutable-data-members-cpp.md)關鍵字視為儲存類別規範。 不過，它只能在類別定義的成員清單中使用。

1. **Visual Studio 2010 和更新版本：** **Auto**關鍵字不再是C++儲存類別規範，而且**register**關鍵字已被取代。 **Visual Studio 2017 15.7 版和更新版本：** （適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： **register**關鍵字已從C++語言中移除。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a>靜止

**Static**關鍵字可以用來宣告全域範圍、命名空間範圍和類別範圍的變數和函式。 靜態變數也可以在區域範圍內進行宣告。

靜態持續期間是指，物件或變數會在程式啟動時配置，並在程式結束時解除配置。 外部連結是指，變數名稱在變數宣告所在的檔案外部可見。 相反地，內部連結是指，名稱在變數宣告所在的檔案外部不可見。 根據預設，全域命名空間中所定義的物件或變數具有靜態持續期間和外部連結。 在下列情況下，可以使用**static**關鍵字。

1. 當您在檔案範圍（全域和/或命名空間範圍）宣告變數或函式時， **static**關鍵字會指定變數或函數具有內部連結。 當您宣告變數時，變數會擁有靜態持續期間，且編譯器會將其初始化為 0 (除非您指定其他值)。

1. 當您在函式中宣告變數時， **static**關鍵字會指定變數在呼叫該函式之間保留其狀態。

1. 當您在類別宣告中宣告資料成員時， **static**關鍵字會指定該成員的一個複本由類別的所有實例共用。 靜態資料成員必須以檔案範圍定義。 您宣告為**const static**的整數資料成員可以有初始化運算式。

1. 當您在類別宣告中宣告成員函式時， **static**關鍵字會指定該函式是由類別的所有實例共用。 因為函式沒有隱含的**this**指標，所以靜態成員函數無法存取實例成員。 若要存取執行個體成員，請使用本身為執行個體指標或參考的參數宣告函式。

1. 您無法將等位的成員宣告為靜態。 不過，全域宣告的匿名等位必須明確宣告為**static**。

這個範例示範在函式中宣告為**static**的變數如何保留其在呼叫該函式之間的狀態。

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

這個範例示範如何在類別中使用**靜態**。

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

這個範例會顯示成員函式中宣告為**static**的區域變數。 靜態變數可供整個程式使用，而類型的所有執行個體會共用靜態變數的相同複本。

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

從 C++11 開始，保證靜態區域變數初始化為執行緒安全。 這項功能有時稱為*魔術靜態*。 不過，在多執行緒應用程式中，必須同步處理所有後續指派。 使用[/zc： threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)旗標可停用安全線程靜態初始化功能，以避免依賴 CRT。

## <a name="extern"></a>extern

宣告為**extern**的物件和變數會宣告在另一個轉譯單位或封閉範圍中定義為具有外部連結的物件。 如需詳細資訊，請參閱[extern](extern-cpp.md)和[轉譯單位和連結](program-and-linkage-cpp.md)。

## <a name="thread_local"></a>thread_local （c + + 11）

使用**thread_local**指定名稱宣告的變數，只能在建立它的執行緒上存取。 變數會在建立執行緒時建立，並在終結執行緒時終結。 每個執行緒都有它自己的變數複本。 在 Windows 上， **thread_local**的功能等同于 Microsoft 專有的[__declspec （thread）](../cpp/thread.md)屬性。

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

**Thread_local**規範的注意事項：

- Dll 中的動態初始化執行緒區域變數可能無法在所有呼叫執行緒上正確初始化。 如需詳細資訊，請參閱[執行緒](thread.md)。

- **Thread_local**規範可以與**static**或**extern**結合。

- 您只能將**thread_local**套用至資料宣告和定義;**thread_local**不能用在函式宣告或定義上。

- 您只能在具有靜態儲存期的資料項目上指定**thread_local** 。 這包括全域資料物件（**靜態**和**外部**）、本機靜態物件，以及類別的靜態資料成員。 如果未提供其他儲存類別，則任何宣告**thread_local**的區域變數都會隱含為靜態。換句話說，在區塊範圍**thread_local**相當於 `thread_local static`。

- 不論是在相同的檔案還是不同的檔案中進行宣告和定義，都必須同時為執行緒區域物件的宣告和定義指定**thread_local** 。

在 Windows 上， **thread_local**的功能等同于[__declspec （thread）](../cpp/thread.md) ，不同之處在于 **__declspec （thread）** 可以套用至類型定義，而且在 C 程式碼中有效。 盡可能使用**thread_local** ，因為它是C++標準的一部分，因此更具可攜性。

##  <a name="register"></a>參加

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： **register**關鍵字不再是支援的儲存類別。 關鍵字仍然保留在標準中，供日後使用。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>範例：自動與靜態初始化

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

這個範例示範如何和何時初始化物件 `I1`、`I2`和 `I3`，以及何時終結它們。

關於此程式，有幾點需要注意：

- 首先，`I1` 和 `I2` 會在控制流程離開其定義所在的區塊時自動終結。

- 其次，在 C++ 中，不需要在區塊開頭宣告物件或變數。 再者，只有在控制流程到達其定義時，這些物件才會初始化 （`I2` 和 `I3` 是這類定義的範例）。輸出會顯示其初始化的確切時間。

- 最後，靜態區域變數 (例如 `I3`) 會在程式執行期間保留其值，不過會在程式終止時終結。

## <a name="see-also"></a>另請參閱

[宣告和定義](../cpp/declarations-and-definitions-cpp.md)