---
title: "LIBRARY | Microsoft Docs"
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
  - "LIBRARY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIBRARY .def 檔案陳述式"
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LIBRARY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告訴 LINK 要建立 DLL。  同時，除非在建置中使用 .exp 檔，否則 LINK 還會建立一個匯入程式庫。  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## 備註  
 *library* 引數指定 DLL 的名稱。  您也可以使用 [\/OUT](../../build/reference/out-output-file-name.md) 連結器選項指定 DLL 的輸出名稱。  
  
 BASE\=*address* 引數設定作業系統用以載入 DLL 的基底位址 \(Base Address\)。  這個引數會覆寫預設 DLL 位址 0x10000000。  如需基底位址的詳細資訊，請參閱 [\/BASE](../../build/reference/base-base-address.md) 選項的說明。  
  
 建置 DLL 時，請記得使用 [\/DLL](../../build/reference/dll-build-a-dll.md) 連結器選項。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)