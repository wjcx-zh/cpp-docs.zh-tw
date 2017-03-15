---
title: "/BIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/bind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BIND editbin 選項"
  - "BIND editbin 選項"
  - "-BIND editbin 選項"
  - "進入點"
  - "進入點, 位址"
  - "匯入位址表格"
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /BIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BIND[:PATH=path]  
```  
  
## 備註  
 這個選項設定可執行檔或 DLL 的匯入位址表 \(IAT\) 中，進入點 \(Entry Point\) 的位址。  使用這個選項可縮短程式的載入時間。  
  
 請在 EDITBIN 命令列上的 *files* 引數中，指定程式的可執行檔和 DLL。  \/BIND 的選擇性引數 *path* 指定了由已指定檔案所使用 DLL 的位置。  請以分號 \(**;**\) 分隔多個目錄。  如果沒有指定 *path*，EDITBIN 會搜尋 PATH 環境變數中指定的目錄。  如果指定了 *path*，EDITBIN 會忽略 PATH 變數。  
  
 依照預設，程式載入器會在載入程式時設定進入點位址。  此過程耗費的時間各異，視程式中參考的 DLL 數目和進入點數目而定。  如果程式已經使用 \/BIND 修改，且可執行檔和其 DLL 的基底位址 \(Base Address\) 與已載入的 DLL 沒有衝突，則作業系統不需要設定這些位址。  在檔案基底位址不正確的情況下，作業系統會重新配置程式的 DLL，並重新計算進入點的位址，因而增加了程式的載入時間。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)