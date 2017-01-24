---
title: "/REBASE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rebase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/REBASE editbin 選項 [C++]"
  - "基底位址 [C++]"
  - "DLL [C++], 連結"
  - "可執行檔 [C++], 基底位址"
  - "REBASE editbin 選項"
  - "-REBASE editbin 選項"
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /REBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/REBASE[:modifiers]  
```  
  
## 備註  
 這個選項可設定指定檔案的基底位址。  EDITBIN 會根據每個檔案大小 \(會進位至最接近 64 的倍數個 KB\)，在連續位址空間中指定新的基底位址。  如需基底位址的詳細資訊，請參閱[基底位址](../../build/reference/base-base-address.md) \(\/BASE\) 連結器選項。  
  
 請在 EDITBIN 命令列上的 *files* 引數中，依所要排列的基底位置順序，指定程式的可執行檔和 DLL。  您可以選擇指定一個或多個 *modifiers*，每個修飾詞之間都以逗號 \(**,**\) 分隔：  
  
|修飾詞|動作|  
|---------|--------|  
|BASE**\=***address*|提供為檔案重新指派基底位址的起始位址。  以十進位數或 C 語言標記法指定 *address*。  如果沒有指定 BASE，預設的起始基底位址為 0x400000。  如果使用 DOWN，則必須指定 BASE，且 *address* 會設定基底位址範圍的結尾。|  
|BASEFILE|建立一個名為 COFFBASE.TXT 的檔案，這個文字檔是 LINK 的 \/BASE 選項所預期的格式。|  
|DOWN|告知 EDITBIN 從結束位址向下重新指派基底位址。  會以所指定的順序重新指派檔案，其中第一個檔案位於位址範圍結尾以下最高的可能位址中。  BASE 必須與 DOWN 一起使用，以確保有足夠的位址空間配置檔案基底位址。  若要判斷指定的檔案所需的位址空間，請針對該檔案執行 EDITBIN \(搭配 \/REBASE\)，並且將顯示的總共大小加上 64 KB。|  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)