---
title: "解構函式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~ 運算子, 指定解構函式"
  - "終結物件, 解構函式"
  - "解構函式, 關於解構函式"
  - "解構函式, C++"
  - "物件 [C++], 終結"
  - "Visual C++, 解構函式"
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 解構函式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「解構函式」是建構函式的相反。  當物件終結時 \(取消配置\)，它們會被呼叫。  藉由在類別名稱前面加上波狀符號 \(`~`\)，將函式指定為類別的解構函式。  例如，`String` 類別的解構函式宣告為：`~String()`。  
  
 在 \/clr 編譯，解構函式在釋放 Managed 和 Unmanaged 資源上有特殊角色。  如需詳細資訊，請參閱[Visual C\+\+ 中的解構函式和完成項](../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
 當物件不再需要時，解構函式通常用於「清除」此物件。  請考慮下面的 `String` 類別宣告：  
  
```  
// spec1_destructors.cpp  
#include <string.h>  
  
class String {  
public:  
   String( char *ch );  // Declare constructor  
   ~String();           //  and destructor.  
private:  
   char    *_text;  
   size_t  sizeOfText;  
};  
  
// Define the constructor.  
String::String( char *ch ) {  
   sizeOfText = strlen( ch ) + 1;  
  
   // Dynamically allocate the correct amount of memory.  
   _text = new char[ sizeOfText ];  
  
   // If the allocation succeeds, copy the initialization string.  
   if( _text )  
      strcpy_s( _text, sizeOfText, ch );  
}  
  
// Define the destructor.  
String::~String() {  
   // Deallocate the memory that was previously reserved  
   //  for this string.  
   if (_text)  
      delete[] _text;  
}  
  
int main() {  
   String str("The piper in the glen...");  
}  
```  
  
 在上述範例中，解構函式 `String::~String` 使用 `delete` 運算子，取消配置動態配置給文字儲存的空間。  
  
## 宣告解構函式  
 解構函式是名稱與類別相同的函式，但其名稱前面會加上波狀符號 \(`~`\)。  
  
 第一種形式的語法是用於類別宣告中已宣告或已定義的解構函式；第二種形式則用於在類別宣告以外定義的解構函式。  
  
 有數種規則用於管理解構函式的宣告。  解構函式：  
  
-   不接受引數。  
  
-   不能指定任何傳回類型 \(包括 `void`\)。  
  
-   不能使用 `return` 陳述式傳回值。  
  
-   不可以宣告為 **const**、`volatile` 或 **static**。  不過，可以為解構宣告為 **const**、`volatile` 或 **static** 的物件而叫用解構函式。  
  
-   可以宣告為 **virtual**。  使用虛擬解構函式可以終結物件而不需要知道它們的類型，其會使用虛擬函式機制為物件叫用正確的解構函式。  請注意，解構函式也可以宣告為抽象類別的純虛擬函式。  
  
## 使用解構函式  
 在下列任一事件發生時，會呼叫解構函式：  
  
-   使用 **new** 運算子配置的物件可以使用 **delete** 運算子明確地取消配置。  使用 **delete** 運算子取消配置物件時，會釋放「最具衍生性的物件」，或者是完整的物件，而不是表示基底類別的子物件。  這個「最具衍生性的物件」取消配置可確保只會與虛擬解構函式一起使用。  取消配置在多重繼承的情況下可能會失敗，其中類型資訊無法對應至實際物件的基礎類型。  
  
-   區塊範圍內的區域 \(自動\) 物件會超出範圍。  
  
-   暫存物件的存留期結束。  
  
-   程式結束，而全域或靜態物件存在。  
  
-   使用解構函式的函式完整名稱明確地呼叫解構函式。  \(如需詳細資訊，請參閱[明確呼叫解構函式](../misc/explicit-destructor-calls.md)\)。  
  
 上述清單中所描述的情況，可確定所有物件皆可透過使用者定義的方法終結。  
  
 如果基底類別或資料成員具有可存取的解構函式，且衍生類別未宣告解構函式，則編譯器會為其產生。  這個編譯器產生的解構函式會呼叫基底類別解構函式，以及衍生類型之成員的解構函式。  預設的解構函式是公用的。  \(如需存取範圍的詳細資訊，請參閱[基底類別的存取指定名稱](../misc/access-specifiers-for-base-classes.md)\)。  
  
 解構函式可以自由呼叫類別成員函式和存取類別成員資料。  從解構函式呼叫虛擬函式時，所呼叫的函式是目前終結之類別的函式。  \(如需詳細資訊，請參閱[解構順序](../misc/order-of-destruction.md)\)。  
  
 使用解構函式有兩個限制。  第一個限制是您無法取得解構函式的位址。  第二個限制是衍生類別不會繼承其基底類別的解構函式。  相反地，如先前所述，它們會覆寫基底類別的解構函式。  
  
## 解構順序  
 當物件超出範圍或被刪除時，事件完整解構的順序如下所示：  
  
1.  呼叫類別的解構函式，並且執行解構函式的主體。  
  
2.  按照非靜態成員物件出現在類別解構函式中的順序反向呼叫其解構函式。  這些成員之建構中使用的選擇性成員初始化清單不影響 \(建構或\) 解構順序   \(如需初始化成員的詳細資訊，請參閱[初始化基底和成員](http://msdn.microsoft.com/zh-tw/2f71377e-2b6b-49da-9a26-18e9b40226a1)\)。  
  
3.  按照宣告的相反順序呼叫非虛擬基底類別的解構函式。  
  
4.  按照宣告的相反順序呼叫虛擬基底類別的解構函式。  
  
```  
// order_of_destruction.cpp  
#include <stdio.h>  
  
struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };  
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };  
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };  
  
struct B1      { ~B1() { printf("B1 dtor\n"); } };  
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };  
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };  
  
int main() {  
   A1 * a = new A3;  
   delete a;  
   printf("\n");  
  
   B1 * b = new B3;  
   delete b;  
   printf("\n");  
  
   B3 * b2 = new B3;  
   delete b2;  
}  
  
Output: A3 dtor  
A2 dtor  
A1 dtor  
  
B1 dtor  
  
B3 dtor  
B2 dtor  
B1 dtor  
  
```  
  
### 虛擬基底類別  
 虛擬基底類別的解構函式會依它們出現在導向非循環圖中的反向順序呼叫 \(深度優先、由左至右、後序走訪\)。  下圖將說明繼承圖表。  
  
 ![顯示虛擬基底類別的繼承圖形](../cpp/media/vc392j1.png "vc392J1")  
顯示虛擬基底類別的繼承圖表  
  
 以下列出圖中所顯示類別的類別開頭。  
  
```  
class A  
class B  
class C : virtual public A, virtual public B  
class D : virtual public A, virtual public B  
class E : public C, public D, virtual public B  
```  
  
 為了判斷 `E` 類型物件之虛擬基底類別的解構順序，編譯器會套用下列演算法來建置清單：  
  
1.  周遊左側圖表，從圖中的最深點開始 \(在這個案例中為 `E`\)。  
  
2.  向左周遊，直到瀏覽過所有節點。  記下目前節點的名稱。  
  
3.  再次瀏覽上一個節點 \(右下方\)，確認記住的節點是否為虛擬基底類別。  
  
4.  如果記住的節點是虛擬基底類別，請掃描清單，查看該節點是否已輸入。  如果不是虛擬基底類別，則會忽略它。  
  
5.  如果記住的節點不在清單中，請將它加入清單的底部。  
  
6.  向上並沿著下一個向右的路徑周遊圖表。  
  
7.  移至步驟 2。  
  
8.  到達最後一個向上路徑時，請記下目前節點的名稱。  
  
9. 移至步驟 3。  
  
10. 繼續這個程序，直到底部節點再次成為目前節點為止。  
  
 因此，`E` 類別的解構順序如下：  
  
1.  非虛擬基底類別 `E`。  
  
2.  非虛擬基底類別 `D`。  
  
3.  非虛擬基底類別 `C`。  
  
4.  虛擬基底類別 `B`。  
  
5.  虛擬基底類別 `A`。  
  
 這個程序會產生已排序的唯一項目清單。  類別名稱不會重複出現。  清單建構之後，會依反向順序查看該清單，而清單中每個類別的解構函式會依最後一個到第一個的順序呼叫。  
  
 如果某一個類別中的建構函式或解構函式要求其他元件必須先建立或保存更長時間 \(例如，如果 `A` 的解構函式 \(如上圖\) 要求其程式碼執行時，`B` 必須持續存在 \(反之亦然\)\)，建構或解構的順序就會非常重要。  
  
 繼承圖表中類別之間的這種相依性原本就存在危險性，因為之後衍生的類別可以修改最左邊的路徑，藉此變更建構和解構的順序。  
  
### 非虛擬基底類別  
 非虛擬基底類別的解構函式會依照基底類別名稱宣告的相反順序呼叫。  請考慮下列類別宣告：  
  
```  
class MultInherit : public Base1, public Base2  
...  
```  
  
 在上述範例中，`Base2` 的解構函式是在 `Base1` 的解構函式之前呼叫。  
  
## 明確解構函式呼叫  
 明確呼叫解構函式不是必要的步驟。  不過，這對放置於絕對位址的物件執行清除作業可能會很有用。  這些物件通常會使用接受位置引數的使用者定義 **new** 運算子進行配置。  **delete** 運算子無法取消配置此記憶體，因為它不是從可用存放區進行配置 \(如需詳細資訊，請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)\)。  不過，呼叫解構函式時，可以執行適當的清除作業。  若要明確呼叫物件的解構函式 \(`s` 類別的 `String`\)，請使用下列其中一種陳述式：  
  
```  
s.String::~String();     // Nonvirtual call  
ps->String::~String();   // Nonvirtual call  
  
s.~String();       // Virtual call  
ps->~String();     // Virtual call  
```  
  
 您可以使用明確呼叫解構函式的標註法 \(如先前所示\)，不論該類型是否定義了解構函式。  這可讓您進行這類明確呼叫，而不需要知道是否已為該類型定義解構函式。  明確呼叫未定義的解構函式不會有任何作用。  
  
## 請參閱  
 [特殊成員函式](../misc/special-member-functions-cpp.md)