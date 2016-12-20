---
title: "/GF (消除重複字串) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.StringPooling"
  - "VC.Project.VCCLWCECompilerTool.StringPooling"
  - "/gf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GF 編譯器選項 [C++]"
  - "重複字串"
  - "消除重複字串編譯器選項 [C++]"
  - "GF 編譯器選項 [C++]"
  - "-GF 編譯器選項 [C++]"
  - "字串共用編譯器選項 [C++]"
  - "字串 [C++], 共用"
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GF (消除重複字串)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使編譯器能夠在執行過程中在程式影像和記憶體中建立完全相同的字串副本。  這是稱為「*字串共用*」\(String Pooling\) 的最佳化，可以建立較小的程式。  
  
## 語法  
  
```  
/GF  
```  
  
## 備註  
 如果使用 **\/GF**，作業系統不會交換記憶體的字串部分，並且可以從影像檔將字串讀回來。  
  
 **\/GF** 共用字串為唯讀。  如果嘗試在 **\/GF** 之下修改字串，就會發生應用程式錯誤。  
  
 字串共用可以讓原來要指向多個緩衝區的多重指標成為指向單一緩衝區的多重指標。  在下列程式碼中，`s` 和 `t` 是以相同的字串初始化的。  字串共用使它們指向相同的記憶體：  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  用於 \[編輯後繼續\] 的 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 選項會自動設定 **\/GF** 選項。  
  
> [!NOTE]
>  **\/GF**編譯器選項會為每個唯一的字串建立一個可定址的區段。  根據預設，物件檔案最多可以包含 65,536 個可定址的區段。  如果您的程式包含超過 65536 個字串，請使用[\/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)編譯器選項建立更多區段。  
  
 使用 [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 **\/O2** 時，**\/GF** 會啟用。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**程式碼產生**\] 屬性頁。  
  
4.  修改 \[**啟用字串共用**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)