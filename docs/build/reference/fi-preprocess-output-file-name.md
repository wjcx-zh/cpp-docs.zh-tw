---
title: "/Fi (前置處理輸出檔名稱) | Microsoft Docs"
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
  - "/Fi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fi 編譯器選項 (C++)"
  - "Fi 編譯器選項 (C++)"
  - "-Fi 編譯器選項 (C++)"
  - "前置處理輸出檔, 檔案名稱"
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fi (前置處理輸出檔名稱)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定輸出檔的名稱，[\/P \(前置處理至檔案\)](../../build/reference/p-preprocess-to-a-file.md) 編譯器選項會將前置處理的輸出寫入該檔案。  
  
## 語法  
  
```  
/Fipathname  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`pathname`|**\/P** 編譯器選項產生的輸出檔名稱和路徑。|  
  
## 備註  
 使用 **\/Fi** 編譯器選項搭配 **\/P** 編譯器選項。  
  
 如果您只指定 `pathname` 參數的路徑，會使用原始程式檔的主檔名做為前置處理過之輸出檔的主檔名。  `pathname` 參數並不需要特定的副檔名。  不過，如果沒有指定檔案副檔名，則會使用副檔名 ".i"。  
  
## 範例  
 下列命令列會前置處理 PROGRAM.cpp、保留註解、加入 [\#line](../../preprocessor/hash-line-directive-c-cpp.md) 指示詞，並將結果寫入至 MYPROCESS.i 檔案。  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [\/P \(前置處理至檔案\)](../../build/reference/p-preprocess-to-a-file.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)