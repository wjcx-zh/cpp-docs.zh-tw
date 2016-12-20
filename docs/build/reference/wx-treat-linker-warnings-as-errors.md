---
title: "/WX (將連結器警告視為錯誤) | Microsoft Docs"
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
  - "/WX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/WX 連結器選項"
  - "WX 連結器選項"
  - "-WX 連結器選項"
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WX (將連結器警告視為錯誤)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/WX[:NO]  
```  
  
## 備註  
 如果連結器產生警告訊息，\/WX 會導致沒有產生輸出檔。  
  
 這類似於編譯器的 **\/WX** \(如需詳細資訊，請參閱 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)\)。  不過，指定編譯的 **\/WX** 並不代表 **\/WX** 也會在連結器階段產生作用；您必須明確地替每一項工具指定 **\/WX**。  
  
 **\/WX** 預設為不作用。  若要將連結器警告視為錯誤，請指定 **\/WX**。  **\/WX:NO** 等於沒有指定 **\/WX**。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)