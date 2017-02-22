---
title: "/IGNOREIDL (不要將屬性處理至 MIDL 中) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.IgnoreEmbeddedIDL"
  - "/ignoreidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IGNOREIDL 連結器選項"
  - "IGNOREIDL 連結器選項"
  - "-IGNOREIDL 連結器選項"
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /IGNOREIDL (不要將屬性處理至 MIDL 中)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IGNOREIDL  
```  
  
## 備註  
 \/IGNOREIDL 選項是表示原始程式碼中的任何 [IDL 屬性](../../windows/idl-attributes.md)都不應被處理至 .idl 檔中。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[內嵌 IDL\] 屬性頁。  
  
4.  修改 \[忽略內嵌 IDL\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [\/IDLOUT \(命名 MIDL 輸出檔\)](../../build/reference/idlout-name-midl-output-files.md)   
 [\/TLBOUT \(命名 .TLB 檔\)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [\/MIDL \(指定 MIDL 命令列引數的選項\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)