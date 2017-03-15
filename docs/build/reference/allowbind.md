---
title: "/ALLOWBIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALLOWBIND editbin 選項"
  - "/ALLOWBIND editbin 選項"
  - "-ALLOWBIND editbin 選項"
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /ALLOWBIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 DLL 是否可以重新繫結 。  
  
```  
  
/ALLOWBIND[:NO]  
  
```  
  
## 備註  
 **\/ALLOWBIND**會設定 DLL 標頭中的一個位元，告訴 Bind.exe 該影像允許被繫結。  當載入器不需要重定及執行每個參考的 DLL 時，位址修復繫結可讓影像快速地載入。  如果某個 DLL 已經以數位方式簽名，您就不應該讓它被繫結——繫結會使簽章無效。  如果位址空間配置隨機載入 \(ASLR\) 為影像啟用以支援 ASLR Windows 版本的 **\/DYNAMICBASE** ，則繫結無效。  
  
 使用 **\/ALLOWBIND:NO** 以防止 Bind.exe 繫結 DLL。  
  
 如需詳細資訊，請參閱 [\/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) 連結器選項。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)