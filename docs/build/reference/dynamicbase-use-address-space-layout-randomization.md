---
title: "/DYNAMICBASE (使用位址空間隨機載入) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RandomizedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE 連結器選項"
  - "DYNAMICBASE 連結器選項"
  - "-DYNAMICBASE 連結器選項"
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DYNAMICBASE (使用位址空間隨機載入)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定是否要產生可執行檔映像，可以使用 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 的位址空間配置隨機載入 \(ASLR\) 功能，於載入時隨機重定基底 \(Rebase\)。  
  
## 語法  
  
```  
/DYNAMICBASE[:NO]  
```  
  
## 備註  
 根據預設值，\/DYNAMICBASE 為 on。  
  
 這個選項會修改可執行檔的標頭，以指示應用程式是否應該在載入階段隨機重定基底 \(Rebase\)。  
  
 在 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 上有支援位址空間配置隨機化。  
  
### 在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**隨機化的基底位址**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)