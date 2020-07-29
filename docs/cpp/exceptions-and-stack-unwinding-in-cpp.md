---
title: C++ 中的例外狀況和堆疊回溯
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: e0dadc90f85caeea359fca4ed0b45868ea77177e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221558"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的例外狀況和堆疊回溯

在 C++ 例外狀況機制中，控制項是從 throw 陳述式移動到可以處理擲回類型的第一個 catch 陳述式。 當到達 catch 語句時，會在稱為*堆疊*回溯的進程中，終結 throw 和 catch 語句之間範圍內的所有自動變數。 堆疊回溯中的執行方式如下：

1. Control 會依照 **`try`** 正常的循序執行來到達語句。 會執行區塊中的保護區段 **`try`** 。

1. 如果在執行保護區段期間未擲回任何例外狀況，則 **`catch`** 不會執行緊接在區塊後面的子句 **`try`** 。 執行會繼續在 **`catch`** 相關聯區塊後面的最後一個子句之後的語句中 **`try`** 。

1. 如果在執行受保護區段期間，或在受保護區段直接或間接呼叫的任何常式中擲回例外狀況，則會從運算元所建立的物件建立例外狀況物件 **`throw`** 。 （這表示可能會牽涉到複製的構造函式）。此時，編譯器 **`catch`** 會在較高的執行內容中尋找子句，以處理所擲回之類型的例外狀況，或可 **`catch`** 處理任何例外狀況類型的處理常式。 **`catch`** 處理常式會依其在區塊後面的外觀順序進行檢查 **`try`** 。 如果找不到適當的處理常式，則會檢查下一個動態封閉 **`try`** 區塊。 此程式會繼續進行，直到檢查最外層的封閉 **`try`** 區塊為止。

1. 如果仍然找不到相符的處理常式，或是回溯過程中、處理常式取得控制之前發生例外狀況，則會呼叫預先定義的執行階段函式 `terminate`。 如果在擲回例外狀況後但回溯開始之前發生例外狀況，則會呼叫 `terminate`。

1. 如果找到相符的 **`catch`** 處理常式，而且它是以傳值方式捕捉，其型式參數就會藉由複製例外狀況物件來初始化。 如果它是以傳址方式攔截，則會初始化參數以參考例外狀況物件。 在型式參數初始化之後，回溯堆疊的處理序才會開始。 這牽涉到在 **`try`** 與處理常式相關聯的區塊開頭與例外狀況的擲回網站之間，終結所有已完全建立（但尚未解構）的自動物件 **`catch`** 。 解構會依照建構的反向順序進行。 **`catch`** 處理常式會執行，而且程式會在最後一個處理常式之後繼續執行，也就是在不是處理常式的第一個語句或結構中 **`catch`** 。 控制項只能透過擲回的例外狀況來輸入 **`catch`** 處理常式，而不是透過語句 **`goto`** 或 **`case`** 語句中的標籤 **`switch`** 。

## <a name="stack-unwinding-example"></a>堆疊回溯範例

下列範例將示範堆疊如何在擲回例外狀況時回溯。 在執行緒上的執行會從 `C` 中的 throw 陳述式跳至 `main` 中的 catch 陳述式，然後一路回溯每個函式。 請注意 `Dummy` 物件建立的順序，以及物件超出範圍後終結的順序。 另請注意，除了包含 catch 陳述式的 `main` 之外，其他函式都不會完成。 函式 `A` 絕不會從其對 `B()` 的呼叫傳回，而且 `B` 絕不會從其對 `C()` 的呼叫傳回。 如果您取消 `Dummy` 指標定義和對應 delete 陳述式的註解，然後執行程式，請注意指標絕不會刪除。 這就說明函式未提供例外狀況保證時，可能發生的狀況。 如需詳細資訊，請參閱＜如何：例外狀況的設計＞。 如果您註解 catch 陳述式，就可以觀察程式因為未處理的例外狀況結束時，會發生什麼情況。

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```
