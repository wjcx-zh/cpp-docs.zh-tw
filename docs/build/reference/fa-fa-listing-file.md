---
title: "/FA、/Fa (清單檔) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.AssemblerListingLocation"
  - "VC.Project.VCCLCompilerTool.ConfigureASMListing"
  - "VC.Project.VCCLWCECompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.AssemblerListingLocation"
  - "/fa"
  - "VC.Project.VCCLCompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FA 編譯器選項 [C++]"
  - "僅列出組譯碼"
  - "FA 編譯器選項 [C++]"
  - "-FA 編譯器選項 [C++]"
  - "列出檔案類型"
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /FA、/Fa (清單檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立包含組譯程式碼的清單檔。  
  
## 語法  
  
```  
/FA[c|s|u]  
/Fapathname  
```  
  
## 備註  
 引數可以控制原始程式碼和機器碼 \(Machine Code\) 的產生和清單檔的副檔名。  
  
 下表將描述 **\/FA** 各個不同的值。  您可以指定一個以上的值給 **\/FA**。  例如，您可以指定 **\/FAsu**。  
  
|選項|清單內容和 副檔名|  
|--------|---------------|  
|**\/FA**|組譯程式碼；.asm|  
|**\/FAc**|機器碼和組譯程式碼；.cod|  
|**\/FAs**|原始程式碼和組譯程式碼；.asm<br /><br /> 如果指定了 **\/FAcs**，副檔名將會是 .cod|  
|**\/FAu**|會讓輸出檔以 UTF\-8 格式建立，加上位元組順序標記。  檔案的編碼方式是預設為 ANSI，但是如果您要在任何系統上正確顯示的清單檔，或是如果使用 Unicode 原始程式碼檔案做為編譯器的輸入，則使用 **\/FAu**。<br /><br /> 如果已指定 **\/FAsu**，而且如果原始程式碼檔案使用 Unicode 編碼方式而不用 UTF\-8，則 .asm 檔中的程式碼行可能無法正確顯示。|  
  
 根據預設，清單檔會使用與原始程式檔相同的主檔名 \(Base Name\)。  您可以使用 **\/Fa** 選項變更清單檔的名稱和建立時所在的目錄。  
  
|\/Fa 的使用|結果|  
|--------------|--------|  
|**\/Fa**|對編譯中的每一個原始程式碼檔案建立一個 *source\_file*.asm。|  
|**\/Fa** *filename*|*filename*.asm 會置於目前的目錄中。  只在編譯單一原始程式碼檔案時有效。|  
|**\/Fa** *filename.extension*|*filename.extension*會置於目前的目錄中。  只在編譯單一原始程式碼檔案時有效。|  
|**\/Fa** *directory*\\|對編譯中的每一個原始程式碼檔案建立一個 *source\_file*.asm，並將其置於指定的 *directory* 中。  請注意，必須要有後面的反斜線。  只允許目前磁碟機上的路徑。|  
|**\/Fa** *directory*\\*filename*|*filename*.asm 會置於指定的 `directory` 中。  只在編譯單一原始程式碼檔案時有效。|  
|**\/Fa** *directory*\\*filename.extension*|*filename.extension*置於指定的`directory`中。  只在編譯單一原始程式碼檔案時有效。|  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**輸出檔**\] 屬性頁。  
  
4.  修改 \[**ASM 清單位置**\] \(**\/Fa**\) 或 \[**組合語言輸出**\] \(**\/FA**\) 屬性 \(必須在 \[**其他選項**\] 方塊的 \[**命令列**\] 屬性頁中指定 **\/FAu**\)。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。  若要指定 **\/FAu**，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 範例  
 以下命令列會產生稱為 HELLO.cod 的原始程式碼和機器碼組合列表：  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)