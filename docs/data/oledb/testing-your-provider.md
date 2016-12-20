---
title: "測試提供者 | Microsoft Docs"
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
  - "OLE DB 提供者, 測試"
  - "測試提供者"
  - "測試, OLE DB 提供者"
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 測試提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

發行提供者 \(Provider\) 之前，您必須依照順序，執行下列測試。  這些測試能確保大部分潛在的使用者能正確運作提供者函式。  
  
1.  使用 OLE DB 消費者樣板編寫的[消費者](../../data/oledb/creating-an-ole-db-consumer.md)應用程式來測試提供者。  測試消費者應涵蓋提供者的所有功能區域 \(所有已加入或已修改的程式碼\)。  
  
2.  使用 ADO 撰寫的消費者應用程式來測試提供者。  大多數的開發人員 \(特別是 Microsoft Visual Basic 和 Microsoft C\# 的開發人員\) 都使用 ADO 或 ADO.NET 做為消費者應用程式。  測試消費者應涵蓋提供者的所有功能區域。  如需 ADO 消費者應用程式的範例，請參閱 [Microsoft Visual Basic 內的 ADO 程式碼範例](https://msdn.microsoft.com/en-us/library/ms807514.aspx)。  
  
3.  執行 OLE DB 一致性測試 \(包含 ADO 一致性測試\)，以保證提供者可符合 OLE DB 提供者的層級 0 標準 \(如需層級的說明 0，搜尋「OLE DB 層級 0 一致性測試 \>。 [OLE DB 程式設計人員的方針](http://go.microsoft.com/fwlink/?LinkId=121548) 這些測試和相關的文件都包含在 Data Access SDK 的 Visual C\+\+ 內。  這些測試也有助於確保其他[服務提供者](../../data/oledb/ole-db-resource-pooling-and-services.md)彙總 \(Aggregate\) 可正確地執行提供者，這點在修改或加入屬性時特別有用。  如需一致性測試的詳細資訊，請參閱 Data Access SDK 的讀我檔案 \(在 Visual Studio CD 的其中一片 CD 中\)。  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)