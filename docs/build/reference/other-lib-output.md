---
title: "其他 LIB 輸出 | Microsoft Docs"
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
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸出檔, LIB"
ms.assetid: 656864a6-0b7a-4633-8dc6-ee3b1766d836
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 其他 LIB 輸出
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在預設模式中，您可以使用 \/LIST 選項顯示有關產生之程式庫的資訊。  您可以把這個輸出重新導向至檔案中。  
  
 除非使用了 \/NOLOGO 選項，否則 LIB 會顯示著作權和版本訊息並回應 \(Echo\) 命令檔案。  
  
 當您只輸入 `lib` 而沒有其他輸入，LIB 會顯示摘要其選項的用法說明。  
  
 LIB 發出的錯誤和警告訊息具有 LNK*nnnn* 的格式。  LINK、DUMPBIN 和 EDITBIN 工具也使用這個範圍的錯誤訊息。  說明可以經由選取 \[輸出\] 視窗的錯誤訊息並按下 F1 來取得。  
  
## 請參閱  
 [LIB 概觀](../../build/reference/overview-of-lib.md)