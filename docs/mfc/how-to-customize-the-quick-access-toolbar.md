---
title: "如何：自訂快速存取工具列 | Microsoft Docs"
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
  - "快速存取工具列, 自訂"
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：自訂快速存取工具列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快速存取工具列 \(QAT\) 是包含一組命令會顯示在應用程式按鈕旁邊或在 CL 選項下的可自訂的工具列。  下列圖例中將顯示一般的快速存取工具列。  
  
 ![MFC 功能區快速存取工具列](../mfc/media/quick_access_toolbar.png "Quick\_Access\_Toolbar")  
  
 若要自訂快速存取工具列，請開啟它在 \[**屬性**\] 視窗中，修改它的命令，然後預覽功能區控制項。  
  
### 開啟屬性視窗的快速存取工具列  
  
1.  在 Visual Studio 中，按一下 \[**檢視**\] 功能表上，按一下 \[**資源檢視**\]。  
  
2.  在 \[**資源檢視**\] 中，按兩下功能區資源顯示在設計介面上。  
  
3.  在設計介面上，以滑鼠右鍵按一下快速存取工具列功能表然後按一下 \[**屬性**\]。  
  
## 快速存取工具列屬性  
 下表定義快速存取工具列的屬性。  
  
|屬性|定義|  
|--------|--------|  
|QAT 位置|當應用程式啟動時，指定快速存取工具列的位置。  位置可以是 \[**上面**\] 或 \[**下面**\] 功能區控制項。|  
|QAT 項目|指定快速存取工具列時可用的命令。|  
  
#### 新增或移除在快速存取工具列的命令  
  
1.  在 \[**屬性**\] 視窗中，按一下 \[**QAT Items**\]，然後按一下省略按鈕 **\(...\)** 。  
  
2.  在 \[**QAT 項目編輯器**\] 對話方塊中，使用 \[**加入**\] 和 \[**移除**\] 按鈕會在快速存取工具列的命令清單。  
  
3.  如果您想要命令會顯示在快速存取工具列、快速存取工具列功能表，請在命令旁邊選取方塊。  如果您想要命令只會出現在功能表中，清除方塊。  
  
## 預覽功能區  
 快速存取工具列命令未出現在設計介面上。  若要檢視它們，您必須預覽功能區或執行應用程式。  
  
#### 預覽功能區控制項  
  
-   在 \[**Ribbon 編輯器**\] 工具列中，按一下 \[**測試 Ribbon**\] 按鈕。  
  
## 請參閱  
 [功能區設計工具 \(MFC\)](../mfc/ribbon-designer-mfc.md)