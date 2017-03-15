---
title: "Makefile 中的特殊字元 | Microsoft Docs"
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
  - "巨集, 特殊字元"
  - "Makefile, 特殊字元"
  - "NMAKE 程式, 特殊字元"
  - "特殊字元, NMAKE 巨集中"
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Makefile 中的特殊字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要將 NMAKE 特殊字元當做常值字元使用，請在該字元前面放置插入號 \(^\)。  NMAKE 會忽略在其他字元前面的插入號。  特殊字元為：  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 引號所包夾字串中的插入號 \(^\) 會被視為常值插入號字元。  在行結尾處的插入號會在字串或巨集中插入常值新行字元。  
  
 在巨集中會以空格取代有新行字元跟隨在後的反斜線 \(\\\)。  
  
 在命令中的百分比符號 \(%\) 是檔案規範。  若要在命令中以常值表示 %，請指定雙百分比符號 \(%%\) 取代單一的百分比符號。  在其他情況下，NMAKE 會將單一的 % 解譯為常值，但永遠會把雙的 %% 解譯為單一的 %。  因此，若要表示常值 %%，請指定三個百分比符號 %%%，或四個百分比符號 %%%%。  
  
 若要在命令中將貨幣符號 \($\) 當成常值字元使用，請指定兩個貨幣符號 \($$\)。  使用 ^$ 時，也可在其他情況中用這個方法。  
  
## 請參閱  
 [Makefile 內容](../build/contents-of-a-makefile.md)