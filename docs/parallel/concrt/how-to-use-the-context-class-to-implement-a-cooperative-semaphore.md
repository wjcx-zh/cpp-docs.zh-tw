---
title: "如何：使用內容類別實作合作式信號 | Microsoft Docs"
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
helpviewer_keywords: 
  - "合作式信號實作"
  - "context 類別"
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用內容類別實作合作式信號
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何使用 concurrency:: context 類別實作合作式信號類別。  
  
  `Context` 類別可讓您封鎖或產生目前的執行內容。 封鎖或產生目前的內容時，因為資源無法使用，無法繼續目前的內容。 A *號誌* 是一種情況下，目前的執行內容必須等候資源變成可用資源的範例。 號誌，像重要區段物件，就可讓程式碼在具有獨佔存取資源的內容中的同步處理物件。 不過，與不同的是一個重要區段物件，一個號誌啟用同時存取資源的多個內容。 如果內容的最大數目掌握號誌的鎖定，每個額外的內容必須等待另一個內容，以便釋放鎖定。  
  
### <a name="to-implement-the-semaphore-class"></a>若要實作 semaphore 類別  
  
1.  宣告的類別，名為 `semaphore`。 新增 `public` 和 `private` 區段，這個類別。  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  在 `private` 區段 `semaphore` 類別中，宣告 [std:: atomic](../../standard-library/atomic-structure.md) 保留號誌計數的變數和 [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 保存內容，必須等候取得號誌的物件。  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  在 `public` 區段 `semaphore` 類別也會實作建構函式。 建構函式接受 `long long` 值，指定可以同時將鎖定的內容的最大數目。  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  
  
4.  在 `public` 區段 `semaphore` 類別也會實作 `acquire` 方法。 這個方法會遞減號誌計數成為不可部分完成的作業。 號誌計數變成負數時，如果需要等候佇列和呼叫的結尾加入目前的內容 [concurrency::Context::Block](../Topic/Context::Block%20Method.md) 方法來封鎖目前的內容。  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  在 `public` 區段 `semaphore` 類別也會實作 `release` 方法。 這個方法會遞增號誌計數，成為不可部分完成的作業。 號誌計數為負數遞增作業之前，如果沒有至少一個正在等候鎖定的內容。 在此情況下，解除封鎖在等候佇列的前面的內容。  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>範例  
  `semaphore` 因為在此範例中的類別行為以合作方式 `Context::Block` 和 `Context::Yield` 方法會先執行，以便讓執行階段執行其他工作。  
  
  `acquire` 方法遞減計數器，但它可能會無法完成將內容加入至另一個內容呼叫之前的等候佇列 `release` 方法。 為了說明這點， `release` 方法會使用呼叫的微調迴圈 [yield](../Topic/Context::Yield%20Method.md) 方法等候 `acquire` 方法，以完成新增內容。  
  
  `release` 方法可以呼叫 `Context::Unblock` 方法，然後再 `acquire` 方法呼叫 `Context::Block` 方法。 您不需要為了防止這種競爭情形，因為執行階段可讓您以任何順序來呼叫這些方法。 如果 `release` 方法呼叫 `Context::Unblock` 之前 `acquire` 方法呼叫 `Context::Block` 該內容就會針對相同的內容保持解除封鎖。 執行階段只會要求每個呼叫到 `Context::Block` 符合對應呼叫 `Context::Unblock`。  
  
 下列範例顯示完整 `semaphore` 類別。  `wmain` 函式會顯示這個類別的基本使用方式。  `wmain` 函式使用 [concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 演算法建立需要存取之號誌的幾項工作。 因為有三個執行緒可以在任何時間持有的鎖定，一些工作必須等候另一個工作完成並釋出鎖定。  
  
 [!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]  
  
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
  
 如需詳細資訊 `concurrent_queue` 類別，請參閱 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。 如需詳細資訊 `parallel_for` 演算法，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼並將它貼在 Visual Studio 專案中，或貼入名為的檔案 `cooperative-semaphore.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc 合作式 semaphore.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 您可以使用 *資源獲取即為初始化* (RAII) 模式，限制存取 `semaphore` 給定範圍的物件。 RAII 模式，在堆疊上配置資料結構。 該資料結構初始化或建立和終結或終結的資料結構時釋放該資源時，取得資源。 RAII 模式可確保，在封閉範圍結束之前，呼叫解構函式。 因此，資源受到妥善管理擲回例外狀況時，或函式包含多個 `return` 陳述式。  
  
 下列範例會定義一個類別，名為 `scoped_lock`, ，定義在 `public` 區段 `semaphore` 類別。  `scoped_lock` 類別類似於 [concurrency::critical_section::scoped_lock](../Topic/critical_section::scoped_lock%20Class.md) 和 [concurrency::reader_writer_lock::scoped_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md) 類別。 建構函式 `semaphore::scoped_lock` 類別取得存取指定 `semaphore` 物件和解構函式釋放該物件的存取權。  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]  
  
 下列範例會修改傳遞至工作函式主體 `parallel_for` 演算法，因此它會使用 RAII 確保函式傳回之前釋放號誌。 這項技術可確保工作函式例外狀況之虞。  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [內容](../../parallel/concrt/contexts.md)   
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)

