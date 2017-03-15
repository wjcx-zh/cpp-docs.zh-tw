---
title: "/C (前置處理時保留註解) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.KeepComments"
  - "/c"
  - "VC.Project.VCCLWCECompilerTool.KeepComments"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c 編譯器選項 [C++]"
  - "c 編譯器選項 [C++]"
  - "-c 編譯器選項 [C++]"
  - "註解, 在前置處理過程中不刪除"
  - "在前置處理過程中保留註解"
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /C (前置處理時保留註解)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在前置處理過程中保留註解。  
  
## 語法  
  
```  
/C  
```  
  
## 備註  
 這個編譯器選項需要有 **\/E**、**\/P** 或 **\/EP** 選項。  
  
 下列程式碼範例將會顯示原始程式碼註解。  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 這個範例會產生以下輸出。  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**前置處理器**\] 屬性頁。  
  
4.  修改 \[**保留註解**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/E \(前置處理至 stdout\)](../../build/reference/e-preprocess-to-stdout.md)   
 [\/P \(前置處理至檔案\)](../../build/reference/p-preprocess-to-a-file.md)   
 [\/EP \(前置處理至 stdout 不加 \#line 指示詞\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)