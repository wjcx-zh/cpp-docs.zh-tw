---
title: "如何： 使用內容類別實作合作式信號 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03884d69877053976fdaf04e507c4c1c4214026e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>如何：使用內容類別實作合作式信號
本主題示範如何使用 concurrency:: context 類別實作合作式信號類別。  
  
 `Context`類別可讓您封鎖或產生目前的執行內容。 封鎖或產生目前的內容時，無法繼續目前的內容，因為資源無法使用。 A*號誌*是一種情況，其中目前執行內容必須等候資源變成可用資源的範例。 號誌，如同關鍵區段物件，是讓程式碼在具有獨佔存取權的資源的內容中的同步處理物件。 不過，不同的關鍵區段物件，於信號可讓多個同時存取資源的內容。 如果內容的最大數目會保留信號鎖定，每個額外的內容必須等候釋放鎖定的其他內容。  
  
### <a name="to-implement-the-semaphore-class"></a>若要實作 semaphore 類別  
  
1.  宣告的類別，名為`semaphore`。 新增`public`和`private`區段，這個類別。  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  在`private`區段`semaphore`類別中，宣告[std::atomic](../../standard-library/atomic-structure.md)保留號誌計數的變數和[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)保存內容物件必須等候的取得號誌。  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  在`public`區段`semaphore`類別，實作建構函式。 建構函式接受`long long`值，指定可以同時保持鎖定的內容的最大數目。  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  

4.  在`public`區段`semaphore`類別，實作`acquire`方法。 這個方法就會減 1 號誌計數成為不可部分完成的作業。 如果號誌計數變成負數時，將目前的內容加入至結束等候佇列及呼叫[concurrency::Context::Block](reference/context-class.md#block)方法來封鎖目前的內容。  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  在`public`區段`semaphore`類別，實作`release`方法。 這個方法會遞增號誌計數，成為不可部分完成的作業。 號誌計數為負數遞增作業之前，如果沒有至少一個正在等候鎖定的內容。 在此情況下，解除封鎖在等候佇列前面的內容。  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>範例  
 `semaphore`因為在此範例中的類別行為以合作方式`Context::Block`和`Context::Yield`方法會先執行，以便在執行階段可以執行其他工作。  
  
 `acquire`方法遞減的計數器，但它可能會無法完成將內容加入至另一個內容呼叫前的等候佇列`release`方法。 若要這麼做，帳戶`release`方法會使用呼叫微調迴圈[yield](reference/context-class.md#yield)方法等候`acquire`方法，以完成新增內容。  
  
 `release`方法可以呼叫`Context::Unblock`方法，然後再`acquire`方法呼叫`Context::Block`方法。 您不需要防範這種競爭情形，因為執行階段允許以任何順序來呼叫這些方法。 如果`release`方法呼叫`Context::Unblock`之前`acquire`方法呼叫`Context::Block`針對相同的內容，該內容會維持已解除封鎖。 執行階段只會要求每個呼叫到`Context::Block`會與對應的呼叫來比對`Context::Unblock`。  
  
 下列範例顯示完整`semaphore`類別。 `wmain`函式將示範這個類別的基本使用方式。 `wmain`函式使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法建立需要存取號誌的幾項工作。 三個執行緒可以在任何時間保持鎖定，因為某些工作必須等候另一個工作完成並釋出鎖定。  
  
 [!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]  
  
 這個範例會產生下列輸出範例。  
  
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
  
 如需有關`concurrent_queue`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。 如需有關`parallel_for`演算法，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`cooperative-semaphore.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 合作式 semaphore.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 您可以使用*資源擷取即初始化*(RAII) 模式，限制存取`semaphore`給定範圍的物件。 下 RAII 模式，是在堆疊上配置的資料結構。 該資料結構初始化或建立和終結或終結的資料結構時，釋放該資源時，取得資源。 RAII 模式可確保解構函式稱為封入範圍結束之前。 因此，資源正確管理時擲回例外狀況，或函式包含多個`return`陳述式。  
  
 下列範例定義一個類別，名為`scoped_lock`，定義在`public`區段`semaphore`類別。 `scoped_lock`類別類似於[concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別。 建構函式`semaphore::scoped_lock`類別取得存取給定`semaphore`物件和解構函式釋放該物件的存取權。  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]    
 下列範例會修改傳遞至工作函式的主體`parallel_for`演算法，因此它會使用 RAII 確保函式傳回前釋放號誌。 這項技術可確保工作函式例外狀況安全。  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [內容](../../parallel/concrt/contexts.md)   
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)

