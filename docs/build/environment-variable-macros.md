---
title: "環境變數巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "環境變數, NMAKE 中的巨集"
  - "巨集, 環境變數"
  - "NMAKE 程式, 環境變數巨集"
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 環境變數巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 繼承在工作階段開始之前就存在的環境變數巨集定義。  如果變數是在作業系統環境中設定，便可當做 NMAKE 巨集來使用。  繼承的名字會轉換成大寫。  在前置處理之前會發生繼承。  使用 \/E 選項導致繼承自環境變數的巨集覆寫在 Makefile 中相同名稱的任何巨集。  
  
 環境變數巨集可以在工作階段中重新定義，而這會變更對應的環境變數。  您也可以使用 SET 命令變更環境變數。  不過，在工作階段中使用 SET 命令變更環境變數，並不會變更對應的巨集。  
  
 例如：  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 在這個範例中，變更 `PATH` 會變更對應的環境變數 `PATH`；會將 `\nonesuch` 附加至您的路徑。  
  
 如果環境變數是定義成在 Makefile 中會出現句法不正確的字串，就不會建立巨集，也不會產生警告。  如果變數的值包含貨幣符號 \($\)，NMAKE 會將它解讀為巨集引動過程的開頭。  使用巨集可能會引起未預期的行為。  
  
## 請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)