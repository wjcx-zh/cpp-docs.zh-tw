---
title: "/CLRIMAGETYPE (指定 CLR 映像類型) | Microsoft Docs"
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
  - "/CLRIMAGETYPE"
  - "VC.Project.VCLinkerTool.CLRImageType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRIMAGETYPE 連結器選項"
  - "-CLRIMAGETYPE 連結器選項"
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRIMAGETYPE (指定 CLR 映像類型)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## 備註  
 連結器接受原生物件，也接受使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md)、\/clr:pure或\/clr:safe所編譯的MSIL 物件。  傳遞相同組建中的混合物件時，所得到輸出檔案的可驗證性將預設為同等於輸入模組最低層級的可驗證性。  例如，如果將安全模組和純粹模組皆傳遞至連結器，輸出檔案將是純粹模組。  如果傳遞原生映像和混合模式映像 \(使用 **\/clr** 所編譯\)，所得到的映像就會是混合模式映像。  
  
 如果您有需要，您可使用\/CLRIMAGETYPE 來指定較低層級可驗證性。  
  
 在 .NET 4.5，\/CLRIMAGETYPE 支援 SAFE32BITPREFERRED選項。  這個集合中——影像的 PE 標頭——旗標表示MSIL 物件為安全的，且可以執行於任何平台，不過優先執行於 32 位元執行環境。  這個選項可讓應用程式執行於 ARM 平台，並指定應用程式要執行於64 位元作業系統的 WOW64 下而不是使用 64 位元執行環境。  
  
 當使用 **\/clr** 或 **\/clr:pure** 所編譯的 .exe 執行於64 位元作業系統時，應用程式將在 WOW64 之下執行，而該環境允許 32 位元應用程式在 64 位元作業系統上執行。  根據預設，使用 **\/clr:safe** 所編譯的 .exe 執行於作業系統 64 位元支援下。  但是您的安全應用程式可能會載入 32 位元元件。  在此情況下，載入 32 位元應用程式時，在作業系統之 64 位元支援下執行的安全映像將失敗。  在 64 位元作業系統上載入 32 位元元件時，若要確保安全映像能繼續執行，請使用 \/CLRIMAGETYPE:SAFE32BITPREFERRED 選項。  如果您的程式碼不需要在 ARM 平台執行，您可以指定 \/CLRIMAGETYPE:PURE 選項變更中繼資料 \(.corflags\)，標記其將執行於 WOW64 \(和替代您的登入符號\)：  
  
 **cl \/clr:safe t.cpp \/link \/clrimagetype:pure \/entry:?main@@$$HYMHXZ \/subsystem:console**  
  
 如需如何判斷檔案之 CLR 映像類型的詳細資訊，請參閱 [\/CLRHEADER](../../build/reference/clrheader.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**CLR 映像類型**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)