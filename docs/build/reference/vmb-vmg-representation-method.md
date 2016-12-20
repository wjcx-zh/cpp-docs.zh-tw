---
title: "/vmb、/vmg (表示方法) | Microsoft Docs"
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
  - "/vmb"
  - "/vmg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmb 編譯器選項 [C++]"
  - "/vmg 編譯器選項 [C++]"
  - "表示方法編譯器選項 [C++]"
  - "vmb 編譯器選項 [C++]"
  - "-vmb 編譯器選項 [C++]"
  - "vmg 編譯器選項 [C++]"
  - "-vmg 編譯器選項 [C++]"
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /vmb、/vmg (表示方法)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選取編譯器用來表示類別成員指標的方法。  
  
 如果您總是在宣告類別成員指標之前定義類別，請使用 **\/vmb**。  
  
 如果需要在定義類別之前先宣告類別成員指標，請使用 **\/vmg**。  如果您要在兩個彼此參考的不同類別中定義成員，就會有這種需要。  如果是這種交互參考的類別，就必須必須先參考某個類別，然後才能加以定義。  
  
## 語法  
  
```  
/vmb  
/vmg  
```  
  
## 備註  
 您也可以在程式碼中使用 [pointers\_to\_members](../../preprocessor/pointers-to-members.md) 或 [繼承關鍵字](../../cpp/inheritance-keywords.md)，指定指標表示。  
  
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