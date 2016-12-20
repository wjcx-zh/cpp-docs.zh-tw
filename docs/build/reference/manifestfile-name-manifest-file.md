---
title: "/MANIFESTFILE (為資訊清單檔案命名) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ManifestFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTFILE 連結器選項"
  - "MANIFESTFILE 連結器選項"
  - "-MANIFESTFILE 連結器選項"
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFESTFILE (為資訊清單檔案命名)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTFILE:filename  
```  
  
## 備註  
 \/MANIFESTFILE 可讓您變更資訊清單檔的預設名稱。資訊清單的預設名稱是副檔名為 .manifest 的檔案名稱。  
  
 如果不同時以 [\/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) 連結，\/MANIFESTFILE 將沒有效用。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**資訊清單檔案**\] 屬性頁。  
  
5.  修改 \[**資訊清單檔案**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)