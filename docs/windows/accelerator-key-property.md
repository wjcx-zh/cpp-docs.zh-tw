---
title: "快速鍵按鍵屬性 | Microsoft Docs"
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
  - "Key 屬性"
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 快速鍵按鍵屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下列出快速鍵 \(Accelerator\) 對應表中按鍵屬性的合法項目：  
  
-   介於 0 至 255 的十進位整數。  這個值可依下列情形，決定其將被視為 ASCII 或 ANSI：  
  
    -   單一數字的數值永遠會解譯成對應的按鍵，而不會解譯成 ASCII 或 ANSI 值。  
  
    -   前面冠上零的 1 到 26 的數值，會解譯成 ^A 到 ^Z，這分別代表配合按住 CTRL 鍵時 26 個字母的 ASCII 值。  
  
    -   27 到 32 之間的數值永遠會解譯成 027 到 032 之間之三位數的十進位值。  
  
    -   而 033 到 255 的數值，前面無論是否冠上零，都會解譯成 ANSI 值。  
  
-   單一鍵盤字元。  大寫的 A\-Z 或數字的 0\-9 可以是 ASCII 或虛擬按鍵值；而其他的字元就只能是 ASCII。  
  
-   前面冠上插入號 \(^\) 並介於 A\-Z 範圍內 \(僅有大寫字母\) 的鍵盤字元 \(例如 ^C\)。  這個項目會輸入按住 CTRL 鍵並同時按下該按鍵時的 ASCII 值。  
  
    > [!NOTE]
    >  輔助按鍵屬性選項在輸入 ASCII 值時會受到限制。  唯一可用的控制鍵是 ALT 鍵。  
  
-   任何有效的虛擬按鍵識別項。  快速鍵對應表中的下拉按鍵方塊包含了一份標準的虛擬按鍵識別項清單。  
  
    > [!TIP]
    >  另一種定義快速鍵的方式是在快速鍵對應表的某個項目或多個項目上按一下滑鼠右鍵，選擇捷徑功能表中的 \[下一個輸入的按鍵\]，接著按下鍵盤中的任一個按鍵或組合鍵。  \[下一個輸入的按鍵\] 命令也可以從 \[編輯\] 功能表中使用。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Editing in an Accelerator Table](../windows/editing-in-an-accelerator-table.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)