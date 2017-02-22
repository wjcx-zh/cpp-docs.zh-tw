---
title: "/WINMDFILE (指定 winmd 檔案) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadataFile"
dev_langs: 
  - "C++"
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WINMDFILE (指定 winmd 檔案)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 [\/WINMD](../../build/reference/winmd-generate-windows-metadata.md) 連結器選項所產生之 Windows 執行階段中繼資料 \(.winmd\) 輸出檔的檔案名稱。  
  
```  
  
/WINMDFILE:filename  
  
```  
  
## 備註  
 使用 `filename` 中指定的值來覆寫預設的 .winmd 檔案名稱\(`binaryname` .winmd\)。  請注意您不用附加「.winmd」至 `filename`。 如果多個值陳列在 **\/WINMDFILE** 命令列，最後一個會優先。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**Windows 中繼資料**\] 屬性頁。  
  
4.  在 \[**Windows 中繼資料檔案**\] 方塊中，輸入檔案的位置。  
  
## 請參閱  
 [\/WINMD \(產生 Windows 中繼資料\)](../../build/reference/winmd-generate-windows-metadata.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)