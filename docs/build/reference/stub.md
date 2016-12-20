---
title: "STUB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STUB"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STUB .def 檔案陳述式"
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# STUB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在建置虛擬裝置驅動程式 \(Virtual Device Driver，VxD\) 的模組定義檔案中使用時，可讓您指定包含將在 VxD 中使用的 IMAGE\_DOS\_HEADER 結構 \(定義於 WINNT.H 中\) 之檔案名稱，而非預設的標題。  
  
```  
STUB:filename  
```  
  
## 備註  
 指定 *filename* 的另一種方式是使用 [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) 連結器選項。  
  
 只有在建置 VxD 時，模組定義檔中的 STUB 才為有效。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)