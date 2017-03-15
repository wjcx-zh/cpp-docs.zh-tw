---
title: "/SWAPRUN (將連結器輸出載入至交換檔) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.SwapRunFromNet"
  - "/swaprun"
  - "VC.Project.VCLinkerTool.SwapRunFromCD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN 連結器選項"
  - "檔案 [C++], LINK"
  - "LINK 工具 [C++], 輸出"
  - "連結器 [C++], 將輸出複製至交換檔"
  - "輸出檔, 連結器"
  - "連結器輸出的交換檔"
  - "SWAPRUN 連結器選項"
  - "-SWAPRUN 連結器選項"
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SWAPRUN (將連結器輸出載入至交換檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{NET|CD}  
```  
  
## 備註  
 \/SWAPRUN 選項會告訴作業系統先將連結器輸出複製到分頁檔，再從分頁檔執行映像。  這是 Windows NT 4.0 \(含\) 以後版本的功能。  
  
 如果指定 NET，作業系統會先將網路上的二進位映像複製到分頁檔，然後再從中加以載入。  這個選項有助於透過網路執行應用程式。  如果指定了 CD，作業系統會將抽取式磁碟上的影像複製到分頁檔，然後再將它載入。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[系統\] 屬性頁。  
  
4.  修改下列其中一項屬性：  
  
    -   **從光碟片交換執行**  
  
    -   **從網路交換執行**  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 屬性。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)