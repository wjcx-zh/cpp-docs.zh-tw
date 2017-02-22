---
title: "/homeparams (將暫存器參數複製到堆疊) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/homeparams"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/homeparams 編譯器選項 [C++]"
  - "-homeparams 編譯器選項 [C++]"
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /homeparams (將暫存器參數複製到堆疊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在函式進入時，強制暫存器中所傳遞的參數寫入至堆疊上的位置。  
  
## 語法  
  
```  
/homeparams  
```  
  
## 備註  
 這個編譯器選項只適用於 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯器 \(原生和跨平台編譯\)。  
  
 在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯中傳遞參數時，呼叫慣例需要參數的堆疊空間，即使在暫存器中傳遞的參數也需要。  如需詳細資訊，請參閱[參數傳遞](../../build/parameter-passing.md)。  但是在發行的組建中，則預設為暫存器參數不會寫入至堆疊，而寫入已經為參數提供的空間中。  這種設定使得偵錯您程式的最佳化 \(發行\) 組建非常困難。  
  
 在發行組建中，請使用 **\/homeparams**，以確保您可以偵錯應用程式。  **\/homeparams** 確實隱含效能缺點，因為它的確需要循環，才能將暫存器參數載入至堆疊上。  
  
 在偵錯組建中，堆疊一定都是以在暫存器中傳遞的參數填入。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)