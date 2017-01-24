---
title: "如何：在已完成的工作之中選取 | Microsoft Docs"
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
  - "在已完成的工作中選取 [並行執行階段]"
  - "已完成的工作，在 [並行執行階段] 中選取"
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在已完成的工作之中選取
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此範例說明如何使用 [concurrency::choice](../../parallel/concrt/reference/choice-class.md) 和 [concurrency::join](../../parallel/concrt/reference/join-class.md) 類別，選取第一項要完成搜尋演算法的工作。  
  
## 範例  
 下列範例會以平行方式執行兩個搜尋演算法，並選取第一個要完成的演算法。  此範例會定義 `employee` 類型；此類型包含某員工的數值識別碼和薪資。  `find_employee` 函式會尋找第一個具有所提供之識別碼或薪資的員工。  `find_employee` 函式也會在沒有任何員工具有提供的識別碼或薪資時，處理此一情況。  `wmain` 函式會建立 `employee` 物件的陣列，並搜尋數個識別碼和薪資值。  
  
 此範例會使用 `choice` 物件來選取下列情況：  
  
1.  有員工具有提供的識別碼。  
  
2.  有員工具有提供的薪資。  
  
3.  沒有任何員工具有提供的識別碼或薪資。  
  
 在前兩種的情況中，此範例會使用 [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) 物件保存識別碼，並使用另一個 `single_assignment` 物件保存薪資。  對於第三種情況，此範例會使用 `join` 物件。  `join` 物件由其他兩個 `single_assignment` 物件所組成，一個適用於沒有任何員工具有提供的識別碼時，另一個則適用於沒有任何員工具有提供的新資時。  `join` 物件會在其每個成員皆收到訊息時傳送訊息。  在此範例中，`join` 物件會在沒有任何員工具有提供的識別碼或薪資時傳送訊息。  
  
 此範例會使用 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件，以平行方式執行這兩個搜尋演算法。  每項搜尋工作分別會寫入到其中一個 `single_assignment` 物件，以指出指定的員工是否存在。  此範例會使用 [concurrency::receive](../Topic/receive%20Function.md) 函式取得第一個包含訊息之緩衝區的索引，並使用 `switch` 區塊列印結果。  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/CPP/how-to-select-among-completed-tasks_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **具有 ID 為 14758 的員工薪資有 27780.00。**  
**具有 ID 為 29150.00 的員工薪資有 84345。**  
**具有 ID 為 61935 的員工薪資有 29905.00。**  
**員工沒有 ID 899 或薪資 31223.00。** 此範例會使用 [concurrency::make\_choice](../Topic/make_choice%20Function.md) Helper 函式來建立 `choice` 物件，並使用 [concurrency::make\_join](../Topic/make_join%20Function.md) Helper 函數來建立 `join` 物件。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `find-employee.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc find\-employee.cpp**  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [choice 類別](../../parallel/concrt/reference/choice-class.md)   
 [join 類別](../../parallel/concrt/reference/join-class.md)