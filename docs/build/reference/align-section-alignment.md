---
title: "/ALIGN (區段對齊) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.Alignment"
  - "/align"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALIGN 連結器選項"
  - "ALIGN 連結器選項"
  - "-ALIGN 連結器選項"
  - "區段記憶體對齊"
  - "區段"
  - "區段, 指定記憶體對齊"
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /ALIGN (區段對齊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALIGN[:number]  
```  
  
## 備註  
 其中：  
  
 `number`  
 對齊值。  
  
## 備註  
 \/ALIGN 選項會在程式的線性位址空間中指定每個區段的對齊方式。  引數 `number` 以是位元組為單位而且必須是 2 的乘冪數。  預設值為 4K \(4096\)。  如果這個對齊產生無效影像，連結器將會發出警告。  
  
 除非您要撰寫裝置驅動程式這類的應用程式，否則應該不需要修改對齊。  
  
 使用 [\/SECTION](../../build/reference/section-specify-section-attributes.md) 選項的 align 參數可以修改特定區段的對齊。  
  
 您所指定的對齊值不可以小於最大的區段對齊。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)