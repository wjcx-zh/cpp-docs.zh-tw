---
title: "如何：偵錯發行的組建 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [C++], 發行組建"
  - "發行組建, 偵錯"
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：偵錯發行的組建
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以偵錯應用程式的發行組建。  
  
### 若要偵錯發行組建  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 節點。  將 \[**偵錯資訊格式**\] 設定為 [C7 相容 \(\/Z7\)](../../build/reference/z7-zi-zi-debug-information-format.md) 或 \[**程式資料庫 \(\/Zi\)**\]。  
  
3.  展開 \[**連結器**\]，然後按一下 \[**一般**\] 節點。  將 \[**啟用累加連結**\] 設定為[否 \(\/INCREMENTAL:NO\)](../../build/reference/incremental-link-incrementally.md)。  
  
4.  選取 \[**偵錯**\] 節點。  將 \[**產生偵錯資訊**\] 設定為[是 \(\/DEBUG\)](../../build/reference/debug-generate-debug-info.md)。  
  
5.  選取 \[**最佳化**\] 節點。  將 \[**參考**\] 設定為 [\/OPT:REF](../../build/reference/opt-optimizations.md)，並將 \[**啟用 COMDAT 摺疊**\] 設定為 [\/OPT:ICF](../../build/reference/opt-optimizations.md)。  
  
6.  現在，您可偵錯發行組建的應用程式。  若要找出問題，請逐步執行程式碼 \(或使用 Just\-In\-Time 偵錯\)，直到找到發生失敗的位置，然後判斷不正確的參數或程式碼。  
  
     如果應用程式是在偵錯組建中運作，但在發行組建中失敗，則編譯器的某一個最佳化動作可能造成原始程式碼的缺失。  若要隔離問題，請停用每個來源程式碼檔案中所選取的最佳化，直到找出造成問題的檔案和最佳化為止。\(若要加快處理序，您可以將檔案分割成兩個群組，停用一個群組的最佳化，而當您找到群組中的問題時，繼續進行分割，直到隔離問題檔案為止。\)  
  
     您可以使用 [\/RTC](../../build/reference/rtc-run-time-error-checks.md) 嘗試在偵錯組建中發現這些錯誤。  
  
     如需詳細資訊，請參閱[最佳化程式碼](../../build/reference/optimizing-your-code.md)。  
  
## 請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)