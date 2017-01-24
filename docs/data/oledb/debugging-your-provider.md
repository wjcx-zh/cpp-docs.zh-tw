---
title: "偵錯提供者 | Microsoft Docs"
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
  - "偵錯 [C++], 提供者"
  - "OLE DB 提供者, 偵錯"
  - "Visual C++ 偵錯工具"
  - "Visual C++ 偵錯工具, 偵錯提供者"
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 偵錯提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵錯提供者有下列兩種方式：  
  
-   由於提供者會在處理中建立，您可使用 OLE DB 消費者樣板來建立一些消費者程式碼，並正常地逐步執行提供者。  
  
-   您可使用隨附於 Visual C\+\+ 的 ITEST 公用程式。  
  
### 若要使用 ITEST 公用程式  
  
1.  開啟提供者專案。  
  
2.  請在 \[專案\] 功能表上按一下 \[**設定**\]。  
  
3.  在 \[**屬性頁**\] 對話方塊中，按一下 \[偵錯\] 索引標籤。  
  
4.  在 \[偵錯作業的執行檔\] 方塊內選取 ITEST 應用程式。  
  
5.  設定中斷點，然後按照平常方式進行偵錯。  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)