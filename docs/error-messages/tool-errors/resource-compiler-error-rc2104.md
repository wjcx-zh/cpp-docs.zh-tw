---
title: "資源編譯器錯誤 RC2104 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2104"
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 資源編譯器錯誤 RC2104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未定義的關鍵字或索引鍵名稱：索引鍵  
  
 未定義指定的關鍵字或索引鍵名稱。  
  
 這個錯誤經常是由於資源定義中或包含的標頭檔中的錯字所導致。  也可能是因為標頭檔遺失而導致。  
  
 若要修正這個問題，請找出應包含已定義的關鍵字或索引鍵名稱的標頭檔，並確認您的資源檔中包含它，且關鍵字或索引鍵名稱的拼字正確。  如果您的專案在建立時具有先行編譯標頭，但是後來將它移除，請確定資源檔仍然包含任何必要的標頭。  
  
 若要確認資源檔中已定義的關鍵字和索引鍵名稱，請在 Visual Studio 中開啟 \[資源檢視\] 視窗，在功能表列上，選擇 \[檢視\]、\[資源檢視\]，然後開啟 .rc 檔的捷徑功能表，再選擇 \[資源符號\] 來檢視已定義的符號清單。  若要修改包含的標頭，請開啟 .rc 檔的捷徑功能表，然後選擇 \[Resource Includes\]。  
  
 如果您遇到此訊息：  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 開啟 \\MCL\\MFC\\Include\\AfxRes.h，並加入這個 include 指示詞：  
  
```  
#include <winresrc.h>  
```