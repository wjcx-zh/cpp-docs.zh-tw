---
title: "/MIDL (指定 MIDL 命令列引數的選項) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/midl"
  - "VC.Project.VCLinkerTool.MidlCommandFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MIDL 連結器選項"
  - "MIDL"
  - "MIDL 連結器選項"
  - "-MIDL 連結器選項"
  - "MIDL, 命令列選項"
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /MIDL (指定 MIDL 命令列引數的選項)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MIDL:@file  
```  
  
## 備註  
 其中：  
  
 `file`  
 是含有 [MIDL 命令列選項](http://msdn.microsoft.com/library/windows/desktop/aa366839)的檔案名稱。  
  
## 備註  
 將 IDL 檔轉換為 TLB 檔的所有選項都必須列在 `file` 中；MIDL 命令列選項不能在連結器的命令列上指定。  如果沒有指定 \/MIDL，則只會以 IDL 檔名而不使用其他選項來叫用 MIDL 編譯器。  
  
 該檔案中的每一個程式行都應該有一個 MIDL 命令列選項。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[內嵌 IDL\] 屬性頁。  
  
4.  修改 \[MIDL 命令檔\]屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [\/IDLOUT \(命名 MIDL 輸出檔\)](../../build/reference/idlout-name-midl-output-files.md)   
 [\/IGNOREIDL \(不要將屬性處理至 MIDL 中\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/TLBOUT \(命名 .TLB 檔\)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)