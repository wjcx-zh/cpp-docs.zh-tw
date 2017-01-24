---
title: "/Za、/Ze (停用語言擴充功能) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions"
  - "/za"
  - "/ze"
  - "VC.Project.VCCLCompilerTool.DisableLanguageExtensions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Za 編譯器選項 [C++]"
  - "/Ze 編譯器選項 [C++]"
  - "Disable Language Extensions 編譯器選項"
  - "啟用語言擴充功能"
  - "語言擴充功能"
  - "語言擴充功能, 在編譯器中停用"
  - "Za 編譯器選項 [C++]"
  - "-Za 編譯器選項 [C++]"
  - "Ze 編譯器選項 [C++]"
  - "-Ze 編譯器選項 [C++]"
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Za、/Ze (停用語言擴充功能)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對不符合 ANSI C 或 ANSI C\+\+ 標準的語言建構，**\/Za** 會發出錯誤。  **\/Ze** 編譯器選項是預設選項，可以啟用 Microsoft Extensions。  
  
## 語法  
  
```  
/Za  
/Ze  
```  
  
## 備註  
  
> [!NOTE]
>  **\/Ze** 選項已被取代。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 編譯器提供了一些 ANSI C 或 ANSI C\+\+ 標準所指定功能以外的功能。  這些功能統稱為 Microsoft 對 C 和 C\+\+ 的擴充功能。  這些擴充功能在指定了預設 **\/Ze** 選項時就可以使用，而指定 **\/Za** 選項時則不能使用。  如需詳細資訊，請參閱[Microsoft 對 C 和 C\+\+ 的擴充功能](../../build/reference/microsoft-extensions-to-c-and-cpp.md)。  
  
 如果您打算移植程式到其他環境，請停用語言擴充功能。  編譯器會將擴充關鍵字視為簡單識別項，停用其他 Microsoft Extensions，並且自動定義 C 程式的`__STDC__` 預先定義巨集。  
  
 搭配 **\/Za** 使用的其他編譯器選項可以影響編譯器確保符合 ANSI 標準的方式。  例如，**\/Za** 和 [\/fp \(指定浮點數行為\)](../../build/reference/fp-specify-floating-point-behavior.md) 可能會產生未預期的行為。  
  
 如需搭配 **\/Za** 取得標準行為的方式，請參閱 [\/Zc](../../build/reference/zc-conformance.md) 編譯器選項。  
  
 如需 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 一致性問題的詳細資訊，請參閱 [Visual C\+\+ 中的相容性和符合性問題](../../misc/compatibility-and-compliance-issues-in-visual-cpp.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**語言**\] 屬性頁。  
  
4.  修改 \[**停用語言擴充功能**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)