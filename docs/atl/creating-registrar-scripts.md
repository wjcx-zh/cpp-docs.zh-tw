---
title: "Creating Registrar Scripts | Microsoft Docs"
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
  - "ATL, 登錄"
  - "registrar scripts [ATL]"
  - "指令碼, registry scripting"
  - "指令碼, 建立"
  - "指令碼, Registrar scripts"
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating Registrar Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

登錄器指令碼提供資料驅動型，而不是 API，導向至系統登錄的存取。  因為它只會在指令碼中兩行加入機碼，註冊資料驅動型存取通常會比較有效率。  
  
 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md) 自動產生 COM 伺服器的系統管理員指令碼。  您可以在 .rgs 檔案中執行此指令碼與物件相關聯。  
  
 ATL 管理員的指令碼引擎處理您的管理員指令碼在執行階段。  在伺服器上安裝期間， ATL 會自動叫用指令碼引擎。  
  
 本文件包含下列主題使用登錄器指令碼相關:  
  
-   [了解 Backus Nauer 表單 \(BNF\) 語法](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [了解剖析樹狀結構](../atl/understanding-parse-trees.md)  
  
-   [註冊指令碼的範例](../atl/registry-scripting-examples.md)  
  
-   [使用可取代的參數 \(管理員的前置處理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [叫用指令碼](../atl/invoking-scripts.md)  
  
## 請參閱  
 [登錄元件 \(登錄器\)](../atl/atl-registry-component-registrar.md)