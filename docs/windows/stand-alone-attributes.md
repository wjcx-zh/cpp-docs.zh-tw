---
title: "Stand-Alone Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "standalone attributes"
  - "attributes [C++], standalone"
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Stand-Alone Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

獨立的屬性不能進行 C\+\+ 關鍵字，但更像一行程式碼。  獨立屬性陳述式需要的線條結尾的分號。  
  
|屬性|描述|  
|--------|--------|  
|[cpp\_quote](../windows/cpp-quote.md)|指定的字串，不能包含引號的字元，發出至產生的標頭檔。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[db\_command](../windows/db-command.md)|建立 OLE DB 命令一樣。|  
|[emitidl](../windows/emitidl.md)|決定是否所有後續的 IDL 屬性將加以處理並放置在產生的.idl 檔。|  
|[idl\_module](../windows/idl-module.md)|指定在 DLL 的進入點。|  
|[idl\_quote](../windows/idl-quote.md)|可讓您使用最新版的 Visual C\+\+ 中不支援的 IDL 建構，並將它們下載到產生的.idl 檔。|  
|[import](../windows/import.md)|指定包含您想要參考主要的.idl 檔中定義的另一個.idl、.odl 或.h 檔案。|  
|[importidl](../windows/importidl.md)|將指定的.idl 檔插入至產生的.idl 檔|  
|[importlib](../windows/importlib.md)|讓已編譯成另一個型別程式庫所建立的型別程式庫，您可以使用的型別。|  
|[包含](../windows/include-cpp.md)|指定要包含在產生的.idl 檔中的一或多個標頭檔。|  
|[includelib](../windows/includelib-cpp.md)|會造成.idl 或.h 檔被包含在產生的.idl 檔。|  
|[library\_block](../windows/library-block.md)|將.idl 檔案的媒體櫃區塊內的建構函式。|  
|[Module \- 模組](../windows/module-cpp.md)|定義文件庫區塊.idl 檔中。|  
|[no\_injected\_text](../windows/no-injected-text.md)|可以防止編譯器插入的屬性使用的程式碼。|  
|[pragma](../windows/pragma.md)|指定的字串，不能包含引號的字元，發出至產生的.idl 檔。|  
  
## 請參閱  
 [Attributes by Usage](../windows/attributes-by-usage.md)