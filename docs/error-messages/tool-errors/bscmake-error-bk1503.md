---
title: "BSCMAKE 錯誤 BK1503 | Microsoft Docs"
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
  - "BK1503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1503"
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 錯誤 BK1503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法寫入檔案 'filename' \[: reason\]  
  
 BSCMAKE 會將編譯過程中產生的 .sbr 檔案結合至一個瀏覽器資料庫中，  如果產生的瀏覽器資料庫超過 64 MB，或是輸入的 \(.sbr\) 檔案數量超過 4092 時，將發生此錯誤。  
  
 如果是因為超過 4092 個 .sbr 檔案而造成此錯誤，您必須減少輸入的檔案數量。  在 Visual Studio 中，可以藉由 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) 整個專案，然後以檔案為單位重新選取檔案，來達成這個目的。  
  
 如果是因為 .bsc 檔案超過 64 MB 而造成此錯誤，減少輸入的 .sbr 檔案數量將可縮小產生的 .bsc 檔案的大小。  此外，瀏覽資訊的數量還可以利用 \/Em \(排除巨集擴充符號\)、\/El \(排除區域變數\) 和 \/Es \(排除系統檔案\) 來減少。  
  
## 請參閱  
 [BSCMAKE 選項](../../build/reference/bscmake-options.md)