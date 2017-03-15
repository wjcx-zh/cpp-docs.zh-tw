---
title: "/INTEGRITYCHECK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/INTEGRITYCHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INTEGRITYCHECK editbin 選項"
  - "INTEGRITYCHECK editbin 選項"
  - "-INTEGRITYCHECK editbin 選項"
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /INTEGRITYCHECK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定必須在載入期間檢查二進位檔映像的數位簽章。  
  
```  
  
/INTEGRITYCHECK[:NO]  
  
```  
  
## 備註  
 在 DLL 或可執行檔的標頭中，這個選項會設定旗標，要求記憶體管理員必須檢查數位簽章，才能將影像載入 Windows 中。  Windows Vista 之前的 Windows 版本會忽略這個旗標。  對於實作核心模式程式碼的 64 位元 DLL，必須設定這個選項，並且建議所有的裝置驅動程式都這麼做。  如需詳細資訊，請參閱 MSDN 網站上的[核心模式程式碼簽署的逐步解說](http://go.microsoft.com/fwlink/?linkid=237093)。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)