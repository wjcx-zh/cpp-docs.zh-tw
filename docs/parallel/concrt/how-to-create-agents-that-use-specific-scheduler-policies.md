---
title: "如何：建立使用特定排程器原則的代理程式 | Microsoft Docs"
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
  - "排程器原則，代理程式 [並行執行階段]"
  - "建立使用特定原則的代理程式 [並行執行階段]"
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立使用特定排程器原則的代理程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代理程式是一種應用程式元件，它會以非同步方式與其他元件合作解決較複雜的運算工作。  代理程式通常已設定生命週期，並且會有狀態。  
  
 每個代理程式可能各有獨特的應用程式需求。  例如，允許使用者互動 \(例如擷取輸入或顯示輸出\) 的代理程式可能需要對運算資源擁有較高優先順序的存取權。  排程器原則可讓您控制排程器在管理工作時所使用的策略。  本主題示範如何建立會使用特定排程器原則的代理程式。  
  
 如需搭配使用自訂排程器原則與非同步訊息區塊的基本範例，請參閱 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
 本主題會使用非同步代理程式程式庫中的功能 \(例如代理程式、訊息區塊和訊息傳遞函式\) 來執行工作。  如需非同步代理程式程式庫的詳細資訊，請參閱[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)。  
  
## 範例  
 下列範例定義衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的兩個類別：`permutor` 和 `printer`。  `permutor` 類別會計算指定之輸入字串的所有排列。  `printer` 類別會將進度訊息列印至主控台。  `permutor` 類別會執行可能會用掉所有可用運算資源的密集運算作業。  `printer` 類別必須要即時列印每則進度訊息才會有用。  
  
 為了讓 `printer` 類別能夠公平存取運算資源，這個範例會使用 [如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)所述的步驟來建立具有自訂原則的排程器執行個體。  這個自訂原則會指定讓這個執行緒具有最高等級的優先順序。  
  
 為了說明使用具有自訂原則之排程器的優點，這個範例會執行整個工作兩次。  這個範例會先使用預設排程器來排程兩項工作。  這個範例接著會使用預設排程器來排定 `permutor` 物件，並且使用具有自訂原則的排程器來排定 `printer` 物件。  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/CPP/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **With default scheduler:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...**  
**With higher context priority:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...** 雖然兩組工作產生的結果相同，但是使用自訂原則的版本可讓 `printer` 物件以更高的優先順序執行，因而有更佳的回應性。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `permute-strings.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc permute\-strings.cpp**  
  
## 請參閱  
 [排程器原則](../../parallel/concrt/scheduler-policies.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 