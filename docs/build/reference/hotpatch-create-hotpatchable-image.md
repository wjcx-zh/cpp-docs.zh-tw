---
title: "/hotpatch (建立可線上修補的影像) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/hotpatch"
  - "VC.Project.VCCLCompilerTool.CreateHotpatchableImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "熱修補"
  - "-hotpatch 編譯器選項 [C++]"
  - "/hotpatch 編譯器選項 [C++]"
  - "熱修補"
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /hotpatch (建立可線上修補的影像)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

準備影像，以進行 Hotpatch 功能。  
  
## 語法  
  
```  
/hotpatch  
```  
  
## 備註  
 在編譯中使用 **\/hotpatch** 時，編譯器會確保各函式的第一個指令至少是兩個位元組，這是熱填補所需要的。  
  
 若要完成製作映像 hotpatchable 的準備，在您使用 **\/hotpatch** 編譯後，您必須使用 [\/FUNCTIONPADMIN \(建立可線上修補的影像\)](../../build/reference/functionpadmin-create-hotpatchable-image.md) 連結。  當您用 cl.exe 的單一引動編譯並連結影像時，**\/hotpatch** 中會隱含 **\/functionpadmin**。  
  
 由於在 ARM 結構上的指示大多都是兩個或是更大的位元組，還有因為 x64 編譯永遠會被視為當作 **\/hotpatch** 被指定了，當您為這些目標時編譯，您不需要指定 **\/hotpatch** ;不過，您仍然必須連接使用 **\/functionpadmin** 以建立其 hotpatchable 影像。  **\/hotpatch** 編譯器選項只會影響 x86 編輯。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 指引  
 如需更新管理的詳細資訊，請參閱 \< 更新管理的安全性方針 \>。 [http:\/\/www.microsoft.com\/technet\/security\/guidance\/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)