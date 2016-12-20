---
title: "專案建置錯誤 PRJ0008 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0008"
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法刪除檔案 'file'。  
  
 **請確認其他處理序並未開啟該檔案，且並非寫入保護。**  
  
 在重建或清除期間，Visual C\+\+ 會刪除組建的所有已知的中繼和輸出檔，以及任何符合[一般組態設定屬性頁](../../ide/general-property-page-project.md)中的 \[清除時要刪除的副檔名\] 屬性中的萬用字元指定的檔案。  
  
 如果 Visual C\+\+ 無法刪除檔案，您將會看到這個錯誤。  若要解決這個錯誤，請讓檔案及其目錄可供使用者寫入以執行建置。