---
title: "Building an Attributed Program | Microsoft Docs"
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
  - "tlb files"
  - "MIDL"
  - "MIDL, linker output"
  - "IDL files"
  - "tlb files, building attributed programs"
  - ".tlb files, building attributed programs"
  - "IDL files, building"
  - "attributes [C++], building type libraries and .idl files"
  - ".tlb files"
  - ".idl files, building"
  - "type libraries, linker options for building"
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Building an Attributed Program
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 屬性放在您的程式碼之後，您可能想 Visual C\+\+ 編譯器為您產生型別程式庫和.idl 檔案。  下列連結器選項您建置.tlb 和.idl 檔的說明：  
  
-   [\/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [\/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [\/MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [\/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 有些專案包含多個獨立的.idl 檔。  這些用來產生兩個或更多的.tlb 檔案，並選擇性地將它們繫結到資源區塊。  這種情況下目前不支援 Visual C\+\+。  
  
 此外，Visual C\+\+ 連結器會輸出到單一的 MIDL 檔的所有相關的 IDL 屬性資訊。  會沒有方法可以從單一專案中產生兩個型別程式庫。  
  
## 請參閱  
 [Concepts](../windows/attributed-programming-concepts.md)