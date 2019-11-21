---
title: C++ 中的例外狀況和堆疊回溯
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246560"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的例外狀況和堆疊回溯

在 C++ 例外狀況機制中，控制項是從 throw 陳述式移動到可以處理擲回類型的第一個 catch 陳述式。 When the catch statement is reached, all of the automatic variables that are in scope between the throw and catch statements are destroyed in a process that is known as *stack unwinding*. 堆疊回溯中的執行方式如下：

1. Control reaches the **try** statement by normal sequential execution. The guarded section in the **try** block is executed.

1. If no exception is thrown during execution of the guarded section, the **catch** clauses that follow the **try** block are not executed. Execution continues at the statement after the last **catch** clause that follows the associated **try** block.

1. If an exception is thrown during execution of the guarded section or in any routine that the guarded section calls either directly or indirectly, an exception object is created from the object that is created by the **throw** operand. (This implies that a copy constructor may be involved.) At this point, the compiler looks for a **catch** clause in a higher execution context that can handle an exception of the type that is thrown, or for a **catch** handler that can handle any type of exception. The **catch** handlers are examined in order of their appearance after the **try** block. If no appropriate handler is found, the next dynamically enclosing **try** block is examined. This process continues until the outermost enclosing **try** block is examined.

1. 如果仍然找不到相符的處理常式，或是回溯過程中、處理常式取得控制之前發生例外狀況，則會呼叫預先定義的執行階段函式 `terminate`。 如果在擲回例外狀況後但回溯開始之前發生例外狀況，則會呼叫 `terminate`。

1. If a matching **catch** handler is found, and it catches by value, its formal parameter is initialized by copying the exception object. 如果它是以傳址方式攔截，則會初始化參數以參考例外狀況物件。 在型式參數初始化之後，回溯堆疊的處理序才會開始。 This involves the destruction of all automatic objects that were fully constructed—but not yet destructed—between the beginning of the **try** block that is associated with the **catch** handler and the throw site of the exception. 解構會依照建構的反向順序進行。 The **catch** handler is executed and the program resumes execution after the last handler—that is, at the first statement or construct that is not a **catch** handler. Control can only enter a **catch** handler through a thrown exception, never through a **goto** statement or a **case** label in a **switch** statement.

## <a name="stack-unwinding-example"></a>Stack unwinding example

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
