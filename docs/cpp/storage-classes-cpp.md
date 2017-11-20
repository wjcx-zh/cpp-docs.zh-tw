---
title: "儲存類別 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
dev_langs: C++
helpviewer_keywords: storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3830f91683399eba4784b5348ca252e9caa22d57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="storage-classes-c"></a>儲存類別 (C++)  
  
A*儲存類別*的 c + + 內容中的變數宣告為類型規範，可控管物件的存留期、 連結和記憶體位置。 指定的物件只能有一個儲存類別。 除非使用 `extern`、`static` 或 `thread_local` 規範另外指定，否則區塊內定義的變數會具有自動儲存區。 自動物件和變數沒有連結；區塊外部的程式碼看不到它們。  
  
**備註**  
  
1.  [可變動](../cpp/mutable-data-members-cpp.md)關鍵字可視為儲存類別規範。 不過，它只能在類別定義的成員清單中使用。  
  
2.  **Visual c + + 2010年及更新版本：** `auto`關鍵字不再是 c + + 儲存類別規範，而`register`關鍵字已被取代。 **Visual Studio 2017 15.3 和更新版本：** (適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):`register`關鍵字已不再支援的存放裝置類別。 關鍵字是仍保留供未來使用的標準。 
```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>本節內容：
  
-   [static](#static)  
-   [extern](#extern)  
-   [thread_local](#thread_local)

<a name="static"></a>
  
## <a name="static"></a>靜態  
  
`static` 關鍵字可以用來在全域範圍、命名空間範圍和類別範圍宣告變數和函式。 靜態變數也可以在區域範圍內進行宣告。  
  
靜態持續期間是指，物件或變數會在程式啟動時配置，並在程式結束時解除配置。 外部連結是指，變數名稱在變數宣告所在的檔案外部可見。 相反地，內部連結是指，名稱在變數宣告所在的檔案外部不可見。 根據預設，全域命名空間中所定義的物件或變數具有靜態持續期間和外部連結。 `static` 關鍵字可在下列狀況中使用。  
  
1.  當您在檔案範圍 (全域和/或命名空間範圍) 宣告變數或函式時，`static` 關鍵字會指定變數或函式擁有內部連結。 當您宣告變數時，變數會擁有靜態持續期間，且編譯器會將其初始化為 0 (除非您指定其他值)。  
  
2.  當您在函式中宣告變數時，`static` 關鍵字會指定該變數在兩次呼叫該函式之間保留其狀態。  
  
3.  當您在類別宣告中宣告資料成員時，`static` 關鍵字會指定成員的一個複本供類別的所有執行個體共用。 靜態資料成員必須以檔案範圍定義。 宣告為整數類資料成員`const static`可以有初始設定式。  
  
4.  當您在類別宣告中宣告成員函式時，`static` 關鍵字會指定該函式供類別的所有執行個體共用。 靜態成員函式無法存取執行個體成員，因為函式沒有隱含的 `this` 指標。 若要存取執行個體成員，請使用本身為執行個體指標或參考的參數宣告函式。  
  
5.  您無法將等位的成員宣告為靜態。 不過，全域宣告的匿名等位必須明確宣告為 `static`。  
  
這個範例會示範如何宣告的變數`static`函式中會保留其對該函式的呼叫之間的狀態。  
  
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
  
這個範例示範如何使用`static`類別中。  
  
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
  
此範例示範宣告的區域變數`static`的成員函式。 靜態變數可供整個程式使用，而類型的所有執行個體會共用靜態變數的相同複本。  
  
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
  
從 C++11 開始，保證靜態區域變數初始化為執行緒安全。 這項功能有時稱為*magic 靜態變數*。 不過，在多執行緒應用程式中，必須同步處理所有後續指派。 安全執行緒的靜態初始設定 」 功能可以藉由停用[/zc: threadsafeinit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)旗標，若要避免採用 CRT 上的相依性。  
  
<a name="extern"></a>  
  
## <a name="extern"></a>extern  
  
宣告為 `extern` 的物件和變數，會將在另一個轉譯單位或封閉範圍中定義的物件，宣告為具有外部連結。  
  
宣告`const`變數`extern`儲存類別會強制該變數具有外部連結。 初始`extern const`定義轉譯單位中不允許變數。 若在定義轉譯單位以外的轉譯單位中初始化，會產生未定義的結果。 如需詳細資訊，請參閱[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)  
  
下列程式碼顯示兩個 `extern` 宣告，即 `DefinedElsewhere` (參考不同轉譯單位中定義的名稱) 和 `DefinedHere` (參考封閉範圍中定義的名稱)：  
  
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
  
<a name="thread_local"></a>  
  
## <a name="threadlocal-c11"></a>thread_local (C++11)  
  
如果變數是使用 `thread_local` 規範所宣告，則只有在建立它的執行緒上才能進行存取。 變數會在建立執行緒時建立，並在終結執行緒時終結。 每個執行緒都有它自己的變數複本。 在 Windows 中，`thread_local`其作用相當於 Microsoft 專有[__declspec (thread)](../cpp/thread.md)屬性。  
  
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
  
-  `thread_local`規範可能會與結合`static`或`extern`。  
  
-  您可以套用`thread_local`至資料宣告和定義;`thread_local`不能在函式宣告或定義。  
  
-  使用`thread_local`可能會干擾[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)DLL 匯入。 
  
-  在 XP 系統上`thread_local`可能無法正確運作如果 DLL 使用`thread_local`資料並透過動態載入`LoadLibrary`。  
  
-  您只能在具有靜態儲存持續時間的資料項目上指定 `thread_local`。 這包括全域資料物件 (同時`static`和`extern`)、 區域靜態物件和類別的靜態資料成員。 任何本機變數宣告`thread_local`是隱含靜態，如果沒有其他儲存類別會提供; 換句話說，在區塊範圍`thread_local`相當於`thread_local static`。 
  
-  不論是在相同的檔案還是不同的檔案進行宣告和定義，您都必須指定執行緒區域物件之宣告和定義的 `thread_local`。  
  
在 Windows 中，`thread_local`其作用相當於[__declspec （thread)](../cpp/thread.md)不同之處在於`__declspec(thread)`可以套用至類型定義並在 C 程式碼中有效。 只要可能，都請使用 `thread_local`，因為它是 C++ 標準的一部分，因此更具可攜性。  
  
##  <a name="register"></a>暫存器  
**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):`register`關鍵字已不再支援的存放裝置類別。 關鍵字是仍保留供未來使用的標準。 

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
  
此範例示範如何及何時物件`I1`， `I2`，和`I3`會初始化並終結時。  
  
有數個程式的相關要點：  
  
- 首先，`I1` 和 `I2` 會在控制流程離開其定義所在的區塊時自動終結。  
  
- 其次，在 C++ 中，不需要在區塊開頭宣告物件或變數。 再者，只有在控制流程到達其定義時，這些物件才會初始化  (這類定義的範例包括 `I2` 和 `I3`)。輸出中會顯示它們初始化的確切時間。  
  
- 最後，靜態區域變數 (例如 `I3`) 會在程式執行期間保留其值，不過會在程式終止時終結。  
  
## <a name="see-also"></a>另請參閱  
  
 [宣告和定義](../cpp/declarations-and-definitions-cpp.md)
