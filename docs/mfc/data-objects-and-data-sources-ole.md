---
title: "資料物件和資料來源 (OLE) | Microsoft Docs"
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
  - "資料物件 [C++], 定義"
  - "資料來源 [C++], 定義"
  - "資料傳輸 [C++]"
  - "資料傳輸 [C++], 定義"
  - "OLE [C++], 資料物件"
  - "OLE [C++], 資料來源"
  - "OLE [C++], 資料傳輸"
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料物件和資料來源 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用剪貼簿或拖放作業時，就會執行資料傳輸，資料具有來源和目的端。  應用程式會複製資料，而另一個應用程式接受貼上文字的。  傳輸所需的每一邊對相同資料的不同作業為傳輸成功。  Microsoft Foundation Class \(MFC\) 程式庫提供代表這個傳輸的每一邊的兩個類別:  
  
-   資料來源 \(如實作由 `COleDataSource` 物件表示\) 傳送資料的來源。  它們的來源應用程式，會建立資料複製到剪貼簿時，或者，當資料為拖放作業期間提供。  
  
-   資料物件 \(實作由 `COleDataObject` 物件表示\) 資料傳輸的目的端。  它們建立，在接收端應用程式有資料進入時，或要求執行永遠從剪貼簿中貼上作業。  
  
 下列文件在您的應用程式會示範如何使用資料物件和資料來源。  因為這兩個可能會要求複製並貼上資料，這份資訊同時適用容器和伺服器應用程式。  
  
-   [資料物件和資料來源：建立和解構](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [資料物件和資料來源：管理](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 本章節內容  
 [拖放](../mfc/drag-and-drop-ole.md)  
  
 [剪貼簿](../mfc/clipboard.md)  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)