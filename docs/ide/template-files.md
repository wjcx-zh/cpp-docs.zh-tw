---
title: "範本檔案 | Microsoft Docs"
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
  - "自訂精靈, 範本檔案"
  - "檔案 [C++], 由自訂精靈建立"
  - "範本 [C++], 精靈"
ms.assetid: 48fae3d8-3a53-4f62-8010-144c5ffe334e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 範本檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

組成精靈的樣板是一個文字檔的集合物件，其包含某些[簡單指示詞](../ide/template-directives.md)，並根據使用者輸入進行剖析和轉譯，以及加入至初始專案。  取得用於剖析範本之正確資訊的方法，是直接存取精靈控制項的符號表。  
  
 下列範例是一個非常簡單的樣板檔案，其中精靈要求使用者選取 A 或 B。  
  
## 範例  
  
```  
This file has been created by My Custom wizard.  
You selected:  
[!if TYPE_A]  
Type A  
[!else]  
Type B  
[!endif]  
The name of this project is [!output PROJECT_NAME].root.cpp:  
```  
  
 如果使用者選擇 Type B，則上述範本將被轉譯為如下：  
  
  **這個檔案已經由 \[我的自訂精靈\] 建立。  您已選取：**  
**B 類型**  
**此專案的名稱是 MyApp8。**    
## Output  
  
```  
This file has been created by My Custom wizard.  
You selected:  
Type B  
The name of this project is MyApp8.  
```  
  
 **注意**：上述語法為 Visual C\+\+ .NET 的新語法。  Visual C\+\+ .NET 中未支援 Visual C\+\+ 的舊版語法。  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [Templates.inf 檔案](../ide/templates-inf-file.md)