---
title: "屬性對應 | Microsoft Docs"
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
  - "對應, 屬性"
  - "OLE DB 提供者, 屬性"
  - "屬性對應"
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 屬性對應
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除了工作階段、資料列集和選擇項命令物件外，每個提供者都支援一個或多個屬性。  這些屬性都定義於 OLE DB 提供者精靈所建立的標頭檔 \(Header File\) 之屬性對應中。  每個標頭檔都包含 OLE DB 屬性群組 \(為該物件或定義於該檔的物件\) 的屬性對應。  包含資料來源物件的標頭檔也包含 [DataSource 屬性](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx)的屬性對應。  Session.h 包含了[工作階段屬性](https://msdn.microsoft.com/en-us/library/ms714221.aspx)的屬性對應。  資料列集和命令物件位於名為 *projectname*RS.h 的單一標頭檔。  這些屬性都是[資料列集屬性](https://msdn.microsoft.com/en-us/library/ms711252.aspx)群組的成員。  
  
## 請參閱  
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)