---
title: "Avoidance of Heap Contention | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "heap contention"
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Avoidance of Heap Contention
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 和 ATL 提供的預設字串處理常式是一個簡單的包裝函式在全域堆積的頂端。  這個全域堆積完全是安全執行緒，這表示多個執行緒可以同時從其配置和釋放記憶體，而不用損毀堆積。  為了協助提供執行緒安全，堆積必須序列化對其本身的存取權。  這通常是利用關鍵區段或類似的鎖定機制。  當兩個執行緒嘗試同時存取堆積，一個執行緒會被封鎖，直到其他執行緒的要求完成。  對於許多應用程式而言，這種情況很少發生，而且堆積的鎖定機制的效能影響微不足道時。  不過，對於經常存取的應用程式從堆積中的多個執行緒上的鎖定的爭用可能會導致應用程式執行速度比，如果它是單一執行緒的 \(即使在具有多個 CPU 的電腦\)。  
  
 使用 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 的應用程式特別容易受到堆積爭用情形，因為在 `CStringT` 物件的作業通常需要字串緩衝區的轉散發。  
  
 其中一個方式可減少在執行緒之間的堆積爭用會讓每個執行緒從私用配置字串，執行緒區域堆積。  只要字串配置與特定執行緒的配置器會在該執行緒中使用，這個配置器不需要具備執行緒安全。  
  
## 範例  
 下列範例會示範轉散發的私用非安全執行緒堆積是針對該執行緒的字串使用的執行緒程序:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/CPP/avoidance-of-heap-contention_1.cpp)]  
  
## 註解  
 多個執行緒可以使用這個相同執行緒程序，但是，因為每個執行緒有自己的堆積不會在執行緒之間的爭用。  此外，這項事實每個堆積不是安全執行緒將效能的測量的擴充，即使執行緒的一個複本執行。  這是堆積的結果不使用高度耗費資源的連鎖的作業可以防止並行存取。  
  
 對於較複雜的執行緒程序，儲存指標對於執行緒的字串處理常式則會在執行緒區域儲存區 \(TLS\) 位置可能會很方便。  這可讓執行緒程序呼叫之其他函式存取執行緒的資料處理常式。  
  
## 請參閱  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)