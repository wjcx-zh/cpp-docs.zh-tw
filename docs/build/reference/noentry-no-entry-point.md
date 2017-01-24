---
title: "/NOENTRY (沒有進入點) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ResourceOnlyDLL"
  - "/noentry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOENTRY 連結器選項 [C++]"
  - "DLL [C++], 建立"
  - "進入點 [C++], 連結器指定"
  - "NOENTRY 連結器選項"
  - "-NOENTRY 連結器選項"
  - "僅含資源的 DLL [C++], 建立"
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOENTRY (沒有進入點)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOENTRY  
```  
  
## 備註  
 必須有 \/NOENTRY 選項才能建立不包含可執行程式碼的僅含資源的 DLL。  如需詳細資訊，請參閱[建立僅含資源的 DLL](../../build/creating-a-resource-only-dll.md)。  
  
 使用此選項可防止 LINK 將 `_main` 的參考連結到 DLL 中。  
  
### 在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[進階\] 屬性頁。  
  
4.  修改 \[沒有進入點\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。  
  
## 請參閱  
 [建立僅含資源的 DLL](../../build/creating-a-resource-only-dll.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)