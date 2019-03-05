---
title: HOW TO：使用內容類別實作合作式信號
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 92f77fade972bff1528bc9a22416670354c70f34
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300761"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>HOW TO：使用內容類別實作合作式信號

本主題說明如何使用 concurrency:: context 類別實作合作式信號類別。

`Context`類別可讓您封鎖或產生目前的執行內容。 因為資源無法使用，無法繼續目前的內容時，封鎖或產生目前的內容很有用。 A*號誌*是一種情況下，其中目前的執行內容必須等待資源變成可用資源的範例。 號誌，像重要區段物件，就可讓一個具有資源的獨佔存取的內容中的程式碼的同步處理物件。 不過，不同於重要區段物件，號誌可讓多個並行存取資源的內容。 如果內容的最大數目為號誌鎖定，每個額外的內容必須等待釋放鎖定的另一個內容中。

### <a name="to-implement-the-semaphore-class"></a>若要實作 semaphore 類別

1. 宣告的類別，名為`semaphore`。 新增`public`和`private`區段，以這個類別。

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. 在`private`一節`semaphore`類別中，宣告[std:: atomic](../../standard-library/atomic-structure.md)保存號誌計數的變數， [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)保存之內容的物件必須等到取得號誌。

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. 在 `public`一節`semaphore`類別，請實作建構函式。 建構函式會採用`long long`值，指定可以同時保留鎖定的內容的最大數目。

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. 在 `public`一節`semaphore`類別，請實作`acquire`方法。 這個方法會遞減號誌計數做為不可部分完成的作業。 號誌計數變成負數，如果目前的內容加入等候佇列並呼叫端[concurrency::Context::Block](reference/context-class.md#block)方法來封鎖目前的內容。

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. 在 `public`一節`semaphore`類別，請實作`release`方法。 這個方法會遞增號誌計數，成為不可部分完成的作業。 號誌計數是負的遞增作業之前，如果沒有至少一個正在等候鎖定的內容。 在此情況下，解除封鎖在等候佇列前端的內容。

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>範例

`semaphore`因為在此範例中的類別行為以合作方式遞交`Context::Block`和`Context::Yield`方法產生的執行，以便讓執行階段執行其他工作。

`acquire`方法會遞減計數器，但它可能會無法完成將內容新增至另一個內容呼叫之前的等候佇列`release`方法。 為了說明這一點，`release`方法會使用呼叫微調迴圈[concurrency](reference/context-class.md#yield)方法以等候`acquire`方法，以完成新增內容。

`release`方法可以呼叫`Context::Unblock`方法，然後再`acquire`方法呼叫`Context::Block`方法。 您不必防範這種競爭狀況，因為執行階段可讓您以任何順序來呼叫這些方法。 如果`release`方法呼叫`Context::Unblock`之前`acquire`方法呼叫`Context::Block`提供相同的內容，該內容會維持已解除封鎖。 執行階段，只需要每個呼叫來`Context::Block`相符的對應呼叫`Context::Unblock`。

下列範例示範完整`semaphore`類別。 `wmain`函式會顯示這個類別的基本使用方式。 `wmain`函式會使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法建立需要存取號誌的幾項工作。 因為有三個執行緒可以在任何時間保留鎖定，一些工作必須等候另一項工作完成，然後釋放鎖定。

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

此範例會產生下列輸出範例。

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

如需詳細資訊`concurrent_queue`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。 如需詳細資訊`parallel_for`演算法，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`cooperative-semaphore.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 合作式 semaphore.cpp**

## <a name="robust-programming"></a>穩固程式設計

您可以使用*資源擷取即初始化*(RAII) 模式，可限制存取`semaphore`給定範圍的物件。 RAII 模式下的資料結構是在堆疊上配置。 該資料結構初始化，或建立和終結或終結的資料結構時釋放該資源時，取得資源。 RAII 模式可保證，封閉範圍結束之前，會呼叫解構函式。 因此，資源受到妥善管理擲回例外狀況時，或函式包含多個`return`陳述式。

下列範例會定義名為類別`scoped_lock`，其定義於`public`一節`semaphore`類別。 `scoped_lock`類別類似於[scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)並[scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別。 建構函式`semaphore::scoped_lock`類別會取得存取權指定`semaphore`物件和解構函式會釋放該物件的存取權。

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
下列範例會修改傳遞給工作函式的主體`parallel_for`演算法，因此它會使用 RAII 確保函式傳回之前釋放號誌。 這項技術可確保工作函式例外狀況安全。

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>另請參閱

[內容](../../parallel/concrt/contexts.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)
