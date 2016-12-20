---
title: "/WINMDKEYCONTAINER (指定金鑰容器) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.WINMDKEYCONTAINER"
dev_langs: 
  - "C++"
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMDKEYCONTAINER (指定金鑰容器)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定簽署 Windows 中繼資料\(.winmd\)檔的金鑰容器。  
  
```  
  
/WINMDKEYCONTAINER:name  
  
```  
  
## 備註  
 類似套用至 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 連結器選項 \(.winmd\) 檔案。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**Windows 中繼資料**\] 屬性頁。  
  
4.  在 \[**Windows 中繼資料重要容器**\] 方塊中，輸入檔案的位置。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)