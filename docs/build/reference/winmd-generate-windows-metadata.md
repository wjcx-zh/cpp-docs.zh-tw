---
title: "/WINMD (產生 Windows 中繼資料) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadata"
dev_langs: 
  - "C++"
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /WINMD (產生 Windows 中繼資料)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用產生 Windows 執行階段中繼資料\(.winmd\)檔。  
  
```  
  
/WINMD[:{NO|ONLY}]  
```  
  
## 備註  
 \/WINMD  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式的預設設定。  連結器皆產生二進位可執行檔以及 .winmd 中繼資料檔。  
  
 \/WINMD:NO  
 連結器只產生二進位可執行檔，而不是 .winmd 檔案。  
  
 \/WINMD:ONLY  
 連結器只產生 .winmd 檔案，而不是二進位可執行檔。  
  
 根據預設，輸出檔案名稱的格式 `binaryname`.winmd 指示詞。  若要指定不同的檔名，請使用 [\/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) 選項。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**Windows 中繼資料**\] 屬性頁。  
  
4.  在 \[**產生 Windows 中繼資料**\] 下拉式清單方塊中，選取您要的選項。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)