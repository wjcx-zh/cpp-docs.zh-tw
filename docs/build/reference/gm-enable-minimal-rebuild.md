---
title: "/Gm (啟用最少重建) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.MinimalRebuild"
  - "/Gm"
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.MinimalRebuild"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gm 編譯器選項 [C++]"
  - "啟用最少重建編譯器選項 [C++]"
  - "Gm 編譯器選項 [C++]"
  - "-Gm 編譯器選項 [C++]"
  - "最少重建"
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gm (啟用最少重建)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用最少重建，其可判定是否需要重新編譯包含已變更 C\+\+ 類別定義 \(儲存於標頭 \(.h\) 檔\) 的 C\+\+ 原始程式檔。  
  
## 語法  
  
```  
/Gm  
```  
  
## 備註  
 編譯器在第一次編譯期間，會在專案的 .idb 檔中，儲存原始程式檔與類別定義之間的相依性資訊   \(相依性資訊會告知哪個原始程式檔與哪個類別定義相依，以及該定義位於哪個 .h 檔\)。後續編譯會使用儲存在 .idb 檔中的資訊，來判定是否需要編譯原始程式檔，即使其包括已修改的 .h 檔。  
  
> [!NOTE]
>  最少重建依賴於包含檔之間未變更的類別定義。  對於專案來說，類別定義必須是全域的 \(給定類別應該只有一個定義\)，這是因為 .idb 檔中的相依性資訊是針對整個專案建立的。  如果專案中類別具有多個定義，請停用最少重建。  
  
 因為使用 [\/ZW \(Windows 執行階段編譯\)](../../build/reference/zw-windows-runtime-compilation.md) 選項，累加連結器不支援 .obj 檔中包含的 Windows 中繼資料，所以 **\/Gm** 選項與 **\/ZW** 不相容。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[程式碼產生\] 屬性頁。  
  
4.  修改 \[啟用最少重建\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)