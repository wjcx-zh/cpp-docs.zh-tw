---
title: "/Od (停用 (偵錯)) | Microsoft Docs"
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
  - "/od"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Od 編譯器選項 [C++]"
  - "停用 (偵錯) 編譯器選項 [C++]"
  - "停用最佳化"
  - "快速編譯"
  - "沒有最佳化"
  - "Od 編譯器選項 [C++]"
  - "-Od 編譯器選項 [C++]"
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Od (停用 (偵錯))
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關閉程式中所有最佳化並且加速進行編譯。  
  
## 語法  
  
```  
/Od  
```  
  
## 備註  
 這個選項是預設值。  由於 **\/Od** 會抑制程式碼移動，所以能簡化偵錯處理序。  如需偵錯用編譯器選項的詳細資訊，請參閱 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**最佳化**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md)