---
title: "/Qfast_transcendentals (Force Fast Transcendentals) | Microsoft Docs"
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
  - "/Qfast_transcendentals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qfast_transcendentals"
  - "Force Fast Transcendentals"
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qfast_transcendentals (Force Fast Transcendentals)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生超越函式的內嵌程式碼。  
  
## 語法  
  
```  
/Qfast_transcendentals  
```  
  
## 備註  
 這個編譯器選項會強制將超越函式轉換為內嵌程式碼以增進執行速度，  而且只有在與 **\/fp:except** 或 **\/fp:precise** 配對使用時才有作用。  產生超越函式的內嵌程式碼已經是 **\/fp:fast** 的預設行為。  
  
 這個選項與 **\/fp:strict** 不相容。  如需浮點編譯器選項的詳細資訊，請參閱 [\/fp \(指定浮點數行為\)](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)