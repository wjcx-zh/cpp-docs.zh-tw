---
title: "/FC (診斷中的原始程式碼檔之完整路徑) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UseFullPaths"
  - "/FC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FC 編譯器選項 [C++]"
  - "-FC 編譯器選項 [C++]"
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /FC (診斷中的原始程式碼檔之完整路徑)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓編譯器顯示原始程式碼檔之完整路徑 \(傳遞給診斷中的編譯器\)。  
  
## 語法  
  
```  
/FC  
```  
  
## 備註  
 請考慮下列程式碼範例：  
  
```  
// compiler_option_FC.cpp  
int main( ) {  
   int i   // C2143  
}  
```  
  
 若沒有 **\/FC**，則診斷文字會類似下列診斷文字：  
  
-   compiler\_option\_FC.cpp\(5\) : 錯誤 C2143: 語法錯誤 : 遺漏 ';'  \(在 '}' 之前\)  
  
 若有 **\/FC**，則診斷文字會類似下列診斷文字：  
  
-   c:\\test\\compiler\_option\_FC.cpp\(5\) : 錯誤 C2143: 語法錯誤 : 遺漏 ';' \(在 '}' 之前\)  
  
 如果使用 \_\_FILE\_\_ macro 時，要查看檔名的完整路徑，則也需要 **\/FC**。如需 \_\_FILE\_\_ 的詳細資訊，請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)。  
  
 **\/FC** 選項是由 **\/ZI** 所隱含。  如需 **\/ZI** 的詳細資訊，請參閱 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 \[**C\/C\+\+**\] 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**使用完整路徑**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)