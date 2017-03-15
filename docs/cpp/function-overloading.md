---
title: "函式多載 | Microsoft Docs"
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
  - "宣告函式, 多載"
  - "函式多載化"
  - "函式多載化, 關於函式多載化"
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 函式多載
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 允許在相同範圍內指定多個同名的函式。  這些函式稱為多載函式，將在＜多載＞中詳細說明。  多載函式可讓程式設計人員根據引數的類型和數目，為函式提供不同的語意。  
  
 例如，接受字串 \(或 **char \***\) 引數的 **print** 函式與接受 **double** 類型引數的相同函式會執行完全不同的工作。  多載允許統一命名，並且可讓程式設計人員不必自創名稱，例如 `print_sz` 或 `print_d`。  下表將說明 C\+\+ 使用函式宣告的哪些部分區分在相同範圍內具有相同名稱的函式群組。  
  
### 多載考量  
  
|函式宣告項目|是否用於多載？|  
|------------|-------------|  
|函式傳回類型|否|  
|引數數目|是|  
|引數類型|是|  
|省略符號是否存在|是|  
|是否使用 `typedef` 名稱|否|  
|未指定的陣列範圍|否|  
|**const** 或 `volatile` \(請參閱下方\)|是|  
  
 雖然函式可以依傳回類型加以區別，但無法在這個基礎上多載。  如果 `Const` 或 `volatile` 在類別中用來套用至類別的 **this** 指標，而不是函式的傳回類型，則只會做為多載的基礎使用。  換句話說，只有在 **const** 或 `volatile` 關鍵字接在宣告中函式的引數清單後面時，才適用多載。  
  
## 範例  
 下列範例將示範如何使用多載。  
  
```  
// function_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <math.h>  
  
// Prototype three print functions.  
int print( char *s );                  // Print a string.  
int print( double dvalue );            // Print a double.  
int print( double dvalue, int prec );  // Print a double with a  
//  given precision.  
using namespace std;  
int main( int argc, char *argv[] )  
{  
const double d = 893094.2987;  
if( argc < 2 )  
    {  
// These calls to print invoke print( char *s ).  
print( "This program requires one argument." );  
print( "The argument specifies the number of" );  
print( "digits precision for the second number" );  
print( "printed." );  
exit(0);  
    }  
  
// Invoke print( double dvalue ).  
print( d );  
  
// Invoke print( double dvalue, int prec ).  
print( d, atoi( argv[1] ) );  
}  
  
// Print a string.  
int print( char *s )  
{  
cout << s << endl;  
return cout.good();  
}  
  
// Print a double in default precision.  
int print( double dvalue )  
{  
cout << dvalue << endl;  
return cout.good();  
}  
  
// Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
int print( double dvalue, int prec )  
{  
// Use table-lookup for rounding/truncation.  
static const double rgPow10[] = {   
10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,  
10E1,  10E2,  10E3,  10E4, 10E5,  10E6  
    };  
const int iPowZero = 6;  
// If precision out of range, just print the number.  
if( prec < -6 || prec > 7 )  
return print( dvalue );  
// Scale, truncate, then rescale.  
dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *  
rgPow10[iPowZero - prec];  
cout << dvalue << endl;  
return cout.good();  
}  
```  
  
 上述程式碼示範檔案範圍中 `print` 函式的多載。  
  
 預設引數不會視為函式類型的一部分。  因此，不會在選取多載函式時使用。  兩個函式的不同之處只有在其預設引數是視為多重定義而不是多載函式。  
  
 無法為多載函式提供預設引數。  
  
 如需有關多載的限制以及多載如何影響 C\+\+ 中其他元素的詳細資訊，請參閱[多載](../misc/overloading-cpp.md)。  
  
## 引數對應  
 多載函式會在為了找出目前範圍中最符合函式呼叫所提供引數的函式宣告項目時選取。  如果找到適合的函式，就會呼叫該函式。  在本內容中，「適合」的意義為下列其中一項：  
  
-   找到完全相符項目。  
  
-   已執行一般轉換。  
  
-   已執行整數提升。  
  
-   有轉換成所需引數類型的標準轉換存在。  
  
-   有轉換成所需引數類型的使用者定義轉換 \(轉換運算子或建構函式\) 存在。  
  
-   找到省略符號所表示的引數。  
  
 編譯器會為每一個引數建立一組候選函式。  候選函式是指函式中該位置的實際引數可以轉換成正式引數的類型。  
  
 每個引數都會有一組建置的「最相符函式」，而且選取的函式是所有集合的交集。  如果交集包含多個函式，則多載會變得模稜兩可並產生錯誤。  最後選取的函式對於至少一個引數來說，永遠是比群組中其他每一個函式更理想的相符項目。  如果情況並非如此 \(如果沒有明顯的最相符項目\)，函式呼叫就會產生錯誤。  
  
 以下列宣告為例 \(在下面的討論中，函式會標記為 `Variant 1`、`Variant 2` 和 `Variant 3` 以便識別\)：  
  
```  
Fraction &Add( Fraction &f, long l );       // Variant 1  
Fraction &Add( long l, Fraction &f );       // Variant 2  
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3  
  
Fraction F1, F2;  
```  
  
 以下列陳述式為例：  
  
```  
F1 = Add( F2, 23 );  
```  
  
 上面的陳述式會建置兩個集合：  
  
|集合 1：第一個引數為 Fraction 類型的候選函式|集合 2：第二個引數可以轉換成 int 類型的候選函式|  
|----------------------------------|---------------------------------|  
|Variant 1|Variant 1 \(`int` 可以使用標準轉換轉換成 `long`\)|  
|Variant 3||  
  
 集合 2 中的函式是指函式中包含從實質參數類型轉換成正式參數類型的隱含轉換，而在這類函式之中，有一個函式的實質參數類型轉換成正式參數類型的「成本」最低。  
  
 這兩個集合的交集為 Variant 1。  模稜兩可函式呼叫的範例如下：  
  
```  
F1 = Add( 3, 6 );  
```  
  
 上述函式呼叫會建立下列集合：  
  
|集合 1：第一個引數為 int 類型的候選函式|集合 2：第二個引數為 int 類型的候選函式|  
|-----------------------------|-----------------------------|  
|Variant 2 \(`int` 可以使用標準轉換轉換成 `long`\)|Variant 1 \(`int` 可以使用標準轉換轉換成 `long`\)|  
  
 請注意，這兩個集合的交集為空集合。  因此，編譯器會產生錯誤訊息。  
  
 為了進行引數比對，有 *n* 個預設引數的函式會視為 *n*\+1 個別函式，而且每個函式各有不同數目的引數。  
  
 省略符號 \(...\) 做為萬用字元使用，它會比對任何實質引數。  如果設計多載函式集合時沒有特別小心，這種情況就可能導致許多模稜兩可的集合出現。  
  
> [!NOTE]
>  在遇到函式呼叫之前，多載函式的模稜兩可情況無法判斷。  遇到函式呼叫時，會為函式呼叫中的每個引數建置集合，如此就可以判斷是否有明確的多載存在。  這表示，模稜兩可的情況可能會持續存在程式碼中，直到特定函式呼叫撤銷這些情況為止。  
  
## 引數類型差異  
 多載函式會區分採用不同初始設定式的各種引數類型。  因此，做為多載的用途時，特定類型的引數以及該類型的參考都會視為相同。  因為它們會採用相同的初始設定式，所以會將它們視為相同。  例如，`max( double, double )` 與 `max( double &, double & )` 會視為相同。  同時宣告兩個這類函式會產生錯誤。  
  
 基於相同的理由，若函式引數的類型經過 **const** 或 `volatile` 修改，則不會視為與多載用途的基底類型不同。  
  
 不過，函式多載機制可以區別以 **const** 和 `volatile` 限定的參考與基底類型的參考。  這樣就可以使用如下所述的程式碼：  
  
```  
// argument_type_differences.cpp  
// compile with: /EHsc /W3  
// C4521 expected  
#include <iostream>  
  
using namespace std;  
class Over {  
public:  
   Over() { cout << "Over default constructor\n"; }  
   Over( Over &o ) { cout << "Over&\n"; }  
   Over( const Over &co ) { cout << "const Over&\n"; }  
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }  
};  
  
int main() {  
   Over o1;            // Calls default constructor.  
   Over o2( o1 );      // Calls Over( Over& ).  
   const Over o3;      // Calls default constructor.  
   Over o4( o3 );      // Calls Over( const Over& ).  
   volatile Over o5;   // Calls default constructor.  
   Over o6( o5 );      // Calls Over( volatile Over& ).  
}  
```  
  
### 輸出  
  
```  
Over default constructor  
Over&  
Over default constructor  
const Over&  
Over default constructor  
volatile Over&  
```  
  
 **const** 和 `volatile` 物件的指標也會視為與多載用途的基底類型指標不同。  
  
## 引數比對和轉換  
 當編譯器嘗試比對實質引數與函式宣告中的引數時，如果找不到完全相符的項目，它可以提供取得正確類型的標準或使用者定義轉換。  轉換的應用會受限於下列規則：  
  
-   若轉換包含多個使用者定義的轉換，則不考慮其序列。  
  
-   若轉換可以藉由移除中繼轉換而縮短，則不考慮其序列。  
  
 轉換產生的序列 \(如果有的話\) 稱為「最相符序列」\(Best Matching Sequence\)。  有幾種方式可使用標準轉換將 `int` 類型的物件轉換為 `unsigned long`類型 \(如[標準轉換](../cpp/standard-conversions.md)中所述\)：  
  
-   從 `int` 轉換成 `long`，然後從 `long` 轉換成 `unsigned long`。  
  
-   從 `int` 轉換成 `unsigned long`。  
  
 第一個序列雖然符合所需目標，但不是最相符序列 \(有較短的序列存在\)。  
  
 下表將顯示稱為一般轉換 \(Trivial Conversion\) 的轉換群組，這類轉換對於判斷最符合序列的效果有限。  有關一般轉換影響序列選擇的執行個體，將在下表後面的清單中討論。  
  
### 一般轉換  
  
|轉換來源類型|轉換目標類型|  
|------------|------------|  
|*type\-name*|*type\-name* **&**|  
|*type\-name* **&**|*type\-name*|  
|*type\-name* **\[ \]**|*type\-name\**|  
|*type\-name* **\(** *argument\-list* **\)**|**\(** *\*type\-name* **\) \(** *argument\-list* **\)**|  
|*type\-name*|**const** *type\-name*|  
|*type\-name*|`volatile` *type\-name*|  
|*type\-name\**|**const** *type\-name\**|  
|*type\-name\**|`volatile` *type\-name\**|  
  
 轉換嘗試執行的序列如下：  
  
1.  完全相符。  呼叫函式所使用的類型與函式原型中所宣告的類型之間完全相符的項目，必定是最相符項目。  一般轉換的序列會分類為完全相符項目。  不過，不進行任何這類轉換的序列通常會比轉換的序列更理想：  
  
    -   從指標到 **const** 的指標 \(`type` **\*** 到 **const** `type` **\***\)。  
  
    -   從指標到 `volatile` \(`type` **\*** 至 `volatile` `type` **\***\)。  
  
    -   從參考到 **const** 的參考 \(`type` **&** 到 **const** `type` **&**\)。  
  
    -   從參考到 `volatile` 的參考 \(`type` **&** 到 `volatile` `type` **&**\)。  
  
2.  使用提升的相符項目。  未分類為完全相符而且只包含整數提升、從 **float** 到 **double** 的轉換，以及一般轉換的任何序列，都會分類為使用提升的相符項目。  雖然不如任何完全相符項目一般合適，但是使用提升的相符項目與使用標準轉換的相符項目相比之下仍較為理想。  
  
3.  使用標準轉換的相符項目。  未分類為完全相符或使用提升的相符項目，而且只包含標準轉換和一般轉換的任何序列，都會分類為使用標準轉換的相符項目。  這個分類適用下列規則：  
  
    -   從指標轉換成衍生類別、轉換成直接或間接基底類別的指標，會比轉換成 **void \*** 或 **const void \*** 更理想。  
  
    -   從指標轉換成衍生類別、轉換成基底類別的指標會產生較佳的相符項目，基底類別也會越接近直接基底類別。  假設類別階層架構如下圖所示。  
  
 ![偏好的轉換](../cpp/media/vc391t1.png "vc391T1")  
用於說明慣用轉換的圖形  
  
 從 `D*` 類型轉換成 `C*` 類型，比從 `D*` 類型轉換成 `B*` 類型更理想。  同樣地，從 `D*` 類型轉換成 `B*` 類型，比從 `D*` 類型轉換成 `A*` 類型更理想。  
  
 相同的規則適用於參考轉換。  從 `D&` 類型轉換成 `C&` 類型，比從 `D&` 類型轉換成 `B&` 類型更理想，以此類推。  
  
 相同的規則適用於指標至成員轉換。  從 `T D::*` 類型轉換成 `T C::*` 類型，比從 `T D::*` 類型轉換成 `T B::*` 類型更理想，以此類推 \(其中 `T` 是成員的類型\)。  
  
 前述規則僅適用於所指的衍生路徑。  以下圖顯示的圖形為例。  
  
 ![顯示偏好轉換的多重繼承](../cpp/media/vc391t2.png "vc391T2")  
用於說明慣用轉換的多重繼承圖形  
  
 從 `C*` 類型轉換成 `B*` 類型，比從 `C*` 類型轉換成 `A*` 類型更理想。  這是因為它們位於相同路徑上，且 `B*` 較接近。  不過，從 `C*` 類型轉換成 `D*` 類型不會比轉換成 `A*` 類型理想，因為轉換遵循的路徑不相同。  
  
1.  使用使用者定義轉換的相符項目  此序列無法分類為完全相符、使用提升的相符項目或使用標準轉換的相符項目。  序列必須只包含使用者定義的轉換、標準轉換或一般轉換，才能分類為透過使用者定義轉換的相符項目。  透過使用者定義轉換的相符項目通常會比使用省略符號的相符項目更理想，但仍不如使用標準轉換的相符項目理想。  
  
2.  使用省略符號的相符項目。  符合宣告中省略符號的任何序列都會分類為使用省略符號的相符項目。  這類相符項目會視為最不理想。  
  
 如果沒有內建的提升或轉換存在，則會套用使用者定義的轉換。  這些轉換會依據所比對的引數類型為基礎選取。  請考慮下列程式碼：  
  
```  
// argument_matching1.cpp  
class UDC  
{  
public:  
   operator int()  
   {  
      return 0;  
   }  
   operator long();  
};  
  
void Print( int i )  
{  
};  
  
UDC udc;  
  
int main()  
{  
   Print( udc );  
}  
```  
  
 可用的 `UDC` 類別使用者定義轉換是來自 `int` 類型和 **long** 類型。  因此，編譯器會考慮所要比對之物件的類型轉換：`UDC`。  轉換為 `int` 存在，並且會加以選取。  
  
 在比對引數的過程中，標準轉換可以同時套用至引數和使用者定義轉換的結果。  因此，下列程式碼可執行：  
  
```  
void LogToFile( long l );  
...  
UDC udc;  
LogToFile( udc );  
```  
  
 前述範例會叫用使用者定義的轉換 **operator long**，將 `udc` 轉換成 **long** 類型。  如果未定義轉換成 **long** 類型的使用者定義轉換，則轉換會以下列方式進行：`UDC` 類型會透過使用者定義轉換來轉換成 `int` 類型。  然後會套用從 `int` 類型到 **long** 類型的標準轉換，以比對宣告中的引數。  
  
 如果比對引數時需要任何使用者定義的轉換，則在評估最符合項目時不會使用標準轉換。  即使是有多個候選函式需要使用者定義轉換的情況也一樣，因為在這類情況下，函式會視為相等。  例如:  
  
```  
// argument_matching2.cpp  
// C2668 expected  
class UDC1  
{  
public:  
   UDC1( int );  // User-defined conversion from int.  
};  
  
class UDC2  
{  
public:  
   UDC2( long ); // User-defined conversion from long.  
};  
  
void Func( UDC1 );  
void Func( UDC2 );  
  
int main()  
{  
   Func( 1 );  
}  
```  
  
 `Func` 的兩種版本都需要使用者定義轉換，將 `int` 類型轉換成類別類型引數。  可能的轉換包括：  
  
-   從 `int` 類型轉換成 `UDC1` 類型 \(使用者定義轉換\)。  
  
-   從類型 `int` 轉換成 **long**，然後轉換成 `UDC2` 類型 \(包含兩個步驟的轉換\)。  
  
 即使這類轉換的第二個步驟需要標準轉換以及使用者定義轉換，這兩種轉換仍會視為相等。  
  
> [!NOTE]
>  使用者定義轉換會視為以建構方式轉換或以初始化方式轉換 \(轉換函式\)。  在考慮最符合項目時，這兩種方法會視為相等。  
  
## 引數比對和 this 指標  
 類別成員函式的處理方式不同，其取決於是否宣告為 `static`。  由於非靜態函式內含提供 `this` 指標的隱含引數，因此非靜態函式會被視為比靜態函式多一個引數，除此之外，它們的宣告是相同的。  
  
 這些非靜態成員函式要求隱含的 `this` 指標應與將呼叫之函式的物件類型相符，或者若是多載運算子，則它們要求第一個引數應與將套用之運算子的物件相符。  \(如需多載運算子的詳細資訊，請參閱[多載運算子](../cpp/operator-overloading.md)\)。  
  
 不同於多載函式中的其他引數，其中沒有引入暫存物件，且在嘗試比對 `this` 指標引數時沒有嘗試進行轉換。  
  
 使用 `– >` 成員選取運算子存取成員函式時，`this` 指標引數具有一個 `class-name` `* const` 的類型。  如果成員宣告為 `const` 或 `volatile`，則類型分別會是 `const` `class-name``* const` 和 `volatile` `class-name` `* const`。  
  
 `.` 成員選取運算子的工作方式完全相同，但有一點除外，就是其物件名稱前方會放置隱含的 `&` \(傳址\) 運算子。  下列範例顯示如何執行這項工作：  
  
```  
// Expression encountered in code  
obj.name  
  
// How the compiler treats it  
(&obj)->name  
```  
  
 `–>*` 和 `.*` \(成員的指標\) 運算子的左運算元處理方式，與具有相符引數的 `.` 和 `–>` \(成員選取\) 運算子相同。  
  
## 限制  
 有幾項限制負責管理一組可接受的多載函式：  
  
-   一組多載函式中的任兩個函式必須具有不同的引數清單。  
  
-   單獨依據傳回類型來判斷，具有相同類型引數清單的多載函式為錯誤。  
  
     **Microsoft 特定的**  
  
 您可以單獨根據傳回類型多載 **operator new**，具體而言，就是根據指定的記憶體模型修飾詞。  
  
## END Microsoft 特定的  
  
-   成員函式無法單獨根據某一個函式為靜態，另一個為非靜態而多載。  
  
-   `typedef` 宣告不會定義新類型，而是引入現有類型的同義資料表。  它們不會影響多載機制。  請考慮下列程式碼：  
  
    ```  
    typedef char * PSTR;  
  
    void Print( char *szToPrint );  
    void Print( PSTR szToPrint );  
    ```  
  
     上述兩個函式擁有相同的引數清單。  `PSTR` 與 **char \*** 同義。  在成員範圍內，這個程式碼會產生錯誤。  
  
-   列舉類型是不同的類型，可以用來區別多載函式。  
  
-   "array of " 和 "pointer to" 類型在區別多載函式時，會視為相同。  這種情況只對單一維度陣列成立。  因此，下列多載函式會發生衝突並產生錯誤訊息：  
  
    ```  
    void Print( char *szToPrint );  
    void Print( char szToPrint[] );  
    ```  
  
     對於多維度陣列而言，第二個和後續所有維度都會視為類型的一部分。  因此，它們會是用來區別多載函式：  
  
    ```  
    void Print( char szToPrint[] );  
    void Print( char szToPrint[][7] );  
    void Print( char szToPrint[][9][42] );  
    ```  
  
## 宣告比對  
 同一個範圍中任何兩個相同名稱的函式宣告可以參考同一個函式，也可以參考兩個多載的個別函式。  如果宣告的引數清單包含相同類型的引數 \(如先前章節所述\)，函式宣告會參考相同的函式。  否則，它們會參考使用多載選取的兩個不同函式。  
  
 類別範圍會受到嚴密的觀察；因此，在基底類別中宣告的函式和在衍生類別中宣告的函式不在同一個範圍內。  如果將衍生類別中的函式宣告為與基底類別中的函式相同名稱，該衍生類別函式會隱藏基底類別函式，而不會引發多載。  
  
 區塊範圍會受到嚴密的觀察；因此，在檔案範圍中宣告的函式和在本機宣告的函式不在同一個範圍內。  如果本機宣告的函式與在檔案範圍中宣告的函式相同名稱，本機宣告的函式會隱藏檔案範圍涵式，而不會引發多載。  例如:  
  
```  
// declaration_matching1.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
void func( int i )  
{  
    cout << "Called file-scoped func : " << i << endl;  
}  
  
void func( char *sz )  
{  
   cout << "Called locally declared func : " << sz << endl;  
}  
  
int main()  
{  
   // Declare func local to main.  
   extern void func( char *sz );  
  
   func( 3 );   // C2664 Error. func( int ) is hidden.  
   func( "s" );  
}  
```  
  
 上述程式碼會顯示函式 `func` 的兩個定義。  因為 `char *` 陳述式的緣故，採用類型為 `main` 之引數的定義對 `extern` 是本機定義。  因此會隱藏採用類型為 `int` 之引數的定義，而對 `func` 的第一個呼叫會出現錯誤。  
  
 對於多載成員函式，可以將不同的存取權限授與不同版本的函式。  這些函式仍在封入類別的範圍內，因此是多載函式。  請考慮下列程式碼，其中的成員函式 `Deposit` 是多載函式；其中一個是公用版本，另一個則是私用版本。  
  
 這個範例的目的在於提供 `Account` 類別，在此類別中需要有正確的密碼才能執行儲放。  此作業需使用多載來完成。  
  
 請注意，呼叫 `Deposit` 中的 `Account::Deposit` 會呼叫私用成員函式。  這個呼叫是正確的，因為 `Account::Deposit` 是成員函式，因此可以存取該類別的私用成員。  
  
```  
// declaration_matching2.cpp  
class Account  
{  
public:  
   Account()  
   {  
   }  
   double Deposit( double dAmount, char *szPassword );  
  
private:  
   double Deposit( double dAmount )  
   {  
      return 0.0;  
   }  
   int Validate( char *szPassword )  
   {  
      return 0;  
   }  
  
};  
  
int main()  
{  
    // Allocate a new object of type Account.  
    Account *pAcct = new Account;  
  
    // Deposit $57.22. Error: calls a private function.  
    // pAcct->Deposit( 57.22 );  
  
    // Deposit $57.22 and supply a password. OK: calls a  
    //  public function.  
    pAcct->Deposit( 52.77, "pswd" );  
}  
  
double Account::Deposit( double dAmount, char *szPassword )  
{  
   if ( Validate( szPassword ) )  
      return Deposit( dAmount );  
   else  
      return 0.0;  
}  
```  
  
## 請參閱  
 [函式 \(C\+\+\)](../cpp/functions-cpp.md)