---
title: "/DYNAMICBASE | Microsoft Docs"
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
  - "/dynamicbase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE editbin 選項"
  - "DYNAMICBASE editbin 選項"
  - "-DYNAMICBASE editbin 選項"
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DYNAMICBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定可執行檔映像是否可以使用位址空間配置隨機載入 \(ASLR\) 功能，於載入時隨機重定基底。  
  
## 語法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## 備註  
 根據預設，連結器設定 **\/DYNAMICBASE** 選項。  
  
 這個選項修改可執行檔映像的標頭，來表明載入器是否可以在載入時間為映像隨機重定基底。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 上可支援 ASLR。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [Windows ISV 軟體安全性防禦措施](http://msdn.microsoft.com/library/bb430720.aspx)