---
title: "/WINMDKEYFILE (指定 winmd 金鑰檔) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.WINMDKeyFile"
dev_langs: 
  - "C++"
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMDKEYFILE (指定 winmd 金鑰檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定簽署 Windows 執行階段中繼資料\(.winmd\) 的金鑰或金鑰組。  
  
```  
  
/WINMDKEYFILE:filename  
  
```  
  
## 備註  
 類似套用到 .winmd 檔案的 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 連結器選項。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**Windows 中繼資料**\] 屬性頁。  
  
4.  在 \[**Windows 中繼資料重要檔案**\] 方塊中，輸入檔案的位置。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)