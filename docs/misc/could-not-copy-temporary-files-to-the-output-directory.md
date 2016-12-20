---
title: "無法將暫存檔複製至輸出目錄 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_copy_to_run_dir"
ms.assetid: b8b54984-74c9-4b9b-8164-d0d13c141055
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法將暫存檔複製至輸出目錄
專案系統無法將暫存檔複製至輸出目錄。 編譯器一律會建置至中繼目錄 \(例如 obj\\`configname`\)。 在建置程序結束時，專案系統會將檔案從中繼目錄複製至專案輸出目錄。  
  
 如果您編譯的其中一個組件大於 64 KB，並且符合下列其中一個 \(或兩個\) 條件，可能會發生這個問題：  
  
-   您方案所含的專案會編譯成相同的輸出資料夾。  
  
-   其中一個所參考組件或專案的 \[複製到本機\] 屬性設為 False。  
  
 **更正這個錯誤**  
  
-   將個別專案的輸出編譯至不同的資料夾。  
  
-   將所參考組件或專案的 \[複製到本機\] 屬性設為 True。  
  
-   請確認您未開啟 \[物件瀏覽器\] 視窗。  
  
-   請確認您未在另一個 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 執行個體中開啟一個或多個相同的專案。  
  
## 請參閱  
 [NIB：如何：設定參考的 &#91;複製到本機&#93; 屬性](http://msdn.microsoft.com/zh-tw/dfe2ba13-f27f-4356-a481-ea67d5acacbd)