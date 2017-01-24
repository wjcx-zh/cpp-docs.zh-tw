---
title: "記憶體管理：範例 | Microsoft Docs"
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
  - "陣列 [C++], 配置資源"
  - "陣列 [C++], 記憶體管理"
  - "資料結構 [C++]"
  - "資料結構 [C++], 配置記憶體"
  - "範例 [MFC], 記憶體配置"
  - "框架配置"
  - "堆積配置, 範例"
  - "記憶體配置 [C++], 陣列"
  - "記憶體配置 [C++], 資料結構"
  - "記憶體配置 [C++], 範例"
  - "記憶體配置 [C++], 物件"
  - "MFC [C++], 記憶體管理"
  - "物件 [C++], 配置記憶體"
  - "物件 [C++], 記憶體配置"
  - "結構記憶體配置"
  - "類型 [C++], 記憶體配置"
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記憶體管理：範例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 執行如何框架配置和堆積配置這三種常見的每一個記憶體配置:  
  
-   [位元組陣列](#_core_allocation_of_an_array_of_bytes)  
  
-   [資料結構](#_core_allocation_of_a_data_structure)  
  
-   [物件](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> 陣列的配置位元組  
  
#### 配置陣列在框架的位元組。  
  
1.  定義陣列如下列程式碼所示。  陣列，其記憶體自動回收，當變數關閉它的範圍。  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/CPP/memory-management-examples_1.cpp)]  
  
#### 將位元組陣列或任何基本資料型別\) 在堆積  
  
1.  使用這個範例中顯示的陣列語法的 **new** 運算子:  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/CPP/memory-management-examples_2.cpp)]  
  
#### 解除配置從堆積的陣列  
  
1.  使用 **delete** 運算子如下:  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/CPP/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> 資料結構的配置  
  
#### 配置在框架中的資料結構。  
  
1.  定義結構變數:  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/CPP/memory-management-examples_4.cpp)]  
  
     當它結束其範圍時，結構所佔用的記憶體回收。  
  
#### 配置在堆積的資料結構。  
  
1.  使用配置在堆積 **new** 和 **delete** 的資料結構解除配置它們，如下所示的範例:  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/CPP/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> 物件的配置  
  
#### 配置在框架的物件  
  
1.  宣告物件如下:  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/CPP/memory-management-examples_6.cpp)]  
  
     當物件完成其範圍時，物件的解構函式自動叫用。  
  
#### 配置在堆積上的物件  
  
1.  使用 **new** 運算子，將指標傳回物件，則會配置在堆積上的物件。  使用 **delete** 運算子刪除它們。  
  
     下列堆積和架構範例假設， `CPerson` 建構函式不接受引數。  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/CPP/memory-management-examples_7.cpp)]  
  
     如果 `CPerson` 建構函式的引數是指向 `char`，框架配置的陳述式是:  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/CPP/memory-management-examples_8.cpp)]  
  
     堆疊配置的陳述式是:  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/CPP/memory-management-examples_9.cpp)]  
  
## 請參閱  
 [記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)