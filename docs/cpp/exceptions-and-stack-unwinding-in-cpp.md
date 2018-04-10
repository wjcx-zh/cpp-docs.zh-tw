---
title: 例外狀況和堆疊回溯，因為在 c + + |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2b354ebaa72c5257e2752a948ece6320a5d8e70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的例外狀況和堆疊回溯
在 C++ 例外狀況機制中，控制項是從 throw 陳述式移動到可以處理擲回類型的第一個 catch 陳述式。 當到達 catch 陳述式時，所有的自動變數中的 throw 之間的範圍內和 catch 陳述式中處理程序，也就是終結*堆疊回溯*。 堆疊回溯中的執行方式如下：  
  
1.  控制項會經由正常循序執行到達 `try` 陳述式。 `try` 區塊中保護的區段將會執行。  
  
2.  如果執行受保護區段期間未擲回例外狀況，`catch` 區塊後面接著的 `try` 子句就不會執行。 此時會在相關聯 `catch` 區塊後面的最後一個 `try` 子句之後，從陳述式繼續執行。  
  
3.  如果在執行受保護區段期間，或是在直接或間接進行受保護區段呼叫的任何常式中擲回例外狀況，則會從 `throw` 運算元所建立的物件建立例外狀況物件  (這表示可能包含複製建構函式)。此時，編譯器會在可以處理所擲回例外狀況類型的更高執行內容中尋找 `catch` 子句，或是尋找可以處理任何例外狀況類型的 `catch` 處理常式。 `catch` 處理常式會在 `try` 區塊之後，依照其出現的順序進行檢查。 如果找不到適當的處理常式，則會檢查下一個動態封閉的 `try` 區塊。 這個處理序會繼續執行，直到檢查最外層的封閉 `try` 區塊為止。  
  
4.  如果仍然找不到相符的處理常式，或是回溯過程中、處理常式取得控制之前發生例外狀況，則會呼叫預先定義的執行階段函式 `terminate`。 如果在擲回例外狀況後但回溯開始之前發生例外狀況，則會呼叫 `terminate`。  
  
5.  如果找到相符的 `catch` 處理常式，而且它是以傳值方式攔截，則其型式參數會藉由複製例外狀況物件初始化。 如果它是以傳址方式攔截，則會初始化參數以參考例外狀況物件。 在型式參數初始化之後，回溯堆疊的處理序才會開始。 這包括在與 `try` 處理常式相關聯的 `catch` 區塊開頭和例外狀況的擲回端之間，解構所有完全建構但尚未終結的自動物件。 解構會依照建構的反向順序進行。 `catch` 處理常式將會執行，而且程式會在最後一個處理常式 (也就是在不是 `catch` 處理常式的第一個陳述式或建構) 之後繼續執行。 控制項只能透過擲回的例外狀況進入 `catch` 處理常式，絕不會透過 `goto` 陳述式或 `case` 陳述式中的 `switch` 標籤。  
  
## <a name="stack-unwinding-example"></a>堆疊回溯範例  
 下列範例將示範堆疊如何在擲回例外狀況時回溯。 在執行緒上的執行會從 `C` 中的 throw 陳述式跳至 `main` 中的 catch 陳述式，然後一路回溯每個函式。 請注意 `Dummy` 物件建立的順序，以及物件超出範圍後終結的順序。 另請注意，除了包含 catch 陳述式的 `main` 之外，其他函式都不會完成。 函式 `A` 絕不會從其對 `B()` 的呼叫傳回，而且 `B` 絕不會從其對 `C()` 的呼叫傳回。 如果您取消 `Dummy` 指標定義和對應 delete 陳述式的註解，然後執行程式，請注意指標絕不會刪除。 這就說明函式未提供例外狀況保證時，可能發生的狀況。 如需詳細資訊，請參閱＜如何：例外狀況的設計＞。 如果您註解 catch 陳述式，就可以觀察程式因為未處理的例外狀況結束時，會發生什麼情況。  
  
```  
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