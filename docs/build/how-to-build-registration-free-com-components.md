---
title: "如何：建置免註冊的 COM 元件 | Microsoft Docs"
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
  - "COM 元件, 免註冊"
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：建置免註冊的 COM 元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

免註冊的 COM 元件是指 DLL 中已內建資訊清單的 COM 元件。  
  
### 若要在 COM 元件中內建資訊清單  
  
1.  開啟 COM 元件的專案屬性頁。  
  
2.  展開 \[**組態屬性**\] 節點，然後展開 \[**資訊清單工具**\] 節點。  
  
3.  選取 \[**輸入和輸出**\] 屬性頁，然後將 \[**內嵌資訊清單**\] 屬性設為等於 \[**是**\]。  
  
4.  按一下 \[**確定**\]。  
  
5.  建置方案。  
  
## 請參閱  
 [隔離應用程式](http://msdn.microsoft.com/library/aa375190)   
 [並存組件](_win32_side_by_side_assemblies)   
 [如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)