---
title: "/IDLOUT (命名 MIDL 輸出檔) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/idlout"
  - "VC.Project.VCLinkerTool.MergedIDLBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".idl 檔, 路徑"
  - "/IDLOUT 連結器選項"
  - "IDL 檔案, 路徑"
  - "IDLOUT 連結器選項"
  - "-IDLOUT 連結器選項"
  - "MIDL"
  - "MIDL, 輸出檔名"
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /IDLOUT (命名 MIDL 輸出檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IDLOUT:[path\]filename  
```  
  
## 參數  
 *path*  
 是絕對或相對路徑規格。  指定路徑時，您只會影響 .idl 檔的位置；其他所有檔案都是置於專案目錄中。  
  
 *filename*  
 指定由 MIDL 編譯器建立的 .idl 檔案名稱。  不會自動假設副檔名；如果您需要 .idl 副檔名，請指定 *filename*.idl。  
  
## 備註  
 \/IDLOUT 選項會指定 .idl 檔的檔名和副檔名。  
  
 連結具有[模組](../../windows/module-cpp.md)屬性的專案時，Visual C\+\+ 連結器會呼叫 MIDL 編譯器。  
  
 \/IDLOUT 也會指定與 MIDL 編譯器關聯的其他輸出檔檔名：  
  
-   *filename*.tlb  
  
-   *filename*\_p.c  
  
-   *filename*\_i.c  
  
-   *filename*.h  
  
 *filename* 是您傳遞給 \/IDLOUT 的參數。  如果指定了 [\/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)，則 .tlb 檔將會從 \/TLBOUT *filename* 取得它的名稱。  
  
 如果您沒有指定 \/IDLOUT 也沒有指定 \/TLBOUT，那麼連結器將會建立 vc70.tlb、vc70.idl、vc70\_p.c、vc70\_i.c 和 vc70.h。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[內嵌 IDL\] 屬性頁。  
  
4.  修改 \[已合併的 IDL 主檔名\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [\/IGNOREIDL \(不要將屬性處理至 MIDL 中\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL \(指定 MIDL 命令列引數的選項\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)