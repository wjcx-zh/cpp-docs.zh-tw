---
title: "資料存取：ADO 和 RDO | Microsoft Docs"
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
  - "繫結控制項 [C++], ADO"
  - "繫結控制項 [C++], RDO"
  - "控制項 [C++], 資料繫結"
  - "資料存取 [C++], RDO 資料控制項"
  - "資料繫結 [C++], ADO"
  - "資料繫結 [C++], RDO"
  - "資料控制項 [C++]"
  - "資料繫結控制項 [C++], ADO"
  - "資料繫結控制項 [C++], RDO"
ms.assetid: 92da8f1e-144b-4605-ac0a-43c25bdc14a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料存取：ADO 和 RDO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表顯示支援資料來源或資料繫結控制項的兩種基礎技術。  
  
 **ADO**  
 ADO 為 OLE DB 的 COM 包裝函式，它有助於撰寫資料存取應用程式 \(消費者\)。  OLE DB 是一個 COM 架構的通用資料存取技術，可讓您使用任何資料來源，而非只有索引循序存取方法 \(Index Sequential Access Method，ISAM\) 和 SQL 架構的資料庫。  
  
 OLE DB 提供者 \(Provider\) 可存取各種資料來源的資料，並且可使用提供者所定義的查詢來擷取資料，而不限於使用 SQL 查詢。  
  
 **RDO**  
 RDO 為 ODBC 的 COM 包裝函式。  ODBC 為 C 架構的 API，可允許一般用途 \(異質性\) 的資料存取。  不過，RDO 需以 SQL 做為存取資料的指令語言。  
  
 您可以考慮使用 ADO 架構的資料存取控制項，而非 RDO 資料存取控制項。  
  
 下表顯示 ADO 和 RDO 資料控制項之間的主要差異。  
  
 **資料繫結控制項**  
 RDO 資料繫結控制項使用 **ICursor** 介面；ADO 控制項則使用 OLE DB `IRowset` 介面。  在這兩種狀況下，控制項所使用的介面都會傳回一個資料列集。  
  
 RDO 架構的資料繫結控制項是為搭配 Visual Basic 運作而設計的。  因此，RDO 資料繫結控制項的一些功能 \(特別是格式化方面的功能\) 並無法用於 Visual C\+\+ 應用程式內。  ADO 資料繫結控制項內並未出現這個問題。  
  
 **資料控制項**  
 ADO 資料控制項可實作 **IDataSource** 介面，而 RDO 資料控制項則實作 **IVBDSC** 介面。  您可以呼叫 **IDataSource** 方法來接收 `IRowset` 介面指標。  同樣地，您可以呼叫 IVBDSC 方法來取得 **ICursor** 介面指標。  
  
## 請參閱  
 [在 Visual C\+\+ 中使用 ActiveX 控制項進行資料繫結](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)