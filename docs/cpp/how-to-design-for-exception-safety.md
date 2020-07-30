---
title: 如何：針對例外狀況安全性設計
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
ms.openlocfilehash: 732a46166c99396c5d55a7d2acd834b58f3d2b2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187799"
---
# <a name="how-to-design-for-exception-safety"></a>如何：針對例外狀況安全性設計

其中一個例外狀況機制的優點是與例外狀況相關資料一起執行，直接從擲回例外狀況的陳述式跳躍到處理它的第一個 catch 陳述式。 處理常式可能是在呼叫堆疊的任意層級。 在 try 陳述式和 throw 陳述式之間呼叫的函式不必知道任何關於擲回例外狀況的事情。  然而，它們必須經過設計，才能在可能從底下傳播例外狀況的任何點意外地超出範圍，而這麼做並不會留下部分建立的物件、流失的記憶體或在無法使用狀態的資料結構。

## <a name="basic-techniques"></a>基本技巧

強大例外狀況處理原則需要仔細考量，且應該納入設計程序的一部分。 一般而言，大部分例外狀況會在軟體模組的較低層被偵測到並擲回，不過，這些圖層通常沒有足夠的內容去處理錯誤，或公開訊息給終端使用者。 在中介層，當必須檢查例外狀況物件時，函式可以攔截並重新擲回例外狀況，或有其他實用資訊提供給最後攔截例外狀況的最上層。 只要可以完全復原，函式就應該攔截並「忍受」例外狀況。 在大部分情況下，中介層的正確行為是讓例外狀況散佈到呼叫堆疊。 在最高層，如果例外狀況讓程式無法保證正確性，最好讓未處理的例外狀況終止程式。

不論函式如何處理例外狀況，為了確保「例外狀況時仍然安全」，它必須根據下列基本規則設計。

### <a name="keep-resource-classes-simple"></a>讓資源類別保持簡單

當您在類別中封裝手動資源管理時，請使用沒有任何功能的類別，除了管理單一資源以外。 藉由讓類別保持簡單，您可以降低引進資源流失的風險。 盡可能使用[智慧型指標](smart-pointers-modern-cpp.md)，如下列範例所示。 當使用 `shared_ptr` 時，這個範例會刻意人工化或簡單化以醒目提示差異之處。

```cpp
// old-style new/delete version
class NDResourceClass {
private:
    int*   m_p;
    float* m_q;
public:
    NDResourceClass() : m_p(0), m_q(0) {
        m_p = new int;
        m_q = new float;
    }

    ~NDResourceClass() {
        delete m_p;
        delete m_q;
    }
    // Potential leak! When a constructor emits an exception,
    // the destructor will not be invoked.
};

// shared_ptr version
#include <memory>

using namespace std;

class SPResourceClass {
private:
    shared_ptr<int> m_p;
    shared_ptr<float> m_q;
public:
    SPResourceClass() : m_p(new int), m_q(new float) { }
    // Implicitly defined dtor is OK for these members,
    // shared_ptr will clean up and avoid leaks regardless.
};

// A more powerful case for shared_ptr

class Shape {
    // ...
};

class Circle : public Shape {
    // ...
};

class Triangle : public Shape {
    // ...
};

class SPShapeResourceClass {
private:
    shared_ptr<Shape> m_p;
    shared_ptr<Shape> m_q;
public:
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }
};
```

### <a name="use-the-raii-idiom-to-manage-resources"></a>使用 RAII 用法來管理資源

若要讓例外狀況安全，函式必須確定已使用或所配置的物件已終結 `malloc` **`new`** ，而且所有資源（例如檔案控制代碼）都已關閉或釋放，即使擲回例外狀況也是一樣。 *資源取得是初始化*（RAII）將這類資源的管理系結至自動變數的存留期。 當藉由正常傳回或因發生例外狀況造成函式超出範圍時，會叫用所有完整建構之自動變數的解構函式。 RAII 包裝函式物件 (例如智慧型指標) 會呼叫其解構函式之適當刪除或終止函式。 在例外狀況安全程式碼中，必須立即將每個資源擁有權傳遞到某種 RAII 物件。 請注意 `vector` ，、 `string` 、 `make_shared` 、 `fstream` 和類似的類別會為您處理資源的取得。  不過， `unique_ptr` 和傳統 `shared_ptr` 的結構是特殊的，因為資源的取得是由使用者執行，而不是物件，因此，它們會計算為*資源釋放的損毀，* 但也是可懷疑為 RAII 的問題。

## <a name="the-three-exception-guarantees"></a>這三個例外狀況保證

一般而言，例外狀況安全性會根據函式可提供的三個例外狀況來加以討論：*不會失敗保證*、*強式保證*和*基本保證*。

### <a name="no-fail-guarantee"></a>否-無法保證

無失誤 (或「無擲回」) 保證是函式可提供之最強保證。 它表示函式不會擲回例外狀況，也不會允許散佈。 不過，您無法可靠地提供這類保證，除非 (a) 您知道所有函式，且函式呼叫也是無失誤，或 (b) 您知道在到達這個函式之前擲回的例外狀況都被攔截，或 (c) 您知道如何攔截並正確處理可能會到達這個函式的所有例外狀況。

強烈保證與基本保證都假設解構函式是無誤的。 標準程式庫中的所有容器和類型保證其解構函式不會擲回。 也有相反的需求：標準程式庫會要求所提供的使用者定義類型 (例如範本引數)，必須具有非擲回解構函式。

### <a name="strong-guarantee"></a>強式保證

強力保證表示，如果因為發生例外狀況而使函式超出範圍，則不會流失記憶體，且程式狀態不會被修改。 提供強力保證的函式基本上是有認可或復原語意的異動，不是完全成功，就是沒有作用。

### <a name="basic-guarantee"></a>基本保證

基本保證是三種保證中最弱的一個。 不過，當強力保證在記憶體耗用量或在效能方面過於昂貴時，基本保證可能是最好的選擇。 基本的保證表示，如果發生例外狀況，記憶體不會流失，而且物件仍處於可使用狀態，即使資料可能已經被修改。

## <a name="exception-safe-classes"></a>例外狀況安全類別

此類別可確保其本身的例外狀況安全性，即使它是由不安全的函式使用，因為它可免於被部分建構或終結。 如果類別建構函式在完成之前結束，則不會建立物件，且絕不會呼叫其解構函式。 雖然在例外狀況之前初始化的自動變數都會叫用其解構函式，但會流失不是由智慧型指標或類似的自動變數管理的動態配置記憶體或資源。

內建類型都是無誤的，因此標準程式庫類型會支援最少的基本保證。 遵循必須是例外狀況安全之使用者定義類型的方針：

- 使用智慧型指標或其他 RAII 類型的包裝函式來管理所有資源。 避免類別解構函式的資源管理功能，因為如果建構函式擲回例外狀況，將不會叫用解構函式。 不過，如果類別是只控制一個資源的專屬資源管理員，則使用解構函式管理資源是可接受的。

- 了解基底類別建構函式所擲回的例外狀況在衍生類別建構函式中是不可以被忍受的。 如果您要轉譯和重新擲回在衍生類別建構函式的基底類別例外狀況，請使用函式 try 區塊。

- 考慮是否在智慧型指標包裝的資料成員中儲存所有類別狀態，特別是如果類別有「允許初始化失敗」的概念。 雖然 C++ 允許未初始化的資料成員，但不支援未初始化或部分初始化的類別執行個體。 建構函式必須不是成功就是失敗，因為如果建構函式沒有執行到完成，則不會建立物件。

- 不允許任何例外狀況從解構函式逸出。 C++ 基本原則為解構函式不得允許例外狀況散佈到呼叫堆疊。 如果解構函式必須執行可能會擲回例外狀況的作業，它必須在 try catch 區塊做這動作，且忍受例外狀況。 標準程式庫會在其定義之所有解構函式提供這項保證。

## <a name="see-also"></a>另請參閱

[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](errors-and-exception-handling-modern-cpp.md)<br/>
[如何：在例外狀況和非例外狀況程式碼之間進行介面](how-to-interface-between-exceptional-and-non-exceptional-code.md)
