---
title: "儲存類別 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "thread_local_cpp"
  - "external_cpp"
  - "static_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "儲存類別, 基本概念"
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 儲存類別 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 變數宣告內容中的*「儲存類別」*\(Storage Class\) 是一種類型規範，可控管物件的存留期、連結和記憶體位置。  指定的物件只能有一個儲存類別。  除非使用 `extern`、`static` 或 `thread_local` 規範另外指定，否則區塊內定義的變數會具有自動儲存區。  自動物件和變數沒有連結；區塊外部的程式碼看不到它們。  
  
 **備註**  
  
1.  [mutable](../cpp/mutable-data-members-cpp.md) 關鍵字可視為儲存類別規範。  不過，它只能在類別定義的成員清單中使用。  
  
2.  從 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 開始，`auto` 關鍵字不再是 C\+\+ 儲存類別規範，而且 `register` 關鍵字已遭取代。  
  
-   [靜態](#static)  
  
-   [extern](#extern)  
  
-   [thread\_local](#thread_local)  
  
## 靜態  
 `static` 關鍵字可以用來在全域範圍、命名空間範圍和類別範圍宣告變數和函式。  靜態變數也可以在區域範圍內進行宣告。  
  
 靜態持續期間是指，物件或變數會在程式啟動時配置，並在程式結束時解除配置。  外部連結是指，變數名稱在變數宣告所在的檔案外部可見。  相反地，內部連結是指，名稱在變數宣告所在的檔案外部不可見。  根據預設，全域命名空間中所定義的物件或變數具有靜態持續期間和外部連結。  `static` 關鍵字可在下列狀況中使用。  
  
1.  當您在檔案範圍 \(全域和\/或命名空間範圍\) 宣告變數或函式時，`static` 關鍵字會指定變數或函式擁有內部連結。  當您宣告變數時，變數會擁有靜態持續期間，且編譯器會將其初始化為 0 \(除非您指定其他值\)。  
  
2.  當您在函式中宣告變數時，`static` 關鍵字會指定該變數在兩次呼叫該函式之間保留其狀態。  
  
3.  當您在類別宣告中宣告資料成員時，`static` 關鍵字會指定成員的一個複本供類別的所有執行個體共用。  靜態資料成員必須以檔案範圍定義。  您宣告為 `const` `static` 的整數資料成員可以擁有初始設定式。  
  
4.  當您在類別宣告中宣告成員函式時，`static` 關鍵字會指定該函式供類別的所有執行個體共用。  靜態成員函式無法存取執行個體成員，因為函式沒有隱含的 `this` 指標。  若要存取執行個體成員，請使用本身為執行個體指標或參考的參數宣告函式。  
  
5.  您無法將等位的成員宣告為靜態。  不過，全域宣告的匿名等位必須明確宣告為 `static`。  
  
 下列範例將示範在函式中宣告為 `static` 的變數如何在兩次呼叫該函式之間保留其狀態。  
  
```  
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
  
  **nStatic is 0**  
**nStatic is 1**  
**nStatic is 3**  
**nStatic is 6**  
**nStatic is 10** 下列範例將示範類別中 `static` 的用法。  
  
```  
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
  
  **0**  
**0**  
**1**  
**1**  
**2**  
**2**  
**3**  
**3** 下列範例將示範在成員函式中宣告為 `static` 的區域變數。  靜態變數可供整個程式使用，而類型的所有執行個體會共用靜態變數的相同複本。  
  
```  
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
  
  **var \!\= value**  
**var \=\= value** 從 C\+\+11 開始，保證靜態區域變數初始化為執行緒安全。  這項功能有時稱為*「識別靜態」*\(Magic Static\)。  不過，在多執行緒應用程式中，必須同步處理所有後續指派。  若要避免採用 CRT 相依性，使用 \/Zc:threadSafeInit\- 旗標可停用安全執行緒的靜態變數功能。  
  
## extern  
 宣告為 `extern` 的物件和變數，會將在另一個轉譯單位或封閉範圍中定義的物件，宣告為具有外部連結。  
  
 宣告具有  **儲存類別的 `extern`const** 變數會強制該變數具有外部連結。  定義轉譯單位時可以初始化 **extern const** 變數。  若在定義轉譯單位以外的轉譯單位中初始化，會產生未定義的結果。  如需詳細資訊，請參閱[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)。  
  
 下列程式碼顯示兩個 `extern` 宣告，即 `DefinedElsewhere` \(參考不同轉譯單位中定義的名稱\) 和 `DefinedHere` \(參考封閉範圍中定義的名稱\)：  
  
```  
// external.cpp  
// defined in another translation unit  
extern int DefinedElsewhere;     
int main() {  
   int DefinedHere;   
   {  
      // refers to DefinedHere in the enclosing scope  
      extern int DefinedHere;  
    }  
}  
```  
  
## thread\_local \(C\+\+11\)  
 如果變數是使用 `thread_local` 規範所宣告，則只有在建立它的執行緒上才能進行存取。  變數會在建立執行緒時建立，並在終結執行緒時終結。  每個執行緒都有它自己的變數複本。  在 Windows 上，`thread_local` 的功能相當於 Microsoft 特定 [\_\_declspec\( thread \)](../cpp/thread.md) 屬性。  
  
```  
thread_local float f = 42.0; //global namespace  
  
struct C // cannot be applied to type definition  
{  
thread_local int i; //local  
thread_local static char buf[10]; // local and static  
};  
  
void DoSomething()  
{  
thread_local C my_struct; // Apply  thread_local to a variable  
}  
```  
  
1.  thread\_local 規範可能會與 `static` 或 `extern` 一起使用。  
  
2.  您只能將 `thread_local` 套用至資料宣告和定義；**thread\_local** 無法用於函式宣告或定義中。  
  
3.  使用 `thread_local` 可能會干擾 DLL 匯入的[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**  
  
4.  在 XP 系統上，如果 DLL 使用 `thread_local` 資料並透過 LoadLibrary 動態予以載入，則 `thread_local` 可能無法正確運作。  
  
5.  您只能在具有靜態儲存持續時間的資料項目上指定 `thread_local`。  這包括全域資料物件 \(**static** 和 `extern`\)、區域靜態物件和類別的靜態資料成員。  您無法使用 **thread\_local** 來宣告自動資料物件。  
  
6.  不論是在相同的檔案還是不同的檔案進行宣告和定義，您都必須指定執行緒區域物件之宣告和定義的 `thread_local`。  
  
 在 Windows 中，`thread_local` 的功能相當於 [\_\_declspec\(thread\)](../cpp/thread.md)，差異在於 \_\_declspec\(thread\) 可以套用至類型定義並在 C 程式碼中有效。  只要可能，都請使用 `thread_local`，因為它是 C\+\+ 標準的一部分，因此更具可攜性。  
  
 如需詳細資訊，請參閱[執行緒區域儲存區](../parallel/thread-local-storage-tls.md)。  
  
## 註冊  
 在 C\+\+11 中，**register** 關鍵字已遭取代。  它會將變數指定為儲存在電腦的暫存器中 \(如果可能\)。  只有函式引數和區域變數可以使用暫存器儲存類別進行宣告。  
  
```  
register int num;  
```  
  
 如同自動變數，暫存器變數只能保存到宣告區段的結尾。  
  
 編譯器不接受使用者要求的暫存器變數，而是在全域最佳化開啟時自行選擇暫存器。  不過，編譯器接受其他所有與 [register](http://msdn.microsoft.com/zh-tw/5b66905a-2f7f-4918-bb55-5e66d4bc50f9) 關鍵字相關的語意。  
  
 如果在使用 register 所宣告的物件上使用傳址運算子 \(**&**\)，編譯器必須將該物件放在記憶體中，而非暫存器中。  
  
## 範例：automatic vs.靜態初始化  
 區域自動物件或變數會在每次控制流程到達其定義時初始化。  區域靜態物件或變數會在控制流程第一次到達其定義時初始化。  
  
 請考慮下列範例，範例中會定義記錄物件初始化和解構的類別，然後再定義三個物件 `I1`、`I2` 和 `I3`：  
  
```  
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
   if( szWhat != 0 && strlen( szWhat ) > 0 ) {  
      // Allocate storage for szObjName, then copy  
      // initializer szWhat into szObjName, using  
      // secured CRT functions.  
      sizeofObjName = strlen( szWhat ) + 1;  
  
      szObjName = new char[ sizeofObjName ];  
      strcpy_s( szObjName, sizeofObjName, szWhat );  
  
      cout << "Initializing: " << szObjName << "\n";  
   }  
   else  
      szObjName = 0;  
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
  
  **Initializing: Auto I1**  
**In block.  Initializing: Auto I2**  
**Initializing: Static I3**  
**Destroying: Auto I2**  
**Exited block.  Destroying: Auto I1**  
**Destroying: Static I3**  上述程式碼示範了如何及何時將 `I1`、`I2` 和 `I3` 物件初始化，以及何時將這些物件終結。  
  
 關於程式，有幾點必須注意。  
  
 首先，`I1` 和 `I2` 會在控制流程離開其定義所在的區塊時自動終結。  
  
 其次，在 C\+\+ 中，不需要在區塊開頭宣告物件或變數。  再者，只有在控制流程到達其定義時，這些物件才會初始化   \(這類定義的範例包括 `I2` 和 `I3`\)。 輸出中會顯示它們初始化的確切時間。  
  
 最後，靜態區域變數 \(例如 `I3`\) 會在程式執行期間保留其值，不過會在程式終止時終結。  
  
## 請參閱  
 [宣告和定義](../cpp/declarations-and-definitions-cpp.md)