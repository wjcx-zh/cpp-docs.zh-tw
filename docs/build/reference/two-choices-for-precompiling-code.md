---
title: "先行編譯程式碼的兩個選擇 | Microsoft Docs"
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
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案"
  - ".pch 檔案, 先行編譯選項"
  - "自動先行編譯"
  - "程式碼, 先行編譯"
  - "編譯原始程式碼, 先行編譯"
  - "PCH 檔案"
  - "PCH 檔案, 先行編譯選項"
  - "先行編譯標頭檔"
  - "先行編譯標頭檔, 先行編譯選項"
  - "先行編譯程式碼"
ms.assetid: f50ac76f-e2a2-462d-bda5-0e2ab7cccdeb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 先行編譯程式碼的兩個選擇
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 Visual C\+\+，您可先行編譯任何 C 或 C\+\+ 程式碼；並不限於只能先行編譯標頭檔。  
  
 先行編譯需要事先規劃，但若是您先行編譯原始程式碼 \(而非簡單標頭檔\)，則它可提供速度大幅提升的編譯作業。  
  
 當您知道您的原始程式檔使用標頭檔的通用集，但不以相同順序加以併入時，或是您要在先行編譯中包含原始程式碼時，請先行編譯程式碼。  
  
 先行編譯標頭選項為 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)。  使用 **\/Yc**，建立先行編譯標頭。  在搭配選擇性 `hdrstop` pragma 使用時，**\/Yc** 可讓您先行編譯標頭檔和原始程式碼。  選取 **\/Yu** 選項，可使用現有編譯中現有的先行編譯標頭。  您也可以使用 **\/Fp** 配合 **\/Yc** 和 **\/Yu** 選項，以提供先行編譯標頭的替代名稱。  
  
 **\/Yu** 和 **\/Yc** 的編譯器選項參考主題會探討如何在開發環境中存取這項功能。  
  
## 詳細資訊  
  
-   [先行編譯原始程式碼的時機](../../build/reference/when-to-precompile-source-code.md)  
  
-   [先行編譯標頭的一致性規則](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [在專案中使用先行編譯的標頭](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 如需使用先行編譯標頭的進一步範例，請參閱用來建置隨附 Microsoft Foundation Class 程式庫之範例程式的 Makefile。  
  
## 請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)