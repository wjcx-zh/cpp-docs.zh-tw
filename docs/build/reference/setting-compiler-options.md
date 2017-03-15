---
title: "設定編譯器選項 | Microsoft Docs"
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
  - "cl.exe 編譯器, 設定選項"
  - "編譯器選項, 設定"
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 設定編譯器選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C 和 C\+\+ 編譯器選項可以在開發環境中設定，也可以在命令列上設定。  
  
## 在開發環境中  
 您可以在每個專案的 \[**屬性頁**\] 對話方塊中設定其編譯器選項。  在左窗格中，選取 \[**組態屬性**\]、\[**C\/C\+\+**\]，然後選擇編譯器選項分類。  每個編譯器選項的主題都會描述設定方式，以及各選項位於開發環境中的位置。  如需完整清單，請參閱[編譯器選項](../../build/reference/compiler-options.md)。  
  
## 在開發環境之外  
 您可以在下列位置設定編譯器 \(CL.exe\) 選項：  
  
-   [在命令列上](../../build/reference/compiler-command-line-syntax.md)  
  
-   [在命令檔中](../../build/reference/cl-command-files.md)  
  
-   [在 CL 環境變數中](../../build/reference/cl-environment-variables.md)  
  
 每次叫用 CL 時，都會使用 CL 環境變數中指定的選項。  如果在 CL 環境變數或命令列中指名了某個命令檔，則會使用這個命令檔中所指定的選項。  與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。  
  
 編譯器選項是「由左至右」處理，而且在偵測到衝突時，會採用最後 \(最右邊\) 的選項。  CL 環境變數會在命令列之前處理，所以當 CL 與命令列之間發生任何衝突時，命令列具有優先權。  
  
## 其他編譯器主題  
  
-   [快速編譯](../../build/reference/fast-compilation.md)  
  
-   [CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [編譯器選項](../../build/reference/compiler-options.md)