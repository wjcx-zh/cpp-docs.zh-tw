---
title: "/ALLOWBIND (阻止 DLL 繫結) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.PreventDLLBinding"
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWBIND 連結器選項"
  - "ALLOWBIND 連結器選項"
  - "-ALLOWBIND 連結器選項"
  - "繫結 DLL"
  - "DLL [C++], 防止繫結"
  - "防止 DLL 繫結"
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWBIND (阻止 DLL 繫結)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALLOWBIND[:NO]  
```  
  
## 備註  
 \/ALLOWBIND:NO 在 DLL 的標頭中設定一個位元，向 Bind.exe 表示不允許繫結影像。  如果 DLL 已數位簽署，您便可能不想要繫結 DLL \(繫結會使簽章無效\)。  
  
 您可以使用 EDITBIN 公用程式的 [\/ALLOWBIND](../../build/reference/allowbind.md) 選項，編輯現有 DLL 的 \/ALLOWBIND 功能。  
  
### 在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開 \[組態屬性\]、\[連結器\]，然後選取 \[命令列\]。  
  
3.  在 \[其他選項\] 中輸入 `/ALLOWBIND:NO`。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [BindImage 函式](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [BindImageEx 函式](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)