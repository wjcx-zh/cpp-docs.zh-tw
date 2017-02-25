---
title: "String and Text Classes | Microsoft Docs"
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
  - "string classes [ATL]"
  - "字串轉換, ATL"
ms.assetid: aa0cdc41-c953-4b17-82b6-59b908545571
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# String and Text Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別提供字串和文字字串轉換的支援。  
  
-   這個類別字串轉換巨集 `CA2TEX` 和 `CT2AEX`和 typedef 使用[CA2 AEX](../atl/reference/ca2aex-class.md)**CA2A**。  
  
-   這個類別字串轉換巨集 `CA2CTEX` 和 `CT2CAEX`和 typedef 使用[CA2 CAEX](../atl/reference/ca2caex-class.md)**CA2CA**。  
  
-   這個類別字串轉換巨集使用[CA2 WEX](../atl/reference/ca2wex-class.md)`CA2TEX`、 `CA2CTEX`、 `CT2WEX`和 `CT2CWEX`和 typedef **CA2W**。  
  
-   這個類別字串轉換巨集使用[CW2 AEX](../atl/reference/cw2aex-class.md)`CT2AEX`、 `CW2TEX`、 `CW2CTEX`和 `CT2CAEX`和 typedef **CW2A**。  
  
-   這個類別字串轉換巨集 `CW2CTEX` 和 `CT2CWEX`和 typedef 使用[CW2 CWEX](../atl/reference/cw2cwex-class.md)**CW2CW**。  
  
-   這個類別字串轉換巨集 `CW2TEX` 和 `CT2WEX`和 typedef 使用[CW2 WEX](../atl/reference/cw2wex-class.md)`CW2W`。  
  
-   [CComBSTR](../atl/reference/ccombstr-class.md) 這個類別是 `BSTR`. 的包裝函式。  
  
-   這個引數[\_U\_STRINGorID](../atl/reference/u-stringorid-class.md) 配接器類別允許資源名稱 \(`LPCTSTR`\) 或資源 ID \(**UINT**\) 使用 **MAKEINTRESOURCE** 巨集，會傳遞至函式，而不要求呼叫端轉換 ID 加入至字串。  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)