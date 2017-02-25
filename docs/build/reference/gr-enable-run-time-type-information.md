---
title: "/GR (啟用執行階段類型資訊) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gr"
  - "VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo"
  - "VC.Project.VCCLCompilerTool.RuntimeTypeInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gr 編譯器選項 [C++]"
  - "啟用執行階段類型資訊編譯器選項 [C++]"
  - "Gr 編譯器選項 [C++]"
  - "-Gr 編譯器選項 [C++]"
  - "RTTI 編譯器選項"
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /GR (啟用執行階段類型資訊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加入程式碼以便在執行階段檢查物件型別。  
  
## 語法  
  
```  
/GR[-]  
```  
  
## 備註  
 啟用 **\/GR** 時，編譯器會定義 `_CPPRTTI` 前置處理器巨集。  **\/GR** 依預設為開啟。  **\/GR\-** 會停用執行階段型別資訊。  
  
 如果編譯器無法靜態解析程式碼中的物件型別，請使用 **\/GR**。  當程式碼使用 [dynamic\_cast 運算子](../../cpp/dynamic-cast-operator.md) 或 [typeid](../../cpp/typeid-operator.md) 時，您通常需要 **\/GR** 選項。  不過，**\/GR** 會讓您映像的 .rdata 區段增加大小。  如果程式碼不使用 **dynamic\_cast** 或 **typeid**，**\/GR\-** 可能會產生較小的映像。  
  
 如需執行階段型別檢查的詳細資訊，請參閱《*C\+\+ 語言參考*》中的[執行階段類型資訊](../../cpp/run-time-type-information.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**語言**\] 屬性頁。  
  
4.  修改 \[**啟用執行階段型別資訊**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)