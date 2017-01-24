---
title: "/WINMDDELAYSIGN (部分簽署 winmd) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.WINMDDelaySign"
dev_langs: 
  - "C++"
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMDDELAYSIGN (部分簽署 winmd)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將公開金鑰置於檔案以啟用 Windows 執行階段中繼資料 \(.winmd\) 檔案的部分簽署。  
  
```  
  
/WINMDDELAYSIGN[:NO]  
  
```  
  
## 備註  
 類似套用到 .winmd 檔案的 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) 連結器選項。  如果您只想將公開金鑰放置在 .winmd 檔案中，請使用 **\/WINMDDELAYSIGN**。  根據預設，連結器如同 **\/WINMDDELAYSIGN:NO** 所指定的行動；也就是它不簽署 winmd 檔案。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**Windows 中繼資料**\] 屬性頁。  
  
4.  在 \[**Windows 中繼資料延遲簽署**\] 下拉式清單方塊中，選取您要的選項。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)