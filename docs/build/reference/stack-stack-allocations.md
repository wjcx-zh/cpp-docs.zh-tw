---
title: "/STACK (堆疊配置) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.StackReserveSize"
  - "VC.Project.VCLinkerTool.StackCommitSize"
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACK 連結器選項"
  - "-STACK 連結器選項"
  - "記憶體配置，堆疊"
  - "/STACK 連結器選項"
  - "堆疊，設定大小"
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /STACK (堆疊配置)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## 備註  
 \/STACK 選項會以位元組為單位設定堆疊的大小。  請只在建置 \(Build\) .exe 檔案時使用這個選項。  
  
 `reserve` 值會指定虛擬記憶體中的總堆疊配置。  若是 ARM，x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 電腦，預設堆疊大小是 1 MB。  
  
 `commit` 會隨作業系統的解讀而異。  在 Windows NT 中，它是指定一次要配置的實體記憶體數量。  認可的虛擬記憶體會在分頁檔中保留空間。  當應用程式需要較多的堆疊空間時，較高的 `commit` 值可以節省時間，但會增加記憶體需求且可能增加啟動時間。  若是 ARM，x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 電腦，預設認可值是 4 KB。  
  
 以十進位數或 C 語言標記法指定 `reserve` 和 `commit` 值。  
  
 另外一種設定堆疊大小的方式是在模組定義檔 \(.def\) 中使用 [STACKSIZE](../../build/reference/stacksize.md) 陳述式。  如果兩者都指定了，**STACKSIZE** 將會覆寫堆疊配置 \(\/STACK\) 選項。  您可以在建置 .exe 檔之後使用 [EDITBIN](../../build/reference/editbin-reference.md) 工具變更堆疊大小。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  按一下 \[**系統**\] 屬性頁。  
  
4.  修改下列其中一項屬性：  
  
    -   **堆疊基本配置大小**  
  
    -   **堆疊預留大小**  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 屬性。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)