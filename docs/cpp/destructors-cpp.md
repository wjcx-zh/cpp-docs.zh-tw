---
title: 解構函式 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae1ca6923bc7e67218e35c5a6c86b9f4ac112e59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="destructors-c"></a>解構函式 (C++)
解構函式是會自動叫用當物件超出範圍或明確地被終結由呼叫成員函式`delete`。 解構函式具有相同的名稱為類別，加上波狀符號 (`~`)。 例如，`String` 類別的解構函式宣告為：`~String()`。 如果未定義解構函式，編譯器會提供一個; 預設值許多類別就足夠了。 您只需要定義自訂的解構函式，此類別會儲存需要釋放系統資源的控制代碼時，或擁有記憶體的指標指向。

請考慮下面的 `String` 類別宣告：  
  
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
  
## <a name="declaring-destructors"></a>宣告解構函式  
 解構函式是名稱與類別相同的函式，但其名稱前面會加上波狀符號 (`~`)。  
  
 有數種規則用於管理解構函式的宣告。 解構函式：  
  
-   不接受引數。  
  
-   不會傳回值 (或`void`)。  
  
-   不能宣告為**const**， `volatile`，或**靜態**。 不過，它們可以叫用的物件的解構宣告為**const**， `volatile`，或**靜態**。  
  
-   可以宣告為**虛擬**。 使用虛擬解構函式可以終結物件而不需要知道它們的類型，其會使用虛擬函式機制為物件叫用正確的解構函式。 請注意，解構函式也可以宣告為抽象類別的純虛擬函式。  
  
## <a name="using-destructors"></a>使用解構函式  
 在下列任一事件發生時，會呼叫解構函式：  

-   區塊範圍內的區域 (自動) 物件會超出範圍。  

-   配置使用的物件**新**運算子會明確地取消配置使用**刪除**。   
  
-   暫存物件的存留期結束。  
  
-   程式結束，而全域或靜態物件存在。  
  
-   使用解構函式的函式完整名稱明確地呼叫解構函式。
  
 解構函式可以自由呼叫類別成員函式和存取類別成員資料。
  
 有兩個限制的解構函式使用：
 - 您無法取得其位址
-  在衍生的類別不會繼承其基底類別的解構函式。
  
## <a name="order-of-destruction"></a>解構順序  
 當物件超出範圍或被刪除時，事件完整解構的順序如下所示：  
  
1.  呼叫類別的解構函式，並且執行解構函式的主體。  
  
2.  按照非靜態成員物件出現在類別解構函式中的順序反向呼叫其解構函式。 這些成員之建構中使用的選擇性成員初始化清單不會影響建構或解構的順序。   
  
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
  
### <a name="virtual-base-classes"></a>虛擬基底類別  
 虛擬基底類別的解構函式會依它們出現在導向非循環圖中的反向順序呼叫 (深度優先、由左至右、後序走訪)。 下圖將說明繼承圖表。  
  
 ![顯示虛擬基底類別的繼承圖形](../cpp/media/vc392j1.gif "vc392J1")  
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
  
1.  周遊左側圖表，從圖中的最深點開始 (在這個案例中為 `E`)。  
  
2.  向左周遊，直到瀏覽過所有節點。 記下目前節點的名稱。  
  
3.  再次瀏覽上一個節點 (右下方)，確認記住的節點是否為虛擬基底類別。  
  
4.  如果記住的節點是虛擬基底類別，請掃描清單，查看該節點是否已輸入。 如果不是虛擬基底類別，則會忽略它。  
  
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
  
 這個程序會產生已排序的唯一項目清單。 類別名稱不會重複出現。 清單建構之後，會依反向順序查看該清單，而清單中每個類別的解構函式會依最後一個到第一個的順序呼叫。  
  
 如果某一個類別中的建構函式或解構函式要求其他元件必須先建立或保存更長時間 (例如，如果 `A` 的解構函式 (如上圖) 要求其程式碼執行時，`B` 必須持續存在 (反之亦然))，建構或解構的順序就會非常重要。  
  
 繼承圖表中類別之間的這種相依性原本就存在危險性，因為之後衍生的類別可以修改最左邊的路徑，藉此變更建構和解構的順序。  
  
### <a name="nonvirtual-base-classes"></a>非虛擬基底類別  
 非虛擬基底類別的解構函式會依照基底類別名稱宣告的相反順序呼叫。 請考慮下列類別宣告：  
  
```  
class MultInherit : public Base1, public Base2  
...  
```  
  
 在上述範例中，`Base2` 的解構函式是在 `Base1` 的解構函式之前呼叫。  
  
## <a name="explicit-destructor-calls"></a>明確解構函式呼叫  
 明確呼叫解構函式不是必要的步驟。 不過，這對放置於絕對位址的物件執行清除作業可能會很有用。 這些物件通常會使用使用者定義來配置**新**接受位置引數的運算子。 **刪除**運算子無法取消配置此記憶體，因為它不會配置從可用的存放區 (如需詳細資訊，請參閱[新和 delete 運算子](../cpp/new-and-delete-operators.md))。 不過，呼叫解構函式時，可以執行適當的清除作業。 若要明確呼叫物件的解構函式 (`s` 類別的 `String`)，請使用下列其中一種陳述式：  
  
```  
s.String::~String();     // Nonvirtual call  
ps->String::~String();   // Nonvirtual call  
  
s.~String();       // Virtual call  
ps->~String();     // Virtual call  
```  
  
 您可以使用明確呼叫解構函式的標註法 (如先前所示)，不論該類型是否定義了解構函式。 這可讓您進行這類明確呼叫，而不需要知道是否已為該類型定義解構函式。 明確呼叫未定義的解構函式不會有任何作用。  
