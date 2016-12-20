---
title: "/RELEASE (設定總和檢查碼) | Microsoft Docs"
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
  - "/release"
  - "VC.Project.VCLinkerTool.SetChecksum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RELEASE 連結器選項"
  - "總和檢查碼設定"
  - "RELEASE 連結器選項"
  - "-RELEASE 連結器選項"
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RELEASE (設定總和檢查碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RELEASE  
```  
  
## 備註  
 \/RELEASE 選項會在 .exe 檔的標頭中設定總和檢查碼。  
  
 作業系統需要裝置驅動程式的總和檢查碼。  設定您裝置驅動程式發行版本 \(Release Version\) 的總和檢查碼可以確保與未來作業系統的相容性。  
  
 依預設值，如果指定了 [\/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) 選項，\/RELEASE 選項也會被設定。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[進階\] 屬性頁。  
  
4.  修改 \[設定總和檢查碼\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)