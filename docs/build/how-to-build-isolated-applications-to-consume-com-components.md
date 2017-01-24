---
title: "如何：建置隔離的應用程式以使用 COM 元件 | Microsoft Docs"
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
  - "隔離的應用程式 [C++]"
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：建置隔離的應用程式以使用 COM 元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

隔離的應用程式是指程式中內建資訊清單的應用程式。  您可以建立隔離的應用程式以使用 COM 元件。  
  
### 若要將 COM 參考加入隔離應用程式的資訊清單中  
  
1.  開啟隔離應用程式的專案屬性頁。  
  
2.  展開 \[**組態屬性**\] 節點，然後展開 \[**資訊清單工具**\] 節點。  
  
3.  選取 \[**隔離的 COM**\] 屬性頁，然後將 \[**元件檔名**\] 屬性設定成要讓隔離的應用程式使用的 COM 元件名稱。  
  
4.  按一下 \[**確定**\]。  
  
### 若要在隔離的應用程式中內建資訊清單  
  
1.  開啟隔離應用程式的專案屬性頁。  
  
2.  展開 \[**組態屬性**\] 節點，然後展開 \[**資訊清單工具**\] 節點。  
  
3.  選取 \[**輸入和輸出**\] 屬性頁，然後將 \[**內嵌資訊清單**\] 屬性設為等於 \[**是**\]。  
  
4.  按一下 \[**確定**\]。  
  
5.  建置方案。  
  
## 請參閱  
 [隔離應用程式](http://msdn.microsoft.com/library/aa375190)   
 [並存組件](_win32_side_by_side_assemblies)