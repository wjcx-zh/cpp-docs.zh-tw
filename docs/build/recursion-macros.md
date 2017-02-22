---
title: "遞迴巨集 | Microsoft Docs"
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
  - "巨集, 遞迴"
  - "NMAKE 程式, 遞迴巨集"
  - "遞迴巨集"
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 遞迴巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用遞迴巨集遞迴呼叫 NMAKE。  遞迴工作階段繼承命令列和環境變數巨集以及 Tools.ini 資訊。  它們不繼承由 Makefile 定義的推斷規則 \(Inference Rule\) 或 **.SUFFIXES** 和 **.PRECIOUS** 規格。  若要將巨集傳遞至遞迴 NMAKE 工作階段，請在遞迴呼叫之前使用 SET 設定環境變數、在遞迴呼叫的命令中定義巨集，或在 Tools.ini 中定義巨集。  
  
|巨集|定義|  
|--------|--------|  
|**MAKE**|原本使用來叫用 NMAKE 的命令。<br /><br /> $\(MAKE\) 巨集會提供 nmake.exe 的完整路徑。|  
|**MAKEDIR**|在叫用 NMAKE 時的目前目錄。|  
|**MAKEFLAGS**|目前生效的選項。  當做 `/$(MAKEFLAGS)` 使用。請注意，不包含 \/F。|  
  
## 請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)