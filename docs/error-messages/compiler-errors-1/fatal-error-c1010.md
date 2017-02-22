---
title: "嚴重錯誤 C1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1010"
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 嚴重錯誤 C1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找先行編譯標頭檔時找到未預期的檔案結尾。您的原始檔中是否忘了加上 '\#include name'?  
  
 使用 [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 指定的包含檔案沒有列於原始程式檔。這個選項在大部分 Visual C\+\+ 專案中是預設為啟用，而且 "stdafx.h" 是由這個選項指定的預設 include 檔。  
  
 在 Visual Studio 環境中，請使用下列方法解決這項錯誤：  
  
-   如果您在專案中不使用先行編譯標頭檔，請將原始程式檔的 \[建立\/使用先行編譯標頭\] 屬性設定為 \[**未使用先行編譯標頭檔**\]。  若要設定這個編譯器選項，請執行下列步驟：  
  
    1.  在專案的 \[方案總管\] 窗格中，用右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  
  
    2.  在左邊的窗格中，按一下 \[C\/C\+\+\] 資料夾。  
  
    3.  按一下 \[先行編譯標頭\] 節點。  
  
    4.  在右窗格中，按一下 \[建立\/使用先行編譯標頭\]，然後按一下 \[**未使用先行編譯標頭檔**\]。  
  
-   請確定您沒有不小心從目前專案中刪除、重新命名或移除標頭檔 \(預設值為 stdafx.h\)。  必須先將這個檔案包括在內，才能讓原始程式檔中的任何其他程式碼使用 **\#include "stdafx.h"** \(這個標頭檔是指定為 \[透過檔案建立\/使用 PCH\] 專案屬性\)。