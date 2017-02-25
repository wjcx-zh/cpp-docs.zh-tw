---
title: "/Wp64 (偵測 64 位元可移植性問題) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems"
  - "VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems"
  - "/wp64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Wp64 編譯器選項 [C++]"
  - "64 位元編譯器 [C++], 偵測可移植性問題"
  - "Wp64 編譯器選項 [C++]"
  - "-Wp64 編譯器選項 [C++]"
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# /Wp64 (偵測 64 位元可移植性問題)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個編譯器選項已過時。 在 Visual Studio 2013 之前的 Visual Studio 版本中，這會在同時使用 [\_\_w64](../../cpp/w64.md) 關鍵字標記的類型上，偵測到 64 位元可攜性問題。  
  
## 語法  
  
```  
/Wp64  
```  
  
## 備註  
 根據預設，在 Visual Studio 2013 之前的 Visual Studio 版本中，**\/Wp64** 編譯器選項在 Visual C\+\+ 32 位元編譯器和 Visual C\+\+ 64 位元編譯器中處於關閉狀態。  
  
> [!IMPORTANT]
>  [\/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) 編譯器選項和 [\_\_w64](../../cpp/w64.md) 關鍵字在 Visual Studio 2010 和 Visual Studio 2012 中已被取代，並且從 Visual Studio 2013 開始將不提供支援。 如果您轉換使用這個參數的專案，則在轉換期間將不會移轉參數。 若要在 Visual Studio 2010 或 Visual Studio 2012 中使用這個選項，您必須在專案屬性的 \[命令列\] 區段中，於 \[其他選項\] 下輸入編譯器參數。 如果您在命令列上使用 **\/Wp64** 編譯器選項，則編譯器會發出命令列警告 D9002。 請改用以 64 位元平台為目標的 Visual C\+\+ 編譯器，並指定 [\/W4](../../build/reference/compiler-option-warning-level.md) 選項，而非使用這個選項和關鍵字來偵測 64 位元可攜性問題。 如需詳細資訊，請參閱[為 64 位元設定程式](../../build/configuring-programs-for-64-bit-visual-cpp.md)。  
  
 您可以如同在 64 位元作業系統上使用下列類型的變數一樣，在 32 位元作業系統上對其進行測試：  
  
-   int  
  
-   long  
  
-   指標  
  
 如果您經常使用 64 位元編譯器編譯您的應用程式，可以在 32 位元編譯中只停用 **\/Wp64**，因為 64 位元編譯器會偵測到所有的問題。 如需如何將目標設定為 Windows 64 位元作業系統的詳細資訊，請參閱[為 64 位元設定程式](../../build/configuring-programs-for-64-bit-visual-cpp.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[屬性頁\] 對話方塊。  
  
     如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[C\/C\+\+\] 資料夾。  
  
3.  按一下 \[命令列\] 屬性頁。  
  
4.  修改 \[其他選項\] 方塊，以包含 **\/Wp64**。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [為 64 位元設定程式](../../build/configuring-programs-for-64-bit-visual-cpp.md)