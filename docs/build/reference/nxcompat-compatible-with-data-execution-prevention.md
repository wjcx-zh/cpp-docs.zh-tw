---
title: "/NXCOMPAT (與資料執行防止相容) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/NXCOMPAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NXCOMPAT 連結器選項"
  - "NXCOMPAT 連結器選項"
  - "-NXCOMPAT 連結器選項"
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /NXCOMPAT (與資料執行防止相容)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示已測試可執行檔，以便能與 Windows 資料執行防止功能相容。  
  
## 語法  
  
```  
/NXCOMPAT[:NO]  
```  
  
## 備註  
 **\/NXCOMPAT** 依預設為開啟。  
  
 您可以使用 **\/NXCOMPAT:NO** 來明確指定某個可執行檔不相容於「資料執行防止」。  
  
 如需資料執行防止的詳細資訊，請參閱這些文章：  
  
-   Microsoft 說明及支援網站上的[資料執行防止 \(DEP\) 詳細描述](http://go.microsoft.com/fwlink/?LinkID=157771)  
  
-   MSDN 網站上的 [資料執行防止](http://go.microsoft.com/fwlink/?LinkID=157770)  
  
-   MSDN 網站上的 [資料執行防止 \(內嵌的視窗\)](http://go.microsoft.com/fwlink/?LinkID=157768)  
  
### 在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入這個選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)