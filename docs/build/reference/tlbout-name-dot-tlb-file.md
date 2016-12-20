---
title: "/TLBOUT (命名 .TLB 檔) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.TypeLibraryFile"
  - "/tlbout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb 檔案, 重新命名"
  - "/TLBOUT 連結器選項"
  - "tlb 檔案, 重新命名"
  - "TLBOUT 連結器選項"
  - "-TLBOUT 連結器選項"
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /TLBOUT (命名 .TLB 檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBOUT:[path\]filename  
```  
  
## 備註  
 其中：  
  
 *path*  
 是應該建立 .tlb 檔的位置之絕對或相對路徑規格。  
  
 *filename*  
 是指定由 MIDL 編譯器建立的 .tlb 檔的名稱。  不會自動假設副檔名；如果您需要 .tlb 副檔名，請指定 *filename*.tlb。  
  
## 備註  
 \/TLBOUT 選項會指定 .tlb 檔的檔名和副檔名。  
  
 連結具有[模組](../../windows/module-cpp.md)屬性的專案時，Visual C\+\+ 連結器會呼叫 MIDL 編譯器。  
  
 如果沒有指定 TLBOUT，則 .tlb 檔將會從 [\/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename* 取得它的名稱。  如果 \/IDLOUT 也沒有指定，那麼這個 .tlb 檔就會被稱為 vc70.tlb。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[內嵌 IDL\] 屬性頁。  
  
4.  修改 \[型別程式庫\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [\/IGNOREIDL \(不要將屬性處理至 MIDL 中\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL \(指定 MIDL 命令列引數的選項\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)