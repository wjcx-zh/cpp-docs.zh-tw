---
title: "/HEAP (設定堆積大小) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.HeapCommitSize"
  - "/heap"
  - "VC.Project.VCLinkerTool.HeapReserveSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/HEAP 連結器選項"
  - "堆積配置, 設定堆積大小"
  - "HEAP 連結器選項"
  - "-HEAP 連結器選項"
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HEAP (設定堆積大小)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/HEAP:reserve[,commit]  
```  
  
## 備註  
 \/HEAP 選項會以位元組為單位設定堆積 \(Heap\) 的大小。  此選項只使用於建置 .exe 檔時。  
  
 *reserve* 引數會指定虛擬記憶體中堆積配置 \(Heap Allocation\) 的總計。  預設的堆積大小為 1 MB。  連結器會將指定的值進位至最接近 4 的倍數個位元組。  
  
 選擇性 `commit` 引數是隨作業系統的解讀而異。  在 Windows NT\/Windows 2000 中，它是指定一次要配置的實體記憶體數量。  認可的虛擬記憶體會在分頁檔中保留空間。  當應用程式需要較多的堆積空間時，較高的 `commit` 值可以節省時間，但會增加記憶體需求且可能增加啟動時間。  
  
 以十進位數或 C 語言標記法指定 *reserve* 和 `commit` 值。  
  
 使用 [HEAPSIZE](../../build/reference/heapsize.md) 透過模組定義檔也可以使用這項功能。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[系統\] 屬性頁。  
  
4.  修改 \[堆積基本配置大小\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>以及<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)