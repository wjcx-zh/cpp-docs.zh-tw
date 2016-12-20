---
title: "/Gw (最佳化全域資料) | Microsoft Docs"
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
  - "/Gw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gw 編譯器選項 [C++]"
  - "-Gw 編譯器選項 [C++]"
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gw (最佳化全域資料)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝在 COMDAT 區段的全域資料以進行最佳化。  
  
## 語法  
  
```  
/Gw[-]  
```  
  
## 備註  
 **\/Gw** 選項可讓編譯器封裝在各自的 COMDAT 區段的全域資料。  根據預設， **\/Gw** 關閉且必須明確啟用。  若要明確停用它，請使用 **\/Gw\-**。  當啟用 **\/Gw** 和 [\/GL](../../build/reference/gl-whole-program-optimization.md) 時，連結器會使用全程式最佳化（whole\-program optimization）來比較多個物件檔案的 COMDAT 區段，以排除未參考的全域資料或合併相同唯讀全域資料。  這可以大幅減小產生的二進位可執行檔之大小。  
  
 當您分別進行編譯及連結時，您可以使用 [\/OPT: REF](../../build/reference/opt-optimizations.md) 連結器選項，便可以將未參考的全域資料從與 **\/Gw** 選項一起編譯的物件檔中之可執行檔排除。  
  
 您也可以一起使用 [\/OPT: ICF](../../build/reference/opt-optimizations.md) 和 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 連結器選項，在與 **\/Gw** 選項編譯之物件檔案中，跨檔案的組合任何與唯讀全域資料編譯相同的可執行檔。  
  
 如需詳細資訊，請參閱在 Visual C\+\+ 團隊部落格上的 [介紹 \/Gw 編譯器 Switch](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[**其他選項**\] 屬性以包含 **\/Gw**，然後選擇 \[**確定**\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)