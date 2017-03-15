---
title: "/NOLOGO (隱藏程式啟始資訊) (連結器) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.SuppressStartupBanner"
  - "/nologo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOLOGO 連結器選項"
  - "橫幅, 隱藏啟始"
  - "著作權訊息"
  - "NOLOGO 連結器選項"
  - "-NOLOGO 連結器選項"
  - "suppress startup banner 連結器選項"
  - "版本編號, 防止連結器顯示"
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /NOLOGO (隱藏程式啟始資訊) (連結器)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOLOGO  
```  
  
## 備註  
 \/NOLOGO 選項不顯示著作權訊息或版本號碼。  
  
 這個選項也會隱藏命令檔的回應。  如需詳細資訊，請參閱 [LINK 命令檔](../../build/reference/link-command-files.md)。  
  
 依預設值，這項資訊是由連結器傳送到 \[輸出\] 視窗。  在命令列上，它會傳送至標準輸出，也可以重新導向至檔案中。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  這個選項只能從命令列使用。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  這個連結器選項無法以程式設計方式變更。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)