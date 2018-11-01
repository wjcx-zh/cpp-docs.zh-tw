---
title: C++ 中的例外狀況和堆疊回溯
ms.date: 11/04/2016
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 43d7945d53a0bd9993e75c04cceb3c8f5fec8ae2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569711"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的例外狀況和堆疊回溯

在 C++ 例外狀況機制中，控制項是從 throw 陳述式移動到可以處理擲回類型的第一個 catch 陳述式。 當到達 catch 陳述式時，所有自動變數的範圍之間會擲回和 catch 陳述式會終結就所謂的程序*堆疊回溯*。 堆疊回溯中的執行方式如下：

1. 控制項到達**嘗試**經由正常循序執行的陳述式。 在保護的區段**嘗試**區塊執行。

1. 如果保護的區段中，在執行期間擲不回任何例外狀況**攔截**遵循的子句**嘗試**區塊不會執行。 最後一個之後的陳述式繼續執行**攔截**遵循相關聯的子句**嘗試**區塊。

1. 如果受保護區段，或直接或間接保護的區段所呼叫的任何常式中的執行期間擲回例外狀況，例外狀況物件會建立從所建立的物件**擲回**運算元。 (這表示可能包含複製建構函式)。到目前為止，則編譯器會尋找**攔截**可以處理的例外狀況的擲回，類型或更高執行內容中的子句**攔截**可處理任何類型的例外狀況處理常式。 **攔截**處理常式會檢查其之後出現的順序**嘗試**區塊。 如果沒有適當的處理常式找到，下一個動態封閉**嘗試**區塊檢查。 此程序會繼續直到最外層的封閉**嘗試**區塊檢查。

1. 如果仍然找不到相符的處理常式，或是回溯過程中、處理常式取得控制之前發生例外狀況，則會呼叫預先定義的執行階段函式 `terminate`。 如果在擲回例外狀況後但回溯開始之前發生例外狀況，則會呼叫 `terminate`。

1. 如果相符**攔截**找到處理常式，以及它傳值方式攔截，其型式參數會藉由複製例外狀況物件初始化。 如果它是以傳址方式攔截，則會初始化參數以參考例外狀況物件。 在型式參數初始化之後，回溯堆疊的處理序才會開始。 這項作業包括解構所有完全建構的自動物件的 — 但尚未解構 — 之間的開頭**嘗試**相關聯的區塊**攔截**處理常式，擲回例外狀況的站的台。 解構會依照建構的反向順序進行。 **攔截**處理常式會執行，而且程式之後繼續執行的最後一個處理常式，也就是在第一個陳述式或建構不**攔截**處理常式。 控制項可以只輸入**攔截**處理常式擲回的例外狀況，絕不會透過**goto**陳述式或**案例**標示**切換**陳述式。

## <a name="stack-unwinding-example"></a>堆疊回溯範例

下列範例將示範堆疊如何在擲回例外狀況時回溯。 在執行緒上的執行會從 `C` 中的 throw 陳述式跳至 `main` 中的 catch 陳述式，然後一路回溯每個函式。 請注意 `Dummy` 物件建立的順序，以及物件超出範圍後終結的順序。 另請注意，除了包含 catch 陳述式的 `main` 之外，其他函式都不會完成。 函式 `A` 絕不會從其對 `B()` 的呼叫傳回，而且 `B` 絕不會從其對 `C()` 的呼叫傳回。 如果您取消 `Dummy` 指標定義和對應 delete 陳述式的註解，然後執行程式，請注意指標絕不會刪除。 這就說明函式未提供例外狀況保證時，可能發生的狀況。 如需詳細資訊，請參閱＜如何：例外狀況的設計＞。 如果您註解 catch 陳述式，就可以觀察程式因為未處理的例外狀況結束時，會發生什麼情況。

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName; 
    int level;
};

void C(Dummy d, int i)
{ 
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();   

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);   
    cout << "Exiting FunctionB" << endl; 
}

void A(Dummy d, int i)
{ 
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd; 
    cout << "Exiting FunctionA" << endl;   
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```