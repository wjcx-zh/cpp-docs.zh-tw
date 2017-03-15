---
title: "/FUNCTIONPADMIN (建立可線上修補的影像) | Microsoft Docs"
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
  - "/functionpadmin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FUNCTIONPADMIN 連結器選項"
  - "-FUNCTIONPADMIN 連結器選項"
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FUNCTIONPADMIN (建立可線上修補的影像)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

準備映像進行 Hotpatch。  
  
## 語法  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## 備註  
 其中：  
  
 `space` \(選擇性\)  
 填補量要加入各函式開始，5、 6 或 16。x86 影像需要五個位元組填補， x64 影像需要 6 位元組和影像建立為 Itanium 處理器系列 \(IPF\) 在每個函式開頭需要 16 位元組的填補。  
  
 編譯器預設為將根據影像的電腦類型，加入正確的空間量至影像。  
  
 為了讓連結器產生可線上修補的影像，.obj 檔案必須已經用 [\/hotpatch \(建立可線上修補的影像\)](../../build/reference/hotpatch-create-hotpatchable-image.md) 進行編譯。  
  
 當您用 cl.exe 的單一引動編譯並連結影像時，**\/hotpatch** 中會隱含 **\/functionpadmin**。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)