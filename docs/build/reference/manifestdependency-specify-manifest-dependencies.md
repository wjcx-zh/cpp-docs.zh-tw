---
title: "/MANIFESTDEPENDENCY (指定資訊清單相依性) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.AdditionalManifestDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTDEPENDENCY 連結器選項"
  - "MANIFESTDEPENDENCY 連結器選項"
  - "-MANIFESTDEPENDENCY 連結器選項"
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFESTDEPENDENCY (指定資訊清單相依性)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## 備註  
 \/MANIFESTDEPENDENCY 可以讓您指定將放入資訊清單檔之 \<dependency\> 區段中的屬性。  
  
 如需有關如何建立資訊清單檔的詳細資訊，請參閱 [\/MANIFEST \(建立並存組件資訊清單\)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)。  
  
 如需資訊清單檔之 \<dependency\> 區段的詳細資訊，請參閱[發行者組態檔](http://msdn.microsoft.com/library/aa375682)。  
  
 \/MANIFESTDEPENDENCY 資訊可以透過下列兩個方法之一傳遞至連結器：  
  
-   直接在命令列上 \(或回應檔中\) 使用 \/MANIFESTDEPENDENCY。  
  
-   經由[註解](../../preprocessor/comment-c-cpp.md) Pragma。  
  
 下列範例示範了經由 Pragma 傳遞 \/MANIFESTDEPENDENCY 註解，  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 結果會在資訊清單檔中產生下列項目：  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 可能會在命令列傳遞相同的 \/MANIFESTDEPENDENCY 註解如下：  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 連結器將收集 \/MANIFESTDEPENDENCY 註解，刪除重複的項目，然後將所產生的 XML 字串加入至資訊清單檔。如果連結器發現有衝突的項目，資訊清單檔就會損毀，而應用程式也就無法啟動 \(可能會有一個項目加入至事件記錄檔，指出失敗的產生的由來\)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**資訊清單檔案**\] 屬性頁。  
  
5.  修改 \[**其他資訊清單相依性**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)