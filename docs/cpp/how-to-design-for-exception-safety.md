---
title: "如何：例外狀況安全的設計 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：例外狀況安全的設計
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其中一個例外狀況機制的優點是，執行與例外狀況的相關資料，直接從擲回例外狀況的陳述式跳躍到處理它的第一個 catch 陳述式。  處理常式可能是在呼叫堆疊的任意的層級。  在 try 陳述式和 throw 陳述式之間呼叫的函式不必知道任何關於擲回例外狀況的事情。然而，它們必須被設計，以便超出範圍之「意外」例外狀況隨時可能會從下面傳播，而這麼做，不用留下部分建立的物件、遺漏在無法使用的狀態的記憶體或資料結構。  
  
## 基本技術  
 一項強大例外狀況處理原則需要仔細考量，且應該是設計程序的一部分。  一般而言，大部分例外狀況會被偵測並擲回到軟體模組的較低層，不過，這些圖層通常沒有足夠的內容去處理錯誤或公開訊息給使用者。  在中介層，函式可以攔截並重新擲回例外狀況，當必須檢查例外狀況物件時，或有其他有用的資訊提供最上層在最後攔截例外狀況。  只要可以從它完全復原，函式應該攔截，且「忍受」例外狀況。  在大部分情況下，在中介層的正確行為是讓呼叫堆疊中的例外狀況傳播的。  在最高的圖層，如果保留在程式裡的例外狀況無法保證正確性，讓未處理的例外狀況結束程式可能是較適當的。  
  
 不論函式如何處理例外狀況，為了協助確保「例外狀況的安全」，必須根據下列基本規則設計它。  
  
### 保持資源類別簡單  
 當您封裝在類別中手動資源管理，請使用沒在處理每個資源的類別；否則，您可能會造成遺漏。  使用 [智慧型指標](../cpp/smart-pointers-modern-cpp.md) ，可能的話，如下列範例所示。  當使用 `shared_ptr` 時，這個範例會刻意人工的或簡單的反白來顯示差異。  
  
```cpp  
// old-style new/delete version  
class NDResourceClass {  
private:  
    int*   m_p;  
    float* m_q;  
public:  
    NDResourceClass() : m_p(0), m_q(0) {  
        m_p = new int;  
        m_q = new float;  
    }  
  
    ~NDResourceClass() {  
        delete m_p;  
        delete m_q;  
    }  
    // Potential leak! When a constructor emits an exception,   
    // the destructor will not be invoked.     
};  
  
// shared_ptr version  
#include <memory>  
  
using namespace std;  
  
class SPResourceClass {  
private:  
    shared_ptr<int> m_p;  
    shared_ptr<float> m_q;  
public:  
    SPResourceClass() : m_p(new int), m_q(new float) { }  
    // Implicitly defined dtor is OK for these members,   
    // shared_ptr will clean up and avoid leaks regardless.  
};  
  
// A more powerful case for shared_ptr  
  
class Shape {  
    // ...  
};  
  
class Circle : public Shape {  
    // ...  
};  
  
class Triangle : public Shape {  
    // ...  
};  
  
class SPShapeResourceClass {  
private:  
    shared_ptr<Shape> m_p;  
    shared_ptr<Shape> m_q;  
public:  
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }  
};  
  
```  
  
### 使用 RAII 慣用語處置資源。  
 若要例外狀況安全，函式必須確定物件是使用 `malloc` 來配置或終結 `new` 和所有資源，像是檔案控制之關閉或釋放，即使擲回例外狀況。  *Resource Acquisition Is Initialization* \(RAII\) 慣用語有這類資源至壽命自動變數的管理。  透過一般傳回或發生例外狀況所造成之函式超出範圍時，所有完整建構之自動變數的解構函式會被叫用。  RAII 包裝函式物件 \(例如智慧型指標\) 呼叫其解構函式之適當的刪除或終止函式。  用無例外狀況之虞的程式碼，直接將每個資源擁有權轉到同樣的 RAII 物件是最重要的。  請注意 `vector`、 `string`、 `make_shared`、 `fstream`和類似的類別處理資源之獲取。不過，因為資源擷取由使用者執行而不是物件， `unique_ptr` 與傳統的 `shared_ptr` 建構是較特別的；因此，它們因為 *資源版本是解構函式*來計數，但做為 RAII 是有疑問的。  
  
## 三個例外狀況之保證  
 通常，例外狀況安全是根據函式可能提供之三個例外狀況保證來討論: *無期限保證*、 *強的保證*和 *基本的保證*。  
  
### 無期限保證  
 無期限 \(或，而「非擲回」\) 保證是函式可能提供之最強的保證。  它說明了函式不會擲回例外狀況也不會允許傳播。  不過，您無法可靠地提供這類保證，除非 \(a\) 您知道所有函式，且函式呼叫也是無期限或、 \(b\) 您知道在到達這個函式之前擲回的所有例外狀況、 \(c\) 您會攔截並正確處理可能會到達這個函式的所有例外狀況。  
  
 強的保證與基礎確保證都是依賴在解構函式是無失效的假設。  所有解構函式不會擲回的標準程式庫保證的容器和型別。  也有相反的需求：標準程式庫會要求使用者定義型別，例如樣板引數，必須有非擲回的解構函式。  
  
### 強的保證  
 強的保證說明，如果因為發生例外狀況而函式超過範圍，則不會遺漏記憶體，且程式狀態不會修改。  提供強的保證的函式基本上是有認可或復原語意的交易：不是完全成功就是沒有作用。  
  
### 基礎保證  
 基本保證是三種保證裡面最弱的。  不過，當強的保證在記憶體用量或在效能上太昂貴時，它可能是最佳選擇。  基本的保證，說明如果發生例外狀況，記憶體不會遺漏，而且物件仍處於可用的狀態，即使可能已經修改了資料。  
  
## 例外狀況安全類別  
 此類別可協助確保它的例外狀況安全，即使它是不安全的函式使用，因為它防止部分建構或部分被終結。  如果類別建構函式在完成之前結束，則物件會建立，而且其解構函式不會呼叫。  雖然在例外狀況之前初始化的自動變數都會叫用解構函式，但不為智慧型指標或類似的自動變數處理的動態方式配置記憶體或資源將會遺漏。  
  
 內建型別都會失效，因此標準程式庫型別在最小的狀況下支援這個基礎保證。  遵循一定是例外狀況安全的使用者定義型別的方針：  
  
-   使用智慧型指標或其他 RAII 型別的包裝函式來管理所有資源。  避免在類別解構函式的資源管理功能，因為如果建構函式擲回例外狀況的話，解構函式不會叫用。  不過，如果類別是控制資源的專屬資源管理員，則使用解構函式管理資源是可接受的。  
  
-   要了解基底類別建構函式所擲回的例外狀況在衍生類別建構函式中不可以被忍受。  如果您要轉譯和重新擲回在衍生的類別建構函式的基底類別例外狀況，請使用函式 try 區塊。  如需詳細資訊，請參閱[\(NOTINBUILD\)How to: Handle Exceptions in Base Class Constructors \(C\+\+\)](http://msdn.microsoft.com/zh-tw/53bb822e-785b-4581-9517-210dd05060a3)。  
  
-   考慮是否儲存所有類別狀態在智慧型指標包裝的資料成員，特別是如果類別有「允許初始化失敗」的概念。雖然 C\+\+ 允許未初始化的資料成員，但不支援未初始化或部分初始化的類別執行個體。  建構函式必須不是成功就是失敗；如果建構函式沒有執行到完成，物件則不會建立。  
  
-   不允許任何例外狀況從解構函式逸出。  C\+\+ 基礎公理說明解構函式不應該允許例外狀況散佈到呼叫堆疊。  如果解構函式必須執行可能會擲回例外狀況的作業，它必須在 try catch 區塊動作且忍受例外狀況。  標準程式庫提供所有解構函式所定義的這個保證。  
  
## 請參閱  
 [錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [如何：例外狀況和非例外狀況代碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)