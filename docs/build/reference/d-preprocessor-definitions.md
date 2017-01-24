---
title: "/D (前置處理器定義) | Microsoft Docs"
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
  - "VC.Project.VCNMakeTool.PreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.PreprocessorDefinitions"
  - "/d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/D 編譯器選項 [C++]"
  - "常數, 定義"
  - "D 編譯器選項 [C++]"
  - "-D 編譯器選項 [C++]"
  - "巨集, 編譯"
  - "前置處理器定義符號"
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /D (前置處理器定義)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為原始程式檔定義前置處理符號。  
  
## 語法  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## 備註  
 您可以搭配 `#if` 或 `#ifdef` 使用此符號，條件式編譯原始程式碼。  在程式碼中重新定義符號定義或者以 `#undef` 指示詞取消定義之前，符號定義都會保持有效。  
  
 **\/D** 具有和原始程式碼檔案開頭的 `#define` 指示詞一樣的效用，唯一不同點在於 **\/D** 會移除命令列的引號，而 `#define` 則會保留。  
  
 與符號相關聯的值預設為 1。  例如 **\/D**`name` 等於 **\/D**`name`**\=1**。  本文結尾的範例中，會示範用來列印 `1` 的 **TEST** 定義。  
  
 使用 **\/D**`name`**\=** 進行編譯會造成符號不含關聯值。  雖然仍可使用該符號對程式碼進行條件式編譯，但除此以外，毫無意義。  在範例中，如果您使用 **\/DTEST\=** 進行編譯，便會發生錯誤。  這個行為與使用包含或不含某值的 `#define` 相似。  
  
 此命令會定義 TEST.c 中的符號 DEBUG：  
  
 **CL \/DDEBUG  TEST.C**  
  
 此命令會移除 TEST.c 中所有出現的關鍵字 `__far`：  
  
 **CL \/D\_\_far\=  TEST.C**  
  
 **CL** 環境變數無法設定為含有等號的字串。  若要使用 **\/D** 搭配 **CL** 環境變數，您必須指定數字符號來取代等號。  
  
```  
SET CL=/DTEST#0  
```  
  
 在命令提示字元定義前置處理符號時，請考慮編譯器剖析規則及殼層剖析規則。  例如，若要在您的程式中定義百分比前置處理符號 \(%\)，請在命令提示字元指定兩個百分比符號字元 \(%%\)：如果您只指定一個，則會發出剖析錯誤。  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在左方窗格中，選取 \[**組態屬性**\]、\[**C\/C\+\+**\]、\[**前置處理器**\]。  
  
3.  在右窗格中，開啟 \[**前置處理器定義**\] 屬性的右邊資料行中的下拉式功能表，然後選擇 \[**編輯**\]。  
  
4.  在 \[**前置處理器定義**\] 對話方塊中，加入 \(每行一個\)、修改或刪除一個或多個定義。  選取 \[**確定**\] 儲存您的變更。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。  
  
## 範例  
  
```  
// cpp_D_compiler_option.cpp  
// compile with: /DTEST  
#include <stdio.h>  
  
int main( )  
{  
    #ifdef TEST  
        printf_s("TEST defined %d\n", TEST);  
    #else  
        printf_s("TEST not defined\n");  
    #endif  
}  
```  
  
  **TEST defined 1**   
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/U、\/u \(取消定義符號\)](../../build/reference/u-u-undefine-symbols.md)   
 [\#undef 指示詞](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [\#define 指示詞](../../preprocessor/hash-define-directive-c-cpp.md)