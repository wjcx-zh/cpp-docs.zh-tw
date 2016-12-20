---
title: "C++ 類型系統 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 類型系統 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「*類型*」的概念在 C\+\+ 中非常重要。  每個變數、函式引數和函式傳回值都必須有類型才能編譯。  此外，在評估之前，編譯器會以隱含的方式指定每一個運算式 \(包括常值\) 的類型。  部分類型範例包括可儲存整數值的 `int`、可儲存浮點數值 \(也稱為「*純量*」資料類型\) 的 `double`，或可儲存文字的標準程式庫類別 [std::basic\_string](../standard-library/basic-string-class.md)。  您可以藉由定義 `class` 或 `struct`，建立自己的類型。  此類型會指定配置給變數 \(或運算式結果\) 的記憶體數量、可在該變數中存放的值種類、這些值 \(位元模式\) 的解譯方式，以及可對其執行的作業。  本文包含 C\+\+ 類型系統主要功能的簡略概觀。  
  
## 用語  
 **變數**：資料數量的符號名稱，可讓您在其定義的所在程式碼之所有範圍中，使用此名稱來存取其所指的資料。  在 C\+\+ 中，「變數」通常指的是純量資料類型的執行個體，而其他類型的執行個體通常稱為「物件」。  
  
 **物件**：為了簡化和一致起見，本文件使用「物件」這個詞彙來指稱類別或結構的所有執行個體，在廣義上使用時則包括所有的類型，甚至純量變數。  
  
 **POD 類型** \(一般舊資料\)：C\+\+ 中的這個非正式資料類型分類指的是純量 \(請參閱＜基本類型＞一節\) 或「*POD 類別*」的類型。  POD 類別的靜態資料成員同時也是 POD，沒有使用者定義的建構函式、使用者定義解構函式或使用者定義的指派運算子。  此外，POD 類別沒有虛擬函式、沒有基底類別，也沒有私用或受保護的非靜態資料成員。  POD 類型通常用於外部資料交換，例如以 C 語言撰寫的模組 \(其中只有 POD 類型\)。  
  
## 指定變數和函式類型  
 C\+\+ 是一種「*強類型*」語言，同時也是「*靜態類型*」；每個物件都有一個類型，且該類型永遠不會變更 \(勿與靜態資料物件混淆\)。           
 當您在程式碼中**宣告變數時**，您必須明確指定其類型，或使用 `auto` 關鍵字指示編譯器由初始設定式推算類型。           
 當您在程式碼中**宣告函式時**，您必須指定每個引數及其傳回值的類型，如果函式不傳回任何值，則指定為 `void`。  例外情況是在您使用函式樣板，可允許任意類型的引數。  
  
 在您初次宣告變數之後，就不能再變更其類型。  不過，您可以將變數值或函式的傳回值複製到另一個不同類型的變數。  這類作業稱為「*類型轉換*」，有時候是必要的，但也是造成資料遺失或無效的可能原因。  
  
 當您宣告 POD 類型的變數時，強烈建議您將其初始化，也就是指定其初始值。  在您初始化變數以前，變數都會包含由先前遺留在該記憶體位置之任何位元所構成的「垃圾」值。  這是一個要記住的 C\+\+ 重要層面，如果您是從另一個用來處理初始化的語言轉換而來時則更是如此。  宣告非 POD 類別類型的變數時，建構函式會處理初始化。  
  
 下列範例示範一些簡單的變數宣告，這些宣告各有一些描述。  這個範例也會示範編譯器如何使用類型資訊允許或不允許對變數進行某些後續作業。  
  
```  
  
int result = 0;              // Declare and initialize an integer.  
double coefficient = 10.8;   // Declare and initialize a floating   
                             // point value.  
auto name = "Lady G.";       // Declare a variable and let compiler   
                             // deduce the type.  
auto address;                // error. Compiler cannot deduce a type   
                             // without an intializing value.  
age = 12;                    // error. Variable declaration must  
                             // specify a type or use auto!  
result = "Kenny G.";         // error. Can’t assign text to an int.  
string result = "zero";      // error. Can’t redefine a variable with  
                             // new type.  
int maxValue;                // Not recommended! maxValue contains   
                             // garbage bits until it is initialized.  
  
```  
  
## 基本 \(內建\) 類型  
 有別於某些程式語言，C\+\+ 並沒有可衍生出所有其他類型的通用基底類型。  語言的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 實作包含許多「*基本類型*」，也稱為「*內建類型*」。  基本類型包括數值類型 \(例如 `int`、`double`、`long`、`bool`\)，以及分別適用於 ASCII 和 UNICODE 字元的 `char` 和 `wchar_t` 類型。  大部分基本類型 \(`bool`、`double`、`wchar_t` 及相關類型除外\) 都有不帶正負號的版本，這會修改變數所能儲存的值範圍。  例如 `int` 儲存 32 位元帶正負號的整數，可表示從 \-2,147,483,648 到 2,147,483,647 的值。  `unsigned int`，也會儲存為 32 位元，可以儲存從 0 到 4,294,967,295 的值。  每個案例中的可能值總數都相同；只有範圍不同。  
  
 基本類型是由編譯器辨識，其內建規則會控制可對這些類型執行哪些作業，以及如何轉換成其他基本類型。  如需內建類型及其大小和數值限制的完整清單，請參閱[基本類型](../cpp/fundamental-types-cpp.md)。  
  
 下圖顯示內建類型的相對大小：  
  
 ![內建類型的大小 &#40;以位元組為單位&#41;](../cpp/media/built-intypesizes.png "Built\-inTYpeSizes")  
  
 下表列出最常用的基本類型：  
  
|類型|大小|註解|  
|--------|--------|--------|  
|int|4 個位元組|整數值的預設選項。|  
|double|8 個位元組|浮點值的預設選項。|  
|bool|1 個位元組|表示可以是 true 或 false 的值。|  
|char|1 個位元組|使用較舊 C\-Style 字串或 std::string 物件中永遠不需要轉換成 UNICODE 之的 ASCII 字元。|  
|wchar\_t|2 個位元組|表示可能以 UNICODE 格式 \(在 Windows 上為 UTF\-16，而其他作業系統可能不同\) 編碼的「寬」字元值。  這是用於 `std::wstring` 類型字串的字元類型。|  
|unsigned char|1 個位元組|C\+\+ 沒有內建 `byte` 類型。使用 unsigned char 表示位元組值。|  
|unsigned int|4 個位元組|位元旗標的預設選項。|  
|long long|8 個位元組|表示極大的整數值。|  
  
## void 類型  
 `void` 類型屬於特殊類型；您無法宣告 `void` 類型的變數，但是可以宣告 `void *` 類型 \(`void` 的指標\) 的變數，有時在配置未經處理 \(不具類型\) 的記憶體時，這麼做是必要的。  然而，`void` 的指標不是類型安全，強烈建議不要在現代 C\+\+ 使用。  在函式宣告中，`void` 傳回值表示函式未傳回值；這是 `void` 常見的適當用途。  雖然 C 語言要求含有零個參數的函式必須在參數清單中宣告 `void` \(例如，`fou(void)`\)，但在現代 C\+\+ 中不建議使用這種作法，反而應該宣告為 `fou()`。  如需詳細資訊，請參閱 [類型轉換和類型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。  
  
## 常數類型限定詞  
 任何內建或使用者定義的類型都可以由 const 關鍵字限定。  此外，成員函式可能是受 `const` 限定的，甚至是 `const` 多載。  `const` 類型的值，在初始化之後，就無法修改。  
  
```  
  
const double PI = 3.1415;  
PI = .75 //Error. Cannot modify const variable.  
  
```  
  
 `const` 限定詞廣泛使用在函式和變數宣告中，而「常數正確性」是 C\+\+ 中的重要概念；基本上就是要使用 `const` 確保該值在編譯時不會無意間遭到修改值。  如需詳細資訊，請參閱 [const](../cpp/const-cpp.md)。  
  
 `const` 類型與其非 Const 版本不同，例如，`const int` 類型與 `int` 類型不同。  當您必須移除變數中的「*常數性*」\(Const\-ness\) 時，您可以對這些不常見的狀況使用 C\+\+ `const_cast` 運算子。  如需詳細資訊，請參閱 [類型轉換和類型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。  
  
## 字串類型  
 嚴格來說，C\+\+ 語言沒有內建的「字串」類型；`char` 和 `wchar_t` 只能儲存單一字元；您必須宣告這些類型的陣列，將結尾 null 值 \(例如，ASCII `‘\0’`\) 加入至超過最後一個有效字元之後的一個陣列元素中，以建立近似的字串 \(也稱為「C\-Style 字串」\)。  C\-Style 字串需要撰寫更多程式碼或使用外部字串公用程式庫函式。  但是在現代 C\+\+ 中，我們有標準程式庫類型 `std::string` \(用於 8 位元 `char` 類型的字元字串\) 或 `std::wstring` \(用於 16 位元 `wchar_t` 類型的字元字串\)。  這些 STL 容器可以視為原生字串類型，因為它們是標準程式庫的一部分，任何標準 C\+\+ 建置環境都會加以納入。  只要使用 `#include <string>` 指示詞，即可在您的程式中使用這些類型。\(如果您正在使用 MFC 或 ATL，CString 類別也是可用的，但是它不是 C\+\+ 標準的一部分\)。強烈建議您不要在現代 C\+\+ 中使用以 null 終止的字元陣列 \(舊稱 C\-Style 字串\)。  
  
## 使用者定義類型  
 當您定義 `class`、`struct`、`union` 或 `enum` 時，程式碼的其餘部分都會使用該建構，就如同基本類型一般。  它在記憶體中的大小已知，而且套用了有關其在編譯時期檢查、執行階段和程式存留期之使用方式的特定規則。  基本內建類型和使用者定義類型之間的主要差異如下：  
  
-   編譯器沒有使用者定義類型的內建知識。  在編譯過程中第一次遇到這個定義時，它會「得知」類型。  
  
-   您會藉由定義 \(透過多載\) 適當的運算子做為類別成員或非成員函式，指定對類型執行哪些作業，以及如何轉換為其他類型。  如需詳細資訊，請參閱 [多載 （c \+ \+）](../misc/overloading-cpp.md)。  
  
-   它們不一定要是靜態類型 \(物件類型永不變更的規則\)。  透過「*繼承*」和「*多型*」的機制，宣告為類別的使用者定義類型 \(稱為類別的物件執行個體\) 的變數可能在執行階段會有不同於編譯時期的類型。  如需詳細資訊，請參閱 [繼承](../cpp/inheritance-cpp.md)。  
  
## 指標類型  
 在 C 語言的最早期版本中，C\+\+ 繼續讓您使用特殊宣告子 `*` \(星號\) 宣告指標類型的變數。  指標類型會將在儲存實際資料值之位置的位址儲存在記憶體中。  在現代 C\+\+ 中，這些就稱為「*原始指標*」\(Raw Pointer\)，可在程式碼中透過特殊運算子 `*` \(星號\) 或 `->` \(破折號和大於\) 進行存取。  這就稱為「*取值*」，而您會使用哪一個，取決於您要取值的是純量的指標，還是物件中成員的指標。  處理指標類型一直以來都是 C 及 C\+\+ 程式開發最具挑戰性和令人困惑的一面。  本節說明一些使用原始指標的基本資訊和做法，以便在您需要原始指標時有所幫助，但是在現代 C\+\+ 中完全不再需要 \(或不建議\) 使用原始指標取得物件擁有權，因為發展了[智慧型指標](../cpp/smart-pointers-modern-cpp.md) \(本節結尾有更多討論\)。  使用原始指標觀察物件仍然有用且安全，但若要將其用於物件擁有權，就必須小心使用，並非常仔細地考量如何建立和終結所擁有的物件。  
  
 您首先應該知道的事就是，宣告原始指標變數時只會配置，在儲存該指標在被取值時所參考之記憶體位置位址時所需的記憶體。  資料值本身的記憶體配置 \(也稱為「*備份存放區*」\(backing store\)\) 尚未配置。  換句話說，宣告原始指標變數，即是在建立記憶體位址變數，而不是實際資料變數。  在確定變數包含可用於備份存放區的有效位址之前就先取值指標變數，會導致程式中產生未定義的行為 \(通常是嚴重錯誤\)。  下列範例示範這種錯誤：  
  
```  
  
int* pNumber;       // Declare a pointer-to-int variable.  
*pNumber = 10;      // error. Although this may compile, it is  
                    // a serious error. We are dereferencing an  
                    // uninitialized pointer variable with no  
                    // allocated memory to point to.  
  
```  
  
 這個範例會對指標類型取值，但不配置任何記憶體的來儲存指派給它的實際整數資料或有效記憶體位址。  下列程式碼示範這些錯誤：  
  
```  
  
    int number = 10;          // Declare and initialize a local integer  
                              // variable for data backing store.  
    int* pNumber = &number;   // Declare and initialize a local integer  
                              // pointer variable to a valid memory  
                              // address to that backing store.  
...  
    *pNumber = 41;            // Dereference and store a new value in   
                              // the memory pointed to by  
                              // pNumber, the integer variable called  
                              // “number”. Note “number” was changed, not  
                              // “pNumber”.  
  
```  
  
 更正的程式碼範例會使用本機堆疊記憶體，建立 `pNumber` 所指向的備份存放區。  我們為了簡單起見使用基本類型。  實際上，指標的備份存放區通常是在稱為「*堆積*」之記憶體區域 \(或「可用存放區」\) 中，使用 `new` 關鍵字 \(在 C\-Style 程式設計中，使用較舊的 `malloc()` C 執行階段程式庫函式\) 所動態配置的使用者定義類型。  一旦配置後，這些「變數」通常就稱為「物件」，特別是在變數根據類別定義配置時。  使用 `new` 配置的記憶體必須由對應的 `delete` 陳述式刪除 \(或者，如果是使用 `malloc()` 函式配置的，則由 C 執行階段函式 `free()` 刪除\)。  
  
 不過，動態配置物件經常會忘記刪除，特別是在複雜程式碼中，造成資源 Bug，稱為「*記憶體流失*」。  因此，強烈建議您不要在現代 C\+\+ 使用原始指標。  將原始指標包裝在[智慧型指標](../cpp/smart-pointers-modern-cpp.md)中，幾乎都是較好的方式，這樣就會在叫用其解構函式時 \(當程式碼超出智慧型指標範圍時\) 自動釋放記憶體；使用智慧型指標，您幾乎是在 C\+\+ 程式中排除了整個類別的 Bug。  下列範例中，假設 `MyClass` 是具有公用方法 `DoSomeWork();` 的使用者定義類型  
  
```  
  
void someFunction() {  
    unique_ptr<MyClass> pMc(new MyClass);  
    pMc->DoSomeWork();  
}  
  // No memory leak. Out-of-scope automatically calls the destructor  
  // for the unique_ptr, freeing the resource.  
  
```  
  
 如需智慧型指標的詳細資訊，請參閱[智慧型指標](../cpp/smart-pointers-modern-cpp.md)。  
  
 如需指標轉換的詳細資訊，請參閱[類型轉換和類型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。  
  
 如需一般指標的詳細資訊，請參閱[指標](../cpp/pointers-cpp.md)。  
  
## Windows 資料類型  
 在 C 和 C\+\+ 的傳統 Win32 程式設計中，大部分函式會使用 Windows 專有的 typedef 和 \#define 巨集 \(定義於 `windef.h`\) 來指定參數和傳回值的類型。  這些「Windows 資料類型」多半只是指定給 C\/C\+\+ 內建類型的特殊名稱 \(別名\)。  如需這些 Typedef 和前置處理器定義的完整清單，請參閱 [Windows Data Types](http://msdn.microsoft.com/zh-tw/4553cafc-450e-4493-a4d4-cb6e2f274d46)。  這些 Typedef \(例如 HRESULT 和 LCID\) 很有用而且是描述性的。  其他如 INT，並無特殊意義，只是基本 C\+\+ 類型的別名而已。  其他 Windows 資料類型有從 C 程式設計和 16 位元處理器時代保留下來的名稱，在現代硬體或作業系統上並無用處或意義。  其中也有與 Windows 執行階段程式庫相關聯的特殊資料類型，如 [Windows Runtime base data types](http://msdn.microsoft.com/zh-tw/b5735851-ec07-48c1-92b4-ca9f768096f6)中所列。  在現代 C\+\+ 中，一般的方針就是，除非 Windows 類型傳達有關如何解譯值的額外涵義，否則優先使用 C\+\+ 基本類型。  
  
## 詳細資訊  
 如需 C\+\+ 類型系統的詳細資訊，請參閱下列主題：  
  
|||  
|-|-|  
|[實值類型](../cpp/value-types-modern-cpp.md)|描述「*實值類型*」以及與其用途相關的問題。|  
|[類型轉換和類型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)|描述一般類型轉換問題並顯示如何避免這些問題。|  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)