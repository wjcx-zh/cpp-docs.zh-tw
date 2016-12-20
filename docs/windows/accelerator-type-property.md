---
title: "快速鍵類型屬性 | Microsoft Docs"
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
  - "Type 屬性"
  - "VIRTKEY"
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 快速鍵類型屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快速鍵的 \[類型\] 屬性，可以決定與快速鍵 ID 關聯的快速鍵組合是虛擬組合鍵還是 ASCII\/ANSI 按鍵值：：  
  
-   如果 \[類型\] 屬性是 \[ASCII\]，[輔助按鍵](../windows/accelerator-modifier-property.md)可能只會是無 \(None\) 或 Alt，否則它便會擁有一個使用 Ctrl 鍵的快速鍵 \(在按鍵前面以 ^ 指定\)。  
  
-   如果 \[類型\] 屬性為 \[VIRTKEY\]，任何輔助按鍵和按鍵值的組合都有效。  
  
    > [!NOTE]
    >  若您想要在快速鍵對應表輸入一值，且該值為 ASCII\/ANSI 類型，您只需在對應表中按一下該項目的 \[類型\]，並從下拉式清單中選取 \[ASCII\] 即可。  不過，如果您使用 \[下一個輸入的按鍵\] 命令 \(\[編輯\] 功能表\) 來指定按鍵，您必須在輸入按鍵碼之前，先將 \[類型\] 屬性從 \[VIRTKEY\] 變更為 \[ASCII\]。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)