---
title: "/U、/u (取消定義符號) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions"
  - "/u"
  - "VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/U 編譯器選項 [C++]"
  - "U 編譯器選項 [C++]"
  - "-U 編譯器選項 [C++]"
  - "取消定義符號編譯器選項"
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /U、/u (取消定義符號)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/U** 編譯器選項會取消定義指定的前置處理器符號。  **\/u** 編譯器選項會取消定義編譯器所定義的 Microsoft 專有符號。  
  
## 語法  
  
```  
/U[ ]symbol  
/u  
```  
  
## Arguments  
 `symbol`  
 要取消定義的前置處理器符號。  
  
## 備註  
 **\/U** 和 **\/u** 選項都不能取消定義以 **\#define** 指示詞建立的符號。  
  
 **\/U** 選項可以取消定義先前以 **\/D** 選項定義的符號。  
  
 依預設，編譯器會定義下列 Microsoft 專有符號。  
  
|符號|功能|  
|--------|--------|  
|\_CHAR\_UNSIGNED|預設 char 型別為 unsigned。  指定 [\/J](../../build/reference/j-default-char-type-is-unsigned.md) 選項時的定義。|  
|\_CPPRTTI|針對以 [\/GR](../../build/reference/gr-enable-run-time-type-information.md) 選項編譯的程式碼而定義。|  
|\_CPPUNWIND|針對以 [\/EHsc](../../build/reference/eh-exception-handling-model.md) 選項編譯的程式碼而定義。|  
|\_DLL|指定 [\/MD](../../build/reference/md-mt-ld-use-run-time-library.md) 選項時的定義。|  
|\_M\_IX86|x86 的目標值預設定義至 600。|  
|\_MSC\_VER|如需詳細資訊，請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)。|  
|\_WIN32|針對 WIN32 應用程式定義。  永遠會定義。|  
|\_MT|指定 [\/MD 或 \/MT](../../build/reference/md-mt-ld-use-run-time-library.md) 選項時的定義。|  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[**取消前置處理器的定義**\] 或 \[**取消所有前置處理器的定義**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/J \(預設 char 類型為 unsigned\)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [\/GR \(啟用執行階段類型資訊\)](../../build/reference/gr-enable-run-time-type-information.md)   
 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)   
 [\/MD、\/MT、\/LD \(使用執行階段程式庫\)](../../build/reference/md-mt-ld-use-run-time-library.md)