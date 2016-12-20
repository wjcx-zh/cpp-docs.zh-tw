---
title: "如何：在資料管線中使用轉換程式 | Microsoft Docs"
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
  - "transformer 類別，範例"
  - "資料管線，使用轉換程式 [並行執行階段]"
  - "在資料管線中使用轉換程式 [並行執行階段]"
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在資料管線中使用轉換程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此主題包含基本的範例顯示如何在資料管道使用  [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 類別。  如需使用資料管線平行執行影像處理的更完整的範例，請參閱[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 「*資料管線*」\(Data Pipelining\) 是並行程式設計中常見的模式。  資料管線是由一系列的階段所組成，其中每個階段分別會執行工作，然後將該工作的結果傳遞至下一個階段。  `transformer` 類別是資料管線中的一項主要元件，因為它會接收輸入值、執行該值的工作，然後產生結果供其他元件使用。  
  
## 範例  
 此範例會使用下列資料管線，以指定的初始輸入值執行一系列的轉換：  
  
1.  第一個階段會計算其輸入的絕對值。  
  
2.  第二個階段會計算其輸入的平方根。  
  
3.  第三個階段會計算其輸入的平方。  
  
4.  第四個階段會變換其輸入的正負號。  
  
5.  第五個階段會將最後的結果寫入訊息緩衝區中。  
  
 最後，此範例會將管線的結果列印到主控台。  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/CPP/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 這個範例會產生下列輸出：  
  
  **結果為 \-42。** 資料管線中的階段常會輸出類型與其輸入值不同的值。  在此範例中，第二個階段以類型 `int` 的值做為其輸入，並產生了該值的平方根 \(`double`\) 做為其輸出。  
  
> [!NOTE]
>  這個範例中的資料管線僅供舉例之用。  因為每個轉換作業執行少量工作，執行訊息傳遞所需的額外負荷可能大於使用資料管線的好處。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `data-pipeline.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc data\-pipeline.cpp**  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)