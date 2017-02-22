---
title: "/ALLOWISOLATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ALLOWISOLATION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION editbin 選項"
  - "ALLOWISOLATION editbin 選項"
  - "-ALLOWISOLATION editbin 選項"
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /ALLOWISOLATION
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定資訊清單查閱的行為。  
  
## 語法  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## 備註  
 **\/ALLOWISOLATION** 會導致作業系統查閱和載入資訊清單。  
  
 **\/ALLOWISOLATION** 是預設值。  
  
 **\/ALLOWISOLATION:NO** 指出已載入可執行檔，好像沒有資訊清單一樣，並會使 [EDITBIN 參考](../../build/reference/editbin-reference.md) 在選擇性標頭的 `DllCharacteristics` 欄位中設定 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位元。  
  
 可執行檔停用隔離時，Windows 載入器並不會試圖尋找新建立處理序的應用程式資訊清單。  新處理序沒有預設的啟用內容，即使可執行檔本身有資訊清單，或有名為 *executable\-name*.exe.manifest 的資訊清單。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [\/ALLOWISOLATION \(資訊清單查閱\)](../../build/reference/allowisolation-manifest-lookup.md)   
 [資訊清單檔案參考](http://msdn.microsoft.com/library/aa375632.aspx)