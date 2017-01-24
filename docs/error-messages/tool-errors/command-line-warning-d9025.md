---
title: "命令列警告 D9025 | Microsoft Docs"
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
  - "D9025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9025"
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令列警告 D9025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

覆寫 'option1'，以 'option2'  
  
 已指定 *option1* 選項，但之後由 *option2* 加以覆寫。  所以會使用 *option2* 選項。  
  
 如果兩個選項指定了相衝突或不相容的指示詞，則會使用在命令列最右邊選項所指定或隱含的指示詞。  
  
 如果從開發環境編譯時收到這項警告，而且不確定衝突選項所在位置，請考慮下列情況：  
  
-   選項可能會在程式碼或專案的專案設定中指定。  如果查看編譯器的[命令列屬性頁](../../ide/command-line-property-pages.md)，在**所有選項**欄位中看到相衝突的選項，則選項是在專案的屬性中設定的，否則，選項就是在原始程式碼中設定的。  
  
     如果選項是在專案的屬性頁中設定的，請查看編譯器的 \[前置處理器\] 屬性頁 \(方案總管中已選取了專案節點\)。如果該處看不到選項，請檢查 \(方案總管中\) 各個原始程式檔中的 \[前置處理器\] 屬性頁設定，以確定未在該處加入。  
  
     如果選項是在程式碼中設定，可能是在程式碼中或視窗標頭中設定。您也許可以嘗試建立已前置處理的檔案 \([\/P](../../build/reference/p-preprocess-to-a-file.md)\) 並在其中搜尋符號。